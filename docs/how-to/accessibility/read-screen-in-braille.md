(read-screen-in-braille)=
# Read screen in Braille

The Orca screen reader can display the user interface on a refreshable Braille display. It uses the BRLTTY service, which provides access to the Linux console for a blind person using a refreshable braille display. 

1. Make sure that Orca is installed:

    ```bash
    sudo apt install orca
    ```

2. Make sure that the BRLTTY service is installed:

    ```bash
    sudo apt install brltty brltty-espeak
    ```

3. Enable the BRLTTY service:

    ```bash
    sudo systemctl enable --now brltty
    ```

4. Add your user to the brlapi group to allow access to the braille device:

    ```bash
    sudo usermod --append -G brlapi user-name
    ```

5. Connect your braille device to the system.

## Read a document in a different language

If you're reading a document in a language different than your system language, set the language text table in BRLTTY.

## Troubleshooting

