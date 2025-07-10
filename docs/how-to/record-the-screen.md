(record-the-screen)=
# Record the screen

You can record a video of your screen. The video either captures your whole screen or a selected region. It's saved as a WebM video file.

1. Press {kbd}`PrintScr` and switch to {guilabel}`Record Screen`.

    Alternatively, press {kbd}`Ctrl+Alt+Shift+R`.

2. Select what to record:

    * {guilabel}`Selection` records a screen region.
    * {guilabel}`Screen` records your whole screen.

3. Click {guilabel}`Capture` or press {kbd}`Enter`.

    A red indicator in the top panel shows that you're recording and for how long.

4. To stop the recording, click the red indicator in the top panel.

5. Find the recording in the `Videos/Screencasts` folder in your home directory.

## Hardware acceleration

If the recording has a reduced frame rate and stutters, enable hardware acceleration for video encoding.

By default, your screen recording is limited by the CPU. If your CPU is slow, the recording skips frames. Instead, you can install VA-API (Video Acceleration API) drivers that encode the video with hardware acceleration, which captures your native screen rate:

```bash
sudo apt install gstreamer1.0-plugins-bad
```

With Ubuntu 25.10 or later, you can install VA-API drivers by selecting third-party drivers during the Ubuntu installation.

