# My Smart Home project with Home Assistant

You can find some of my Home Assistant configuration files [here](https://github.com/florib779/homeassistant-config) (which are not always up to date yet).

## Home Assistant Dashboard
![Home Assistant Dashboard](../images/home-assistant-dashboard.png)

## Integrated Roon Web Controller
![Integrated Roon Web Controller](../images/home-assistant-roon-web-controller.png)

## Goal

* Sonos
  - [x] Night mode (does not work when playing music via roon)
  - [x] Speech enhancement (does not work when playing music via roon)
  - [x] Speaker group management - [Mini Media Player](https://github.com/kalkih/mini-media-player) (Customizable media player card for Home Assistant Lovelace UI)
  - [ ] Bass/Treble/Loudness
  - [ ] Control subwoofer
    - [x] On/Off
    - [ ] Volume level
    - [ ] Crossover frequency (possible, but not testet yet)
    - [ ] Polarity (possible, but not testet yet)
* Roon
  - [x] Control/Show info
    - [x] [RoonLabs music player](https://www.home-assistant.io/integrations/roon/) (Home Assistant integration)
    - [x] [Roon Web Controller](https://github.com/pluggemi/roon-web-controller) (Roon-Extension)
    - [x] [Mini Media Player](https://github.com/kalkih/mini-media-player) (Customizable media player card for Home Assistant Lovelace UI)
* TV
  - [x] Turn TV on [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/)
  - [x] Turn TV off [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/)
  - [ ] Control TV
    - [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/) or [Android TV](https://www.home-assistant.io/integrations/androidtv/)
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
      - Actually not implemented in Home Assistant
      - [ ] Close shutter when TV is turned on.
      - [ ] Go to favorite position at a given time
  * Show info
    - [x] Comet DECT (radiator control)
    - [x] Deutsche Telekom/Eurotronic 40318684 (door/window contact)
    - [x] FRITZ!DECT 200 (smart plug)
    - [x] FRITZ!DECT 210 (smart plug)
    - [x] FRITZ!DECT 300 (radiator control)
    - [x] FRITZ!DECT 440 (switch with temperature sensor)
    - [x] Rademacher RolloTron DECT 1213 (shutter)
* Ecovacs Deebot [lovelace-xiaomi-vacuum-card](https://github.com/benct/lovelace-xiaomi-vacuum-card)
  - [x] Control
  - [x] Show info
- [x] Cooking Timer
- [ ] Alarm Clock
  * [Hass-Custom-Alarm](https://github.com/akasma74/hass-custom-alarm)
- [ ] Report the amount of unread emails - [IMAP](https://www.home-assistant.io/integrations/imap/)

## Installation

I am currently running Home Assistant Supervised on an Intel NUC with Manjaro. On the one hand to be able to use [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/) to control Roon with my remote control (which is still in the works). On the other hand because the RaspberryPi 3 is a bit sluggish.

1. `sudo usermod -aG docker user # Add our linux user to the Docker group`
2. `docker --version # Check if Docker is running`
3. `sudo curl -Lo installer.sh https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh`
4. `sudo bash installer.sh --machine qemux86-64`

After a while, the script will ask the following question:

`Do you want to proceed with overwriting the /etc/network/interfaces file? [N/y]`

In my case I simply pressed return (No), although it's recommended to press "Yes".

[Source](https://peyanski.com/how-to-install-home-assistant-supervised-official-way/#Home_Assistant_Supervised_method)

### Install HACS

`sudo docker exec -ti homeassistant /bin/bash`

`wget -q -O - https://install.hacs.xyz | bash -`

[Source](https://hacs.xyz/docs/installation/installation/)

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

### HDMI-CEC

`configuration.yaml`:

```
hdmi_cec:
  devices:
    TV: 0.0.0.0
    PulseEight: 3.0.0.0
```

#### Log in to your Docker container

`sudo docker exec -ti homeassistant /bin/bash`

#### Get CEC version

`cec-client -l`

#### Test your installation

`echo scan | cec-client -s -d 1`

#### Get available CEC commands

`echo h | cec-client -s -d 1`

#### Change volume on TV

`echo 'volup' | cec-client -s -d 1`

`echo 'voldown' | cec-client -s -d 1`

`echo 'mute' | cec-client -s -d 1`

#### Links
* https://www.cec-o-matic.com/

## Links
* [Awesome Home Assistant](https://www.awesome-ha.com)
* [HACS Repositories](https://hacs-repositories.web.app/)
* [Sonos Dashboard](https://community.home-assistant.io/t/sonos-dashboard/18843)
* [HA-Sonos](https://github.com/vmcosco/HA-Sonos)
