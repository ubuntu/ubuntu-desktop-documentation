(record-the-screen)=
# Record the screen

You can record a video of your screen. The video either captures your whole screen or a selected region. It's saved as a WebM or MP4 video file.

1. Press {kbd}`PrintScr` and switch to {guilabel}`Record Screen`.

    Alternatively, press {kbd}`Ctrl+Alt+Shift+R`.

2. Select what to record:

    * {guilabel}`Selection` records a screen region.
    * {guilabel}`Screen` records your whole screen.

3. Click {guilabel}`Capture` or press {kbd}`Enter`.

    A red indicator in the top panel shows that you're recording and for how long.

4. To stop the recording, click the red indicator in the top panel.

5. Find the recording in the `Videos/Screencasts` folder in your home directory.


## Hardware acceleration for improved recording

To improve performance and save battery life on laptops, you can enable hardware acceleration for video encoding.

By default, your screen recording relies on your CPU. This might cause skipped frames or higher resource usage, even if you don't immediately notice stuttering. Many computers have dedicated hardware for video encoding using VA-API (Video Acceleration API), which is more efficient.

* When installing Ubuntu 25.10 or later, you can select third-party drivers in the installer to enable hardware acceleration.

* On any Ubuntu release that's already installed and running, install packages that provide hardware acceleration:

    ```bash
    sudo apt install gstreamer1.0-plugins-bad
    ```

:::{note}
Certain GPU models and drivers don't support VA-API. With these, screen recording will still rely on the CPU even after installing the extra packages.
:::

