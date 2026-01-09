```{tags} Security
```

(enable-smart-cards-in-snapped-browsers)=
# Enable smart cards in snapped browsers

<!--
Authors: Marek Suchánek <marek.suchanek@canonical.com>, Nathan Teodosio <nathan.teodosio@canonical.com>
-->

Enable smart card authentication in Firefox or Chromium installed from snap.

## Overview

With this configuration, you can use your smart card to authenticate and sign content in Firefox or Chromium installed from snap. By default, smart cards do not work in snapped web browsers due to strict confinement in the snap.

If instead you want to use your smart card to **log in and authenticate the user**, see {ref}`log-in-using-a-smart-card`.

### What you’ll need

* A web browser installed from snap: [Firefox](https://snapcraft.io/firefox) or [Chromium](https://snapcraft.io/chromium).

* A smart card, ideally one that is [supported by OpenSC](https://github.com/OpenSC/OpenSC/wiki/Supported-hardware-%28smart-cards-and-USB-tokens%29).

## Select your smart card driver

1. Check if your smart card is supported by OpenSC. See [Supported hardware (smart cards and USB tokens)](https://github.com/OpenSC/OpenSC/wiki/Supported-hardware-%28smart-cards-and-USB-tokens%29).

    If you can see your smart card on the list, you can skip this whole section.

2. If your smart card isn't supported by OpenSC, you need a binary driver for your smart card. Your organization or government usually provides this driver.

    :::{warning}
    Using third-party smart card drivers in snap is experimental and unsupported. The driver might not work.
    :::

3. Install the smart card driver that you received from your organization or government. For example, **Bit4id** cards require the `libbit4xpki.so` driver, which is a proprietary `p11k` library. When you install the driver, it's available at the `/usr/lib/libbit4xpki.so` file path.

    In the following commands, **replace** `libbit4xpki.so` with the file name of your driver and `/usr/lib/libbit4xpki.so` with the full path to the driver.

4. Move the smart card driver, such as `libbit4xpki.so`, into the snap environment in your home directory.

    * For Firefox:

        ```{terminal}
        :copy:
        :user:
        :host:
        :dir:
        cp /usr/lib/libbit4xpki.so ~/snap/firefox/common/
        ```

    * For Chromium:

        ```{terminal}
        :copy:
        :user:
        :host:
        :dir:
        cp /usr/lib/libbit4xpki.so ~/snap/chromium/common/
        ```

## Configure Firefox

Enable smart card access in the Firefox snap. You can choose the graphical or terminal interface:

* In the GNOME graphical interface:

    1. Open Settings.
    2. Go to {menuselection}`Apps --> Firefox`.
    3. Enable `pcscd`.

* In the terminal, enter the following command:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo snap connect firefox:pcscd
    ```

Load the smart card module in Firefox:

1. Open Firefox and go to {menuselection}`Settings --> Privacy & Security --> Security --> Security devices`.

2. Click the **Load** button.

3. Enter the following line into the **Module filename** field:

    * If your card is supported by OpenSC:

        ```text
        /usr/lib/x86_64-linux-gnu/opensc-pkcs11.so
        ```

        If you're running Ubuntu on a different CPU architecture than Intel 64 and AMD64, replace `x86_64-linux-gnu` with your architecture code name.

    * If you provided a proprietary smart card driver:

        ```text
        /home/MY_USER_NAME/snap/firefox/common/libbit4xpki.so
        ```

        Replace `MY_USER_NAME` with your user name and `libbit4xpki.so` with the proprietary driver file name.

    :::{warning}
    Do not use the *Browse* button.
    :::

4. Click **OK** to confirm.

## Configure Chromium

Enable smart card access in the Chromium snap. You can choose the graphical or terminal interface:

* In the GNOME graphical interface:

    1. Open Settings.
    2. Go to {menuselection}`Apps --> Chromium Web Browser`.
    3. Enable `pcscd`.

* In the terminal, enter the following command:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo snap connect chromium:pcscd
    ```

Load the smart card module in Chromium:

1. Install the `modutil` tool:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    sudo apt install libnss3-tools
    ```

2. Add the smart card module to the NSS Database:

    * If your card is supported by OpenSC:

        ```{terminal}
        :copy:
        :user:
        :host:
        :dir:
        modutil -dbdir sql:.pki/nssdb/ -add "OpenSC" -libfile /usr/lib/x86_64-linux-gnu/opensc-pkcs11.so
        ```

        If you're running Ubuntu on a different CPU architecture than Intel 64 and AMD64, replace `x86_64-linux-gnu` with your architecture code name.

    * If you provided a proprietary smart card driver:

        ```{terminal}
        :copy:
        :user:
        :host:
        :dir:
        modutil -dbdir sql:.pki/nssdb/ -add "Bit4id" -libfile /home/MY_USER_NAME/snap/chromium/common/libbit4xpki.so
        ```

        Replace `MY_USER_NAME` with your user name, `Bit4id` with your smart card name or brand and `libbit4xpki.so` with the proprietary driver file name.

## Test if the authentication works

Open your web browser and try authenticating with your smart card.

Did it work? If not:

### Report any bugs

* If your card is supported by OpenSC and you encounter an issue with the workflow, please add your comment to [OpenSC smart cards do not work in the snapped browsers (LP#2089141)](https://launchpad.net/bugs/2089141).

* If you provided a proprietary smart card driver, it might not work for a variety of reasons. Please file a new issue at [Launchpad Bugs](https://launchpad.net/bugs).

    Your driver might depend on missing libraries. See the full list of dependencies and attach them to your bug report:

    ```{terminal}
    :copy:
    :user:
    :host:
    :dir:
    snap run --shell firefox -c ldd ~/snap/firefox/common/libbit4xpki.so
    ```

    Replace `libbit4xpki.so` with your driver's file name. Replace `firefox` with `chromium` if you use Chromium.

* If your card isn't supported by OpenSC, see the known issue tracked in [[snap] `apparmor` denied when trying to load `pkcs11` module for smart card authentication (LP#1967632)](https://launchpad.net/bugs/1967632).

### Additional resources

This tutorial connects the `pcscd` smart card plug to the web browser snap. For details about `pcscd`, see [The `pcscd` interface](https://snapcraft.io/docs/pcscd-interface).
