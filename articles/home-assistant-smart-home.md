# My Smart Home project with Home Assistant

You can find some of my Home Assistant configuration files [here](https://github.com/florib779/homeassistant-config).

## Home Assistant Dashboard
![Home Assistant Dashboard](../images/home-assistant-dashboard.png)

## Integrated Roon Web Controller
![Integrated Roon Web Controller](../images/home-assistant-roon-web-controller.png)

## Goal

* Sonos
  - [x] Night mode (does not work when playing music via roon)
  - [x] Speech enhancement (does not work when playing music via roon)
  - [x] Speaker group management - [Mini Media Player](https://github.com/kalkih/mini-media-player) (Customizable media player card for Home Assistant Lovelace UI)
  - [ ]  Bass/Treble/Loudness
  - [ ] Control subwoofer
    - [x] On/Off
    - [x] Volume level
    - [ ] Crossover frequency (possible, but not testet yet)
    - [ ] Polarity (possible, but not testet yet)
* Roon
  - [x] Control/Show info
    - [x] [RoonLabs music player](https://www.home-assistant.io/integrations/roon/) (Home Assistant integration)
    - [x] [Roon Web Controller](https://github.com/pluggemi/roon-web-controller) (Roon-Extension)
    - [x] [Mini Media Player](https://github.com/kalkih/mini-media-player) (Customizable media player card for Home Assistant Lovelace UI)
* TV
  - [x] Turn TV on - [Wake on LAN](https://www.home-assistant.io/integrations/wake_on_lan/)
  - [ ] Turn TV off
  - [ ] Control TV
    - [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/)
    - [Android TV](https://www.home-assistant.io/integrations/androidtv/)
  - [ ] [Notifications for Android TV / FireTV ](https://www.home-assistant.io/integrations/nfandroidtv/)
* AVM FRITZ!Box
  - [x] Sensor for internet connectivity (with external IP and uptime attributes)
  - [x] Turn on/off wifi and guest wifi
  * [FRITZ!Box Tools](https://github.com/mammuth/ha-fritzbox-tools)
* AVM FRITZ!DECT devices
  * Control
    - [x] Comet DECT (radiator control)
    - [x] FRITZ!DECT 200 (smart plug)
    - [x] FRITZ!DECT 210 (smart plug)
    - [x] FRITZ!DECT 300 (radiator control)
    - [ ] FRITZ!DECT 500 (LED light)
      - Actually not implemented in Home Assistant
    - [ ] Rademacher RolloTron DECT 1213 (shutter)
      - [ ] Close shutter when TV is turned on.
  * Show info
    - [x] Comet DECT (radiator control)
    - [x] Deutsche Telekom/Eurotronic 40318684 (door/window contact)
    - [x] FRITZ!DECT 200 (smart plug)
    - [x] FRITZ!DECT 210 (smart plug)
    - [x] FRITZ!DECT 300 (radiator control)
    - [x] FRITZ!DECT 440 (switch with temperature sensor)
    - [x] Rademacher RolloTron DECT 1213 (shutter)
* Ecovacs Deebot
  - [x] Control
  - [x] Show info
- [x] Cooking Timer
- [ ] Alarm Clock
  * [Hass-Custom-Alarm](https://github.com/akasma74/hass-custom-alarm)
- [ ] Report the amount of unread emails - [IMAP](https://www.home-assistant.io/integrations/imap/)

## Hardware

Raspberry Pi 3 Model B with [DietPi](https://github.com/MichaIng/DietPi) including [Roon Bridge](https://kb.roonlabs.com/RoonBridge), [Roon-Extension-Manager](https://github.com/TheAppgineer/roon-extension-manager), [Home Assistant](https://github.com/home-assistant) and display for Home Assistant.

## Installation

### Dietpi

[Diet-Pi-Installation-Extension-Manager](https://github.com/pluggemi/roon-web-controller/wiki/Diet-Pi-Installation-Extension-Manager)

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
2. Select Chromium and Roon Bridge
  1. Software Optimized -> Chromium
  2. Software Optimized -> Roon Bridge
3. Install the software, Dietpi-Config --> Install, then exit. The Raspberry Pi will reboot at this point.

![DietPi GPU Memory](../images/dietpi_gpu_memory.png)

![DietPi Software Final](../images/dietpi_software_final.png)

Roon Bridge is now installed and running.

#### Console boot up

1. As root, run the autostart configuration:
  1.`dietpi-autostart`
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
/usr/bin/chromium-browser --kiosk http://ip-of-the-homeassistant-server:8123
```

7. Save and exit
8. Make the kiosk.sh executable
  1. `chmod +x /root/kiosk.sh`
9. Reboot

### Home Assistant

I am currently trying to get Home Assistant running on an Intel NUC. On the one hand to be able to use [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/) to control Roon with my remote control. On the other hand because the RaspberryPi 3 is a bit sluggish.

#### HDMI-CEC

```
Logger: homeassistant.setup
Source: deps/lib/python3.9/site-packages/pycec/cec.py:20
First occurred: 10:28:29 (1 occurrences)
Last logged: 10:28:29
Error during setup of component hdmi_cec

Traceback (most recent call last):
  File "/usr/lib/python3.9/site-packages/homeassistant/setup.py", line 213, in _async_setup_component
    result = await task
  File "/usr/lib/python3.9/concurrent/futures/thread.py", line 52, in run
    result = self.fn(*self.args, **self.kwargs)
  File "/usr/lib/python3.9/site-packages/homeassistant/components/hdmi_cec/__init__.py", line 214, in setup
    adapter = CecAdapter(name=display_name[:12], activate_source=False)
  File "/root/.homeassistant/deps/lib/python3.9/site-packages/pycec/cec.py", line 20, in __init__
    import cec
ModuleNotFoundError: No module named 'cec'
```
To avoid this error message I appended `sys.path.append(’/user/.homeassistant/deps/lib/python3.9/site-packages/’)` in line 20, just before `import cec`.

---

Unfortunately, I had no luck installing Home Assistant via DietPi, so I decided on a Docker image.

<https://www.home-assistant.io/docs/installation/docker/>

`docker run --init -d --name="home-assistant" -v /mnt/dietpi_userdata/homeassistant/:/config -v /etc/localtime:/etc/localtime:ro --net=host --restart=always homeassistant/raspberrypi3-homeassistant:stable`

#### Updating the Docker image

`docker pull homeassistant/raspberrypi3-homeassistant:stable`  # if this returns "Image is up to date" then you can stop here

`docker stop home-assistant`  # stop the running container

`docker rm home-assistant`  # remove it from Docker's list of containers

`docker run --init -d --name="home-assistant" -v /mnt/dietpi_userdata/homeassistant/:/config -v /etc/localtime:/etc/localtime:ro --net=host --restart=always homeassistant/raspberrypi3-homeassistant:stable`  # finally, start a new one

#### Cleanup disc space

`docker system prune`  # this will remove all stopped containers, networks not used by at least one container, dangling images, build cache
~

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
* Automatic update of home assistant (docker image)

## Links

* [DietPi installation](https://dietpi.com/phpbb/viewtopic.php?p=9#p9)
* [Installation of roon-extension-manager on DietPi](https://github.com/pluggemi/roon-web-controller/wiki/Diet-Pi-Installation-Extension-Manager)
* [Measurements: A look & listen to Roon Bridge](http://archimago.blogspot.com/2017/02/measurements-look-listen-to-roon-bridge.html)
* [Awesome Home Assistant](https://www.awesome-ha.com)
* [HACS Repositories](https://hacs-repositories.web.app/)
