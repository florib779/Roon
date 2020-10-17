# Roon Web Display

Since Roon Build 354 it's possible to [display Now Playing information and lyrics](https://help.roonlabs.com/portal/en/kb/articles/displays) in your webbrowser and Chromecast devices.

modified_roon_web_display.png

## FireTV devices

It's possible to display it on FireTV devices with Firefox and Silk.

To prevent the screen from shutting off after a while, I use the app [Fully Kiosk Browser](https://www.fully-kiosk.com/) on my Android tablet and FireTV (there are different apks available).

## My Modified Version

![Modified Roon Web Display](../images/modified_roon_web_display.png)

[My modified version of /opt/RoonServer/Appliance/webroot/display_ui.html](https://github.com/florib779/Modified-Roon-Web-Display/blob/main/opt/RoonServer/Appliance/webroot/display_ui.html).

If you are using [ROCK](https://help.roonlabs.com/portal/en/kb/articles/roon-optimized-core-kit) it is not possible to modify this file.

I'm using the browser extension [Stylus](https://github.com/openstyles/stylus/) where I can put [this CSS code](https://github.com/florib779/Modified-Roon-Web-Display/blob/main/Stylus.css) into without fiddling around with Roon server files.
