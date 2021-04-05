# RaspberryPi with Roon Bridge and display

## Hardware

Raspberry Pi 3 Model B with [DietPi](https://github.com/MichaIng/DietPi) including [Roon Bridge](https://kb.roonlabs.com/RoonBridge), [Roon-Extension-Manager v1.0](https://community.roonlabs.com/t/roon-extension-manager-v1-0-beta-program/151438) and display for [my Home Assistant installation](home-assistant-smart-home.md).

## Installation

### Dietpi

After initial bootup, login through ssh.

![DietPi Initial](../images/dietpi_initial.png)

![DietPi Survey](../images/dietpi_survey.png)

![DietPi Serial Console](../images/dietpi_serial_console.png)

![DietPi Password](../images/dietpi_password.png)

![DietPi Unix Password](../images/dietpi_unix_password.png)

Dietpi will update itself.

In my configuration I had to turn the display 180 degrees:

Dietpi-Config --> Display Options --> Rotation (LCD)

Additionally I dim the display a little bit:

Dietpi-Config --> Display Options -->Display Brightness

#### Additional software

![DietPi Software](../images/dietpi_software.png)

![DietPi Software Install](../images/dietpi_software_install.png)


1. As root, run the software configuration
  1. `dietpi-software`
2. Select Software
  1. Software Optimized -> Chromium
  2. Software Optimized -> Roon Bridge
  3. Software Optimized -> Docker
3. Install the software, Dietpi-Config --> Install, then exit. The Raspberry Pi will reboot at this point.

![DietPi GPU Memory](../images/dietpi_gpu_memory.png)

![DietPi Software Final](../images/dietpi_software_final.png)

Roon Bridge is now installed and running.

#### Console boot up

1. As root, run the autostart configuration:
  1. `dietpi-autostart`
2. Select Custom - `/var/lib/dietpi/dietpi-autostart/custom.sh`
3. Save and exit

#### System configuration

1. Modify the custom.sh startup script
  1. `nano /var/lib/dietpi/dietpi-autostart/custom.sh`
2. Add this to the bottom of the file:
```
# Run the custom kiosk script
xinit /root/kiosk.sh -- -nocursor
```
3. Save and exit
4. Make the custom.sh script executable
  1. `chmod +x /var/lib/dietpi/dietpi-autostart/custom.sh`
5. Create the kiosk.sh script
  1. `nano /root/kiosk.sh`
6. Paste the following code as content:

```
#######################################
#
# Start up script for running the
# Chromium web browser full screen
#
#######################################

# Set the X display
export DISPLAY=":0"
# Tune the screen blanking time - time in seconds (standby, suspend, off)
# All numbers are time in seconds
# default value
# xset dpms 600 600 600 &
# 1 minute blank time
xset dpms 60 60 60 &

# start full screen web app
# change the URL if Roon Web Controller is running on a different system
#/usr/bin/chromium-browser --kiosk http://ip-of-the-homeassistant-server:8123
/usr/bin/chromium-browser --start-fullscreen http://ip-of-the-homeassistant-server:8123 #--kiosk
```

7. Save and exit
8. Make the kiosk.sh executable
  1. `chmod +x /root/kiosk.sh`
9. Reboot

### Roon Extension Manager

https://community.roonlabs.com/t/roon-extension-manager-v1-0-beta-program/151438

### node-sonos-http-api

#### Install

`wget https://github.com/jishi/node-sonos-http-api/archive/master.zip`

`unzip master.zip`

`cd node-sonos-http-api-master`

`npm install --production`

#### Autostart

`nano /etc/systemd/system/sonosapi.service`

```
[Unit]
Description=Sonos HTTP API Daemon
After=syslog.target network.target

[Service]
Type=simple
ExecStart=node /root/node-sonos-http-api-master/server.js
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

`systemctl enable sonosapi.service`

`systemctl start sonosapi.service`

#### Links

* [node-sonos-http-api](https://github.com/jishi/node-sonos-http-api)
* [Node-Sonos-HTTP-API Installation](https://www.mkshb.de/howto-node-sonos-http-api-installation/)
* [Sonos Dashboard](https://community.home-assistant.io/t/sonos-dashboard/18843)

## ToDo
* Automatic system upgrade via [cron-apt](https://wiki.ubuntuusers.de/cron-apt/)

## Links

* [DietPi installation](https://dietpi.com/phpbb/viewtopic.php?p=9#p9)
* [Installation of roon-extension-manager on DietPi](https://github.com/pluggemi/roon-web-controller/wiki/Diet-Pi-Installation-Extension-Manager)
* [Measurements: A look & listen to Roon Bridge](http://archimago.blogspot.com/2017/02/measurements-look-listen-to-roon-bridge.html)
