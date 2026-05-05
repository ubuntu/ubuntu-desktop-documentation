```{tags} Accessibility
```

(improve-screen-reader-usability)=
# Improve screen reader usability

Ubuntu Desktop might present some challenges when using the screen reader. If you experience difficulty, the following tips can help enhance the screen reader experience.

:::{note}
Many accessibility issues have been resolved with Ubuntu 26.04 LTS. If you're using Ubuntu 24.04 LTS, switch to the earlier version of this guide for additional tips.
:::

## Try different keyboard layouts

If you use a mix of various user interface languages and localized keyboard layouts, the screen reader might be using a different keyboard layout for its commands than your active layout. For example, you might be using the French layout but the screen reader commands treat your keyboard as if it had the American English layout.

If screen reader commands don't work, try pressing the key as if another relevant layout was active.

## Enable Orca before running applications

This issue affects Firefox and Chromium-based browsers in particular but can occur with other applications. If Orca is enabled and works in your desktop environment but does not work properly in the application, for example, it does not read web pages in your browser, try closing the application and restarting Orca *before* launching the application again.
