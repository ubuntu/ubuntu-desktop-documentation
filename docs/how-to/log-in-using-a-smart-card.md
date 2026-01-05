```{tags} Security
```

(log-in-using-a-smart-card)=
# Log in using a smart card

<!--
Author: Marco Trevisan <marco.trevisan@canonical.com>
-->

Learn how to configure smart card authentication in Ubuntu desktop using SSSD as security service daemon

## Overview


If you have a smart card, you can configure the Ubuntu desktop to accept your  smart card instead of a password for user authentication. You can then log in with your smart card.

You'll learn how to configure smart card authentication in the SSSD authentication daemon, the GDM login screen, the GNOME Settings Daemon and components that are common to headless setups.

If you want to use your smart card in a different way:

- To enable smart cards on a **server**, see {external:ref}`smart-card-authentication` in the Ubuntu Server documentation.
- To sign content in the **web browser** with your smart card, see {ref}`enable-smart-cards-in-snapped-browsers`.

### What you'll learn

- How to get smart card certificates and how they are used for authentication
- How to enable GDM smart card authentication for local users
- How to debug configuration issues

### What you'll need

- Ubuntu 20.04 or newer
- A smart card and a smart card reader (sometimes the reader is embedded in the card itself as for YubiKey)
- Smart card module supported by [`p11-kit`](https://p11-glue.github.io/p11-glue/p11-kit.html), in this guide we use cards supported by [OpenSC](https://github.com/OpenSC/OpenSC/wiki).
- The smart card certificate's certificate authority certificate in PEM format
- The `libpam-sss` package installed (it is already the case in versions newer than Ubuntu 20.04).

## Prerequisites

The smart card in use is expected to contain one or more X.509 certificates and the corresponding private keys to be used for authentication.

Smart card-based authentication is based on the principle that such certificate is associated to an user and unlocking the card gives the user access to the system.

This guide assumes having a smart card reader supported by [OpenSC](https://github.com/OpenSC/OpenSC/wiki), but setup for other libraries supported by [`p11-kit`](https://p11-glue.github.io/p11-glue/p11-kit.html) should not differ substantially.

1. The SSSD PAM module, needed for authentication, already installed after 20.04:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install libpam-sss
    ```

2. The smart card module: replace this with the PKCS#11 driver supporting your device:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install opensc-pkcs11
    ```

3. This is needed to expose the smart card reader, already installed after 20.04:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install pcscd
    ```

### Smart card PKCS#11 modules

While `opensc-pkcs11` supports a wide number of smart cards, some of them may require specific PKCS#11 modules that should be provided by the card manufacturer, and you must refer to your vendor to install the proper one.

All the modules supported by [`p11-kit`](https://p11-glue.github.io/p11-glue/p11-kit.html) can be used.

In case that custom PKCS#11 modules are used, you need to ensure that `p11-kit` is properly [configured](https://p11-glue.github.io/p11-glue/p11-kit/manual/config.html) so that it can find them.

In any case, `p11-kit` command will provide information regarding all the configured modules (with relative tokens if they're inserted and readable) that can be used for authentication:

```{terminal}
:copy:
:user:
:host:
:dir:
p11-kit list-modules

p11-kit-trust: p11-kit-trust.so
    library-description: PKCS#11 Kit Trust Module
    library-manufacturer: PKCS#11 Kit
    library-version: 0.23
    token: System Trust
        manufacturer: PKCS#11 Kit
        model: p11-kit-trust
        serial-number: 1
        hardware-version: 0.23
        flags:
               write-protected
               token-initialized
opensc-pkcs11: opensc-pkcs11.so
    library-description: OpenSC smartcard framework
    library-manufacturer: OpenSC Project
    library-version: 0.20
    token: MARCO TREVISAN (PIN CNS0)
        manufacturer: IC: STMicroelectronics; mask:...
        model: PKCS#15 emulated
        serial-number: 6090010669298009
        flags:
               login-required
               user-pin-initialized
               token-initialized
               user-pin-locked
```

### Extracting smart card X.509 Certificate

While the card certificate itself is not required, it's useful to save it in a `card-cert.pem` file to be used for debugging during this guide.

The procedures to extract a certificate are explained in the [Ubuntu Server smart card authentication guide](https://documentation.ubuntu.com/server/how-to/security/smart-card-authentication/index.html#x-509-smart-card-certificates) and we won't duplicate it here, but we'll just assume that the card certificate is saved in a file called `card-cert.pem` from now on.

Once the authentication is working this file can be safely removed.

### Certificate Authority verification

The card certificate must be allowed by a Certificate Authority, and the CA certificate file should be available in PEM format (we assume is called `CA-Auth-cert.pem` here).

You can check this:

1. List certificates:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
  	pkcs15-tool --list-certificates

  	Using reader with a card: Alcor Micro AU9560 00 00
  	X.509 Certificate [CNS1]
  		Object Flags   : [0x00]
  		Authority      : no
  		Path           : 3f00140090012002
  		ID             : 02
  		Encoded serial : 02 10 0357B1EC0EB725BA67BD2D838DDF93D5
    ```

  	```{terminal}
    :copy:
    :user:
    :host:
    :dir:
  	pkcs15-tool --read-certificate 2 > card-cert.pem
  	```

2. See the certificate contents:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    openssl x509 -text -noout -in card-cert.pem
    ```

3. Verify it is valid for the given CA:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    openssl verify -verbose -CAfile CA-Auth-cert.pem card-cert.pem
    ```

## Configure SSSD

### Disclaimer

SSSD is the default authentication daemon in Ubuntu it and supports various identity managers. Configuring them (such as FreeIPA, LDAP, Kerberos and others) is out the scope of this guide, but you can refer to [`man sssd.conf`](https://manpages.ubuntu.com/manpages/noble/en/man5/sssd.conf.5.html) and [SSSD official documentation](https://sssd.io/docs/introduction.html) for further reference on the topic.

For the purpose of this guide, we're going to show how SSSD should be configured for local user access, that is still something useful to enhance the security of a desktop computer, so that the user login is protected by a stronger authentication mechanism.

In the next steps we'll mention to change `sssd.conf` file by that we intend that the file in `/etc/sssd/sssd.conf` must be changed, note that these are just examples and this can be done using:

```{terminal}
:copy:
:user:
:host:
:dir:
sudoedit /etc/sssd/sssd.conf
```

:::{note}
The `sssd.conf` file **must** be owned by `root` and have permissions set to `600`.

If this is not the case, the file won't be loaded by SSSD.
:::

:::{warning}
SSSD **must** be restarted after each configuration change.

This can be done with `systemctl restart sssd`.

It's possible to check if configuration is correct, temporary launching the daemon with `sudo sssd -d9 -i`.
:::

### Include the CA certificates in the SSSD CA database

Since SSSD using OpenSSL under the hood, we need to add the certificate to the SSSD well known certificate path (if not changed via `sssd.certificate_verification` option) as PEM format, so copying the CA certificates (can be a chain of certificates) to `/etc/sssd/pki/sssd_auth_ca_db.pem` should be enough:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo mkdir -p /etc/sssd/pki -m 600
```

```{terminal}
:copy:
:user:
:host:
:dir:
sudo cat Ca-Auth-root-CERT.pem Ca-Auth-leaf-CERT.pem >> /etc/sssd/pki/sssd_auth_ca_db.pem
```

#### CA Certificate verification options

The smart card certificate verification against its Certificate Authority certificate can be tuned using various `sssd.conf` options.

For example:

```ini
[sssd]
# To validate a certificate against an incomplete CA chain
certificate_verification = partial_chain

[pam]
# To define a custom ca-certificates path
pam_cert_db_path = /etc/ssl/certs/ca-certificates.crt
```

#### Troubleshooting

Card certificate verification can be simulated using SSSD tools directly, by using the command SSSD's `p11_child`:

* In Ubuntu 20.04:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo /usr/libexec/sssd/p11_child --pre -d 10 --debug-fd=2 --nssdb=/etc/sssd/pki/sssd_auth_ca_db.pem
    ```

* In Ubuntu 22.04 and later versions:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo /usr/libexec/sssd/p11_child --pre -d 10 --debug-fd=2 --ca_db=/etc/sssd/pki/sssd_auth_ca_db.pem
    ```

If the certificate verification succeeds, the tool should output the card certificate name, its ID and the certificate itself in base64 format (other than debug data):

```{terminal}
:output-only:
(Mon Sep 11 16:33:32:129558 2023) [p11_child[1965]] [do_card] (0x4000): Found certificate has key id [02].
MARCO TREVISAN (PIN CNS1)
/usr/lib/x86_64-linux-gnu/pkcs11/opensc-pkcs11.so
02
CNS1
MIIHXDCCBUSgAwIBAgIQA1ex7....
```

For checking if the smart card works, without doing any verification check (and so for debugging purposes the option) `--verify=no_ocsp` can also be used, while `--verify=partial_chain` can be used to do incomplete CA verification.

### Enable PAM service

SSSD is a coordinator of various services, in order to support PAM we need to explicitly enable it in `sssd.conf`:

```ini
[sssd]
services = pam # This line can contain a list of other services

[pam]
pam_cert_auth = True
```

### Certificates Mapping

As explained, in order to make an user safely access to the system via a smart card, we need to associate one of the X.509 certificates that is present in the card to a system user.

The way of doing this changes slightly depending on the authentication provider in use, but as said, we're going to show the case for local users, that should not differ much from what can be done in more complex setups.

Mapping for more complex configurations can be done following the official [SSSD documentation](https://sssd.io/design-pages/matching_and_mapping_certificates.html) depending on [providers](https://sssd.io/design-pages/certmaps_for_LDAP_AD_file.html).

#### For local users

:::{warning}
This is just **an example**.

Configuration shown here must be adapted to match specific cases.
:::

When using only local users, SSSD can be configured to define an `implicit_domain` that maps all the local users.

Certificates can be associated to users using the card certificate subject, so in our example:

```{terminal}
:copy:
:user:
:host:
:dir:
openssl x509 -noout -subject -in card-cert.pem | sed "s/, /,/g;s/ = /=/g"

subject=C=IT,O=Some Organization,OU=REGIONE TOSCANA,SN=TREVISAN,GN=MARCO,CN=TRVMRC[...data-removed...]/6090033068507002.UyMnHxfF3gkAeBYHhxa6V1Edazs=
```

The `sssd.conf` configuration for the user `foo` would be:

```ini
[sssd]
enable_files_domain = True
services = pam

[certmap/implicit_files/foo]
matchrule = <SUBJECT>.*CN=TRVMRC[A-Z0-9]+/6090033068507002\.UyMnHxfF3gkAeBYHhxa6V1Edazs=.*

[pam]
pam_cert_auth = True
```

Note that the section where the `matchrule` regex is, should be in the form `[certmap/$PROVIDER/$USER_ID]`.

#### Troubleshooting

User mapping can be tested working in versions newer than Ubuntu 20.04 with:

```{terminal}
:copy:
:user:
:host:
:dir:
sudo dbus-send --system --print-reply \
    --dest=org.freedesktop.sssd.infopipe \
    /org/freedesktop/sssd/infopipe/Users \
    org.freedesktop.sssd.infopipe.Users.ListByCertificate \
    string:"$(cat card-cert.pem)" uint32:10
```

That should return the object path containing the expected user ID:

```{terminal}
:output-only:
method return time=1605127192.698667 sender=:1.1628 -> destination=:1.1629 serial=6 reply_serial=2
   array [
      object path "/org/freedesktop/sssd/infopipe/Users/implicit_5ffiles/1000"
   ]
```

#### Example of SSSD configuration

The SSSD configuration for accessing to the system is out of the scope of this document, however for smart card login it should contain at least such values:

```ini
[sssd]
# Comma separated list of domains
;domains = your-domain1, your-domain2

# comma-separated list of SSSD services
# pam might be implicitly loaded already, so the line is optional
services = pam

# You can enable debug of the SSSD daemon
# Logs will be in /var/log/sssd/sssd.log
;debug_level = 10

# A mapping between the Smart Card certificate and users
;[certmap/your-domain1/<username1>]
;matchrule = <SUBJECT>.*CN=<REGEX MATCHING CARD1 CN>.*

;[certmap/your-domain2/<username2>]
;matchrule = <SUBJECT>.*CN=<REGEX MATCHING CARD2 CN>.*

[pam]
pam_cert_auth = True

# The Certificate DB to be used:
# - Needs to be an openSSL CA certificates list
;pam_cert_db_path = /etc/ssl/certs/ca-certificates.crt

# You can enable debug infos for the PAM module
# Logs will be in /var/log/sssd/sssd_pam.log
# p11 child logs are in /var/log/sssd/p11_child.log
# standard auth logs are in /var/log/auth.log
;pam_verbosity = 10
;debug_level = 10
```

In general what's in the configuration file will affect the way SSSD will call the `p11_child` tool (that is the one in charge for the actual authentication).
Check [`man sssd.conf`](https://manpages.ubuntu.com/manpages/noble/en/man5/sssd.conf.5.html) for details.

Every time the configuration is changed SSSD should be restarted (`systemctl restart sssd`).

## Configure GDM

GDM is the default desktop manager in GNOME and Ubuntu, it does not require any particular configuration to work with smart cards authentication, but system administrators may still want to customize it.

When a supported smart-card is inserted in GDM or in GNOME Shell lock screen, the `/etc/pam.d/gdm-smartcard` PAM configuration will be loaded and that controls how authentication must be done.

:::{note}
Use `update-alternatives` to control the default mode interactively.

The `gdm-smartcard` PAM configuration implementation can be selected just running `sudo update-alternatives --config gdm-smartcard`.
:::

### Enable smart card only access

Using this PAM configuration smart card access will be the sole method to login.

This is the default configuration, but we document it for completeness:

```{terminal}
:copy:
:user:
:host:
:dir:
update-alternatives --set gdm-smartcard /etc/pam.d/gdm-smartcard-sssd-exclusive
```

### Enable smart card access with password fallback

Using this PAM configuration smart card access will tried first, if no smart card is available or the smart card verification fails, the password authentication will be used instead

```{terminal}
:copy:
:user:
:host:
:dir:
update-alternatives --set gdm-smartcard /etc/pam.d/gdm-smartcard-sssd-or-password
```

### Disable password access in GDM settings

This can be done to prevent the `gdm-password` PAM configuration to be loaded, it's not normally required as we already have profiles to avoid this, but it could be useful in some scenarios

```{terminal}
:copy:
:user:
:host:
:dir:
sudo -u gdm env DCONF_PROFILE=gdm gsettings set org.gnome.login-screen enable-password-authentication false
```

### Disable smart card access in GDM settings

Smart card authentication is always used when a token is inserted in the reader. There are cases in which this is not the wanted behavior, so it can be disabled at all.

```{terminal}
:copy:
:user:
:host:
:dir:
sudo -u gdm env DCONF_PROFILE=gdm gsettings set org.gnome.login-screen enable-smartcard-authentication false
```

### Lock GDM settings for users

These GSettings can be locked for users so that for example it's possible to use smart cards only to login but they are disabled for unlock, or to ensure that user can't disable smart card authentication for unlocking.

:::{note}
This is done through the GNOME `dconf` locking system. You can read more about this at [`man dconf.7`](https://manpages.ubuntu.com/manpages/noble/en/man7/dconf.7.html) or in the [GNOME documentation](https://help.gnome.org/admin/system-admin-guide/stable/dconf-lockdown.html.en).
:::

An example to configure it could be:

1. Create the `dconf` profile. This may not be required if a such file is already present:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/profile/user
    user-db:user
    system-db:local
    EOF
    ```

2. Create the `locks` directory:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo mkdir -p /etc/dconf/db/local.d/locks
    ```

3. Disable password authentication:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/db/local.d/00_gdm-password-disable
    [org/gnome/login-screen]
    enable-password-authentication=false
    EOF
    ```

4. Enable smart card authentication:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/db/local.d/00_gdm-smartcard-enable
    [org/gnome/login-screen]
    enable-smartcard-authentication=true
    EOF
    ```

5. Make these options non-user configurable:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/db/local.d/locks/00_gdm-smartcard-locks
    /org/gnome/login-screen/enable-password-authentication
    /org/gnome/login-screen/enable-smartcard-authentication
    EOF
    ```

6. Update system database:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo dconf update
    ```

### Troubleshooting

Given the amount of components in play, getting a working configuration may be tricky, so while lower levels of the stack can be tested independently it's also possible to simulate what GDM does using `pamtester`.

To get better debug logging, also enable it changing `/etc/sssd/sssd.conf` so that it has:

```ini
[pam]
pam_verbosity = 10
debug_level = 10
```

And `/etc/gdm3/custom.conf` with:
```ini
[debug]
Enable=true
```

You can use it to check your configuration without having to login/logout for real:

1. Install it:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install pamtester
    ```

2. Run the authentication service as standalone:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    pamtester -v gdm-smartcard $USER authenticate
    ```

3. Run the authentication service to get user from cert:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    pamtester -v gdm-smartcard "" authenticate
    ```

4. You can check what happened in the logs, reading:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo less /var/log/auth.log
    ```
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo less /var/log/sssd/sssd_pam.log
    ```
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo less /var/log/sssd/p11_child.log
    ```
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo journalctl | grep gdm
    ```
    
    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo journalctl --unit='*gdm*'
    ```
    

## Configure GNOME Settings Daemon

GNOME Settings daemon is in charge of monitoring the smart card state in GNOME, notifying when the token is added or removed. This allows to control some actions.

### Set action on card removal

When a smart card token that has been used for logging-in is removed from the system, GNOME can react automatically, by locking the screen or even logging out the user.

#### User setting

This can be configured at user level for each user by just changing this GSettings key:

```{terminal}
:copy:
:user:
:host:
:dir:
gsettings set org.gnome.settings-daemon.peripherals.smartcard removal-action 'lock-screen'
```

Valid values are `none`, `lock-screen` or `force-logout`.

#### Global settings

This value can be locked down at user level by system administrators

:::{note}
This is done through the GNOME `dconf` locking system. You can read more about this at [`man dconf.7`](https://manpages.ubuntu.com/manpages/noble/en/man7/dconf.7.html) or in the [GNOME documentation](https://help.gnome.org/admin/system-admin-guide/stable/dconf-lockdown.html.en).
:::

In particular an example could be:

1. Create the `dconf` profile. This may not be required if a such file is already present:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/profile/user
    user-db:user
    system-db:local
    EOF
    ```

2. Create the `locks` directory:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo mkdir -p /etc/dconf/db/local.d/locks
    ```

3. Lock the screen on smart card removal:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/db/local.d/00_gsd-smartcard-action
    [org/gnome/settings-daemon/peripherals/smartcard]
    removal-action='lock-screen'
    EOF
    ```

    Valid options are `lock-screen`, `force-logout` or `none`.

4. Make action non-user configurable:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    cat << EOF | sudo tee -a /etc/dconf/db/local.d/locks/00_gsd-smartcard-action
    /org/gnome/settings-daemon/peripherals/smartcard/removal-action
    EOF
    ```

5. Update system database:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo dconf update
    ```

These files can be safely removed to disable the lockdown (including the `profile/user` one, if no other override/lock is set).


## Testing the configuration

Now that all the pieces have been configured, just inserting a smart card should be enough to be required using it for GDM login and unlock.

If this is not the case, go through the various *Troubleshooting* sections of this guide to see what's not working, reading the logs output should be enough to figure out what needs to be fixed.
