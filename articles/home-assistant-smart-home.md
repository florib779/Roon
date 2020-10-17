# My Smart Home project with Home Assistant

## Home Assistant Dashboard
![Home Assistant Dashboard](../images/home-assistant-dashboard.png)

## Integrated Roon Web Controller
![Integrated Roon Web Controller](../images/home-assistant-roon-web-controller.png)

## Goal

* Sonos
  - [x] Night mode (does not work when playing music via roon)
  - [x] Speech enhancement (does not work when playing music via roon)
  - [x] Speaker group management - [Mini Media Player](https://github.com/kalkih/mini-media-player) (Customizable media player card for Home Assistant Lovelace UI)
  - [ ] Control of subwoofer volume level
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
* AVM FRITZ!DECT devices
  * Control
    - [x] Comet DECT (radiator control)
    - [x] FRITZ!DECT 200 (smart plug)
    - [x] FRITZ!DECT 210 (smart plug)
    - [x] FRITZ!DECT 300 (radiator control)
    - [ ] FRITZ!DECT 500 (LED light)
      - Actually not implemented in Home Assistant
  * Show info
    - [x] Comet DECT (radiator control)
    - [x] FRITZ!DECT 200 (smart plug)
    - [x] FRITZ!DECT 210 (smart plug)
    - [x] FRITZ!DECT 300 (radiator control)
    - [x] FRITZ!DECT 440 (switch with temperature sensor)
* Ecovacs Deebot
  - [x] Control
  - [x] Show info
- [x] Cooking Timer
- [ ] Report the amount of unread emails - [IMAP](https://www.home-assistant.io/integrations/imap/)


You can find some of my Home Assistant configuration files [here](https://github.com/florib779/homeassistant-config).
