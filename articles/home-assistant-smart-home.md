# My Smart Home project with Home Assistant

You can find some of my Home Assistant configuration files [here](https://github.com/florib779/homeassistant-config) (which are not always up to date yet).

## Home Assistant Dashboard

![Home Assistant Dashboard](../images/home-assistant-dashboard.png)

![Home Assistant Roon Web Display](../images/home-assistant_roon-display.png)

![Home Assistant ROCK](../images/home-assistant_roon-rock.png)

### Raw Source Code of the ROCK card

```
title: Home
views:
  - path: default_view
    title: Home
    panel: false
    type: 'custom:masonry-layout'
    layout:
      max_cols: 3
    icon: 'si:Home Assistant'
    badges: []
    cards:
      - type: vertical-stack
        cards:
          - type: grid
            cards:
              - type: button
                tap_action:
                  action: toggle
                entity: switch.kuchenlicht
                icon: 'mdi:lightbulb'
                show_name: false
              - type: button
                tap_action:
                  action: toggle
                entity: switch.dunstabzugshaube
                icon: 'mdi:stove'
                show_name: false
              - type: button
                tap_action:
                  action: toggle
                entity: switch.wohnzimmer
                icon: 'mdi:fan'
                show_name: false
              - type: button
                tap_action:
                  action: toggle
                entity: switch.tv_licht
                icon: 'mdi:television-ambient-light'
                show_name: false
              - type: button
                tap_action:
                  action: toggle
                entity: switch.hdmi_0
                show_state: false
                show_name: false
              - type: button
                tap_action:
                  action: more-info
                entity: binary_sensor.wohnzimmer_klein
                icon: 'mdi:window-shutter'
                show_name: false
              - type: button
                tap_action:
                  action: more-info
                entity: binary_sensor.wohnzimmer_balkontur
                show_name: false
            square: true
            columns: 7
          - type: entities
            entities:
              - entity: sensor.zuk_z1_akkufullstand
                name: Handy
              - entity: sensor.lenovo_tab_2_a10_70f_akkufullstand
                name: Tablet
            state_color: true
          - type: 'custom:xiaomi-vacuum-card'
            entity: vacuum.e0001103417610630506
            name: false
            vendor: deebot_slim
            buttons:
              locate: false
              spot:
                show: true
            attributes:
              side_brush:
                label: 'Bürsten: '
                unit: ' Std.'
              filter:
                label: 'Filter: '
                unit: ' Std.'
          - type: entities
            entities:
              - entity: sensor.time
              - entity: timer.cooking_timer
              - entity: input_number.timer_minutes
              - entity: script.timer_start
              - entity: script.timer_cancel
      - type: entities
        entities:
          - type: 'custom:mini-media-player'
            entity: media_player.wohnzimmer
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              controls: true
              icon: true
              info: true
              mute: true
              name: false
              power: true
              progress: true
              source: true
              volume_level: false
            speaker_group:
              platform: sonos
              show_group_count: true
              entities:
                - entity_id: media_player.wohnzimmer
                  name: Wohnzimmer
                - entity_id: media_player.kuche
                  name: Küche
                - entity_id: media_player.buro
                  name: Büro
                - entity_id: media_player.bad
                  name: Bad
                - entity_id: media_player.schlafzimmer
                  name: Schlafzimmer
          - type: 'custom:mini-media-player'
            entity: media_player.wohnzimmer_2
            artwork: full-cover-fit
            group: true
            hide:
              icon: true
              mute: true
              name: true
              power: true
              progress: true
              volume: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.kopfhorer
            artwork: full-cover-fit
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              icon: true
              mute: true
              power: true
              progress: true
              volume: true
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.kuche_2
            group: true
            artwork: full-cover-fit
            volume_stateless: true
            volume_step: 1
            hide:
              icon: true
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.buro_2
            artwork: full-cover-fit
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              icon: true
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.bad_2
            artwork: full-cover-fit
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              icon: true
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.schlafzimmer_2
            artwork: full-cover-fit
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              icon: true
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
      - type: vertical-stack
        cards:
          - type: weather-forecast
            entity: weather.home
            secondary_info_attribute: humidity
          - type: entities
            entities:
              - entity: sensor.kuche_temperature_sensor
                name: 'Aktuell:'
            show_header_toggle: false
            state_color: false
            title: Küche
          - type: 'custom:simple-thermostat'
            entity: climate.wohnzimmer
            control: false
            layout:
              step: row
              mode:
                names: true
                icons: true
                headings: true
            header:
              toggle:
                entity: switch.wohnzimmer
                name: Ventilator
            decimals: '1'
            view_layout:
              step: row
              mode:
                names: true
                icons: true
                headings: true
          - type: 'custom:simple-thermostat'
            entity: climate.bad
            control: false
            layout:
              step: row
            view_layout:
              step: row
          - type: 'custom:simple-thermostat'
            entity: climate.schlafzimmer
            control: false
            layout:
              step: row
          - type: 'custom:simple-thermostat'
            entity: climate.buro
            control: false
            layout:
              step: row
  - title: Remote
    path: remote
    type: 'custom:grid-layout'
    icon: 'mdi:remote'
    badges: []
    cards:
      - type: grid
        cards:
          - type: button
            tap_action:
              action: toggle
            entity: switch.hdmi_0
            show_state: false
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.sonos_sub_state
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.night_sound
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.speech_enhance
            show_name: false
        columns: 4
        square: false
      - type: entities
        entities:
          - type: 'custom:mini-media-player'
            entity: media_player.wohnzimmer_2
            group: true
            artwork: full-cover-fit
            info: short
            volume_stateless: true
            volume_step: 1
            hide:
              icon: true
              mute: true
              name: true
              power: true
              progress: true
              volume_level: false
          - type: 'custom:mini-media-player'
            entity: media_player.android_tv_1
            group: true
            name: TV
            hide:
              icon: true
              power: true
              power_state: false
              state_label: false
              volume: true
  - title: Wartung
    path: fritzbox
    icon: 'mdi:tools'
    badges: []
    cards:
      - type: entities
        entities:
          - entity: binary_sensor.fritzbox_7490_connectivity
          - entity: switch.fritzbox_7490_wifi
          - entity: switch.fritzbox_7490_wifi_5ghz
          - entity: switch.fritzbox_7490_guest_wifi
        state_color: true
        show_header_toggle: false
        title: Fritz!Box
      - type: picture
        image: /local/img/fritz_guest_wifi.png
        hold_action:
          action: none
        tap_action:
          action: url
          url_path: 'https://fritz.box/'
      - type: glance
        entities:
          - entity: sensor.nuc_cpu_temperature
          - entity: sensor.hacs
          - entity: binary_sensor.updater
          - entity: binary_sensor.check_home_assistant_configuration_update_available
          - entity: sensor.check_home_assistant_configuration_version
        show_name: true
        state_color: true
        show_state: true
        title: NUC
        columns: 3
      - type: entities
        entities:
          - entity: sensor.wohnzimmer_battery
          - entity: sensor.bad_battery
          - entity: sensor.buro_battery
          - entity: sensor.schlafzimmer_battery
        state_color: true
  - title: ROCK
    type: 'custom:masonry-layout'
    layout:
      width: 300
      max_cols: 3
    theme: Caule Light Blue
    icon: 'mdi:server'
    badges: []
    cards:
      - type: vertical-stack
        cards:
          - type: iframe
            url: 'http://rock'
            aspect_ratio: 350%
      - type: vertical-stack
        cards:
          - type: markdown
            content: >-
              ### Intel NUC-Kit NUC8i3BEH


              **RAM**

              Crucial CT8G4SFS8266 8GB, DDR4, 2666 MT/s, PC4-21300, Single Rank
              x8, SODIMM, 260-Pin


              **System SSD**

              Transcend 128GB PCIe Gen3 x4 M.2 SSD 2280


              **Internal Music Storage**

              Samsung MZ-76E1T0B/EU 860 EVO 1TB SATA 2,5"
          - type: sensor
            entity: sensor.rock_current_power
            graph: line
            name: Current Power Consumption
            hours_to_show: 4
          - type: sensor
            entity: sensor.rock_temperature_sensor
            graph: line
            name: Ambient Temperature
            hours_to_show: 4
          - type: entity
            entity: sensor.rock_total_consumption
            name: Total Power Consumption (since 2021/05/10)
      - type: vertical-stack
        cards:
          - type: entity
            entity: sensor.florib
            name: Now Playing
            icon: 'si:Last.fm'
          - type: entity
            entity: sensor.florib
            attribute: last_played
            name: Last Played
            icon: 'si:Last.fm'
          - type: entity
            entity: sensor.florib
            attribute: play_count
            unit: Tracks
            name: Scrobbles
            icon: 'si:Last.fm'
      - type: history-graph
        entities:
          - entity: media_player.kopfhorer
            name: Headphone
          - entity: media_player.wohnzimmer_2
            name: Living Room
          - entity: media_player.kuche_2
            name: Kitchen
          - entity: media_player.buro_2
            name: Office
          - entity: media_player.bad_2
            name: Bathroom
          - entity: media_player.schlafzimmer_2
            name: Bedroom
        hours_to_show: 4
        refresh_interval: 0
        title: Player History
  - title: Firefox
    path: firefox
    icon: 'si:firefox'
    badges: []
    cards:
      - type: grid
        cards:
          - type: button
            tap_action:
              action: toggle
            entity: switch.kuchenlicht
            icon: 'mdi:lightbulb'
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.dunstabzugshaube
            icon: 'mdi:stove'
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.wohnzimmer
            icon: 'mdi:fan'
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.tv_licht
            icon: 'mdi:television-ambient-light'
            show_name: false
          - type: button
            tap_action:
              action: toggle
            entity: switch.hdmi_0
            show_state: false
            show_name: false
          - type: button
            tap_action:
              action: more-info
            entity: binary_sensor.wohnzimmer_klein
            icon: 'mdi:window-shutter'
            show_name: false
          - type: button
            tap_action:
              action: more-info
            entity: binary_sensor.wohnzimmer_balkontur
            show_name: false
        square: true
        columns: 7
      - type: entities
        entities:
          - type: 'custom:mini-media-player'
            entity: media_player.wohnzimmer
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              controls: true
              icon: true
              info: true
              mute: true
              name: false
              power: true
              progress: true
              source: true
              volume_level: false
            speaker_group:
              platform: sonos
              show_group_count: true
              entities:
                - entity_id: media_player.wohnzimmer
                  name: Wohnzimmer
                - entity_id: media_player.kuche
                  name: Küche
                - entity_id: media_player.buro
                  name: Büro
                - entity_id: media_player.bad
                  name: Bad
                - entity_id: media_player.schlafzimmer
                  name: Schlafzimmer
          - type: 'custom:mini-media-player'
            entity: media_player.wohnzimmer_2
            group: true
            hide:
              mute: true
              name: true
              power: true
              progress: true
              volume: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.kopfhorer
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              mute: true
              power: true
              progress: true
              volume: true
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.kuche_2
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.buro_2
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.bad_2
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
          - type: 'custom:mini-media-player'
            entity: media_player.schlafzimmer_2
            group: true
            volume_stateless: true
            volume_step: 1
            hide:
              mute: true
              power: true
              progress: true
              volume_level: false
            idle_view:
              when_idle: true
              when_paused: true
              when_standby: true
```

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
      - [ ] Transfer zones
    - [x] [Mini Media Player](https://github.com/kalkih/mini-media-player) (Customizable media player card for Home Assistant Lovelace UI)
    - [ ] Remote control with [roon-cec-controller-extension](https://github.com/benjaminbellamy/roon-cec-controller-extension)
      - [x] Start/pause
      - [ ] ~Forward~ (my remote control does not send a command for this)
      - [ ] ~Backward~ (my remote control does not send a command for this)
      - [ ] Fast forward (has to be modified)
      - [x] Rewind
      - [ ] Volume
* TV
  - [x] Turn TV on [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/)
  - [x] Turn TV off [HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/)
  - [ ] Control TV
    - ~[HDMI-CEC](https://www.home-assistant.io/integrations/hdmi_cec/) or~ (my TV only sends a little few CEC commands) [Android TV](https://www.home-assistant.io/integrations/androidtv/)
  - [ ] [Notifications for Android TV / FireTV ](https://www.home-assistant.io/integrations/nfandroidtv/)
* AVM FRITZ!Box
  - [x] Sensor for internet connectivity (with external IP and uptime attributes) [FRITZ!Box Tools](https://github.com/mammuth/ha-fritzbox-tools)
  - [x] Turn on/off wifi and guest wifi [FRITZ!Box Tools](https://github.com/mammuth/ha-fritzbox-tools)
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

All commands as `root`

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

`sudo groupadd dialout`

`sudo gpasswd -a USER dialout`

`sudo usermod -a -G dialout USER`

`sudo chmod a+rw /dev/ttyACM0`

`configuration.yaml`:

```
hdmi_cec:
#  devices:
#    TV: 0.0.0.0
#    PulseEight: 3.0.0.0
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
