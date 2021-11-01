# Home Assistant Roon ROCK Dashboard

## Screenshots

![Home Assistant Roon ROCK display 1](https://github.com/florib779/homeassistant-config/blob/7e360416e20a81d5c4d254ffe268ec01e47c0de8/screenshots/ha_roon_rock_dashboard.png)

![Home Assistant Roon ROCK display 2](https://github.com/florib779/homeassistant-config/blob/7e360416e20a81d5c4d254ffe268ec01e47c0de8/screenshots/ha_roon_rock_dashboard_2.png)

## Requirements
* [card-mod](https://github.com/thomasloven/lovelace-card-mod) (Custom CSS)
* [hass-simpleicons](https://github.com/vigonotion/hass-simpleicons)
* [lovelace-layout-card](https://github.com/thomasloven/lovelace-layout-card)
* [Roon Integration](https://www.home-assistant.io/integrations/roon/)

## Code

```
title: Home
views:
```

[...]

```
  - title: ROCK
    type: custom:masonry-layout
    layout:
      width: 300
      max_cols: 3
    theme: Caule Light Blue
    icon: mdi:server
    badges: []
    cards:
      - type: vertical-stack
        cards:
          - type: iframe
            url: http://rock
            aspect_ratio: 520%
      - type: vertical-stack
        cards:
          - type: picture-elements
            elements:
              - type: image
                image: /local/img/roon-moon-white.png
                style:
                  top: 49%
                  left: 28%
                  color: white
              - type: icon
                tap_action:
                  action: toggle
                entity: switch.wol_rock
                name: WOL
                icon: mdi:power
                icon_height: 10px
                show_name: true
                show_state: true
                show_icon: true
                hold_action:
                  action: none
                style:
                  top: 50%
                  left: 70%
                  color: '#3073ad'
            image: /local/img/rock_akasa_case_front.jpg
          - type: markdown
            style:
              ha-markdown:
                $: |
                  ha-markdown-element { /* body */
                    font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
                    font-size: 14px;
                    line-height: 1.42857143;
                    color: #333;
                  }
                  h1, h2, h3, h4, h5, h6 {
                    font-family: inherit;
                    line-height: 1.1;
                    color: inherit;
                  }
                  h4, h5, h6 {
                    margin-top: 10px;
                    margin-bottom: 10px;
                  }
                  h1 { /* h3 */
                    font-size: 24px;
                    font-weight: 400;
                    margin-top: 10px;
                    margin-bottom: 10px;
                    padding-top: 20px; /* modification */
                  }
                  h2, ha-markdown-element h2 { /* h6 */
                    font-size: 12px;
                    font-weight: normal;
                    margin-top: 10px;
                    margin-bottom: 10px;
                  }
                  h3 { /* .statusheader */
                    font-size: 1.2em;
                    font-weight: 700;
                    margin-top: 40px;
                    margin-bottom: 0;
                  }
                  p {
                    margin-top: 0;
                  }
                  img { /* Pseudo image to create spaces */
                    height: 1.5em;
                  }
            content: >-
              # Hardware

              ## Intel NUC-Kit NUC8i3BEH

              ### Stats

              Case temperature {{states('sensor.rock_temperature') }} °C.

              Current power consumption {{ states('sensor.rock_current_power')
              }} Watt.

              {{ states('sensor.rock_total_consumption') }} kWh total power
              consumption since May 10, 2021.

              ### RAM

              ![]() 

              Crucial CT8G4SFS8266 8GB, DDR4, 2666 MT/s, PC4-21300, Single Rank
              x8, SODIMM, 260-Pin.

              ### CD Drive

              ![]()

              LG Slim Portable DVD Writer, GP50NW40

              ### System SSD

              ![]() 

              Transcend 128GB PCIe Gen3 x4 M.2 SSD 2280<br><br>


              ### Internal Music SSD

              ![]() 

              Samsung MZ-76E1T0B/EU 860 EVO 1TB SATA 2,5"<br><br>

              # Network Zones

              ### Headphones

              **Model:** {{ state_attr('device_tracker.raspberrypi_3',
              'friendly_name') }}

              **Connection:** CAT 7

              **Host Name:** {{ state_attr('device_tracker.raspberrypi_3',
              'host_name') }}

              **IP Address:** {{ state_attr('device_tracker.raspberrypi_3',
              'ip') }}

              **MAC:** {{ state_attr('device_tracker.raspberrypi_3', 'mac') }}

              ### Livingroom

              **Model:** {{
              state_attr('device_tracker.livingroom_sonos_playbase',
              'friendly_name') }}

              **Connection:** 1 GB digital

              **Host Name:** {{
              state_attr('device_tracker.livingroom_sonos_playbase',
              'host_name') }}

              **IP Address:** {{
              state_attr('device_tracker.livingroom_sonos_playbase', 'ip') }}

              **MAC:** {{ state_attr('device_tracker.livingroom_sonos_playbase',
              'mac') }}

              + **Model:** {{
              state_attr('device_tracker.livingroom_sonos_play1_rl',
              'friendly_name') }}
                **Host Name:** {{ state_attr('device_tracker.livingroom_sonos_play1_rl',
              'host_name') }}
                **IP Address:** {{
              state_attr('device_tracker.livingroom_sonos_play1_rl', 'ip') }}
                **MAC:** {{ state_attr('device_tracker.livingroom_sonos_play1_rl',
              'mac') }}

              + **Model:** {{
              state_attr('device_tracker.livingroom_sonos_play1_rr',
              'friendly_name') }}
                **Host Name:** {{ state_attr('device_tracker.livingroom_sonos_play1_rr',
              'host_name') }}
                **IP Address:** {{
              state_attr('device_tracker.livingroom_sonos_play1_rr', 'ip') }}
                **MAC:** {{ state_attr('device_tracker.livingroom_sonos_play1_rr',
              'mac') }}

              + **Model:** {{ state_attr('device_tracker.livingroom_sonos_sub',
              'friendly_name') }}
                **Host Name:** {{ state_attr('device_tracker.livingroom_sonos_sub',
              'host_name') }}
                **IP Address:** {{
              state_attr('device_tracker.livingroom_sonos_sub', 'ip') }}
                **MAC:** {{ state_attr('device_tracker.livingroom_sonos_sub',
              'mac') }}


              ### Bedroom

              **Model:** {{ state_attr('device_tracker.bedroom_sonos_playbar',
              'friendly_name') }}

              **Connection:** SonosNet

              **Host Name:** {{
              state_attr('device_tracker.bedroom_sonos_playbar', 'host_name') }}

              **IP Address:** {{
              state_attr('device_tracker.bedroom_sonos_playbar', 'ip') }}

              **MAC:** {{ state_attr('device_tracker.bedroom_sonos_playbar',
              'mac') }}

              ### Kitchen

              **Connection:** SonosNet

              1. **Model:** {{
              state_attr('device_tracker.kitchen_sonos_play1_left',
              'friendly_name') }}
                 **Host Name:** {{ state_attr('device_tracker.kitchen_sonos_play1_left',
              'host_name') }}
                 **IP Address:** {{ state_attr('device_tracker.kitchen_sonos_play1_left', 'ip')
              }}
                 **MAC:** {{ state_attr('device_tracker.kitchen_sonos_play1_left', 'mac') }}
              2. **Model:** {{
              state_attr('device_tracker.kitchen_sonos_play1_right',
              'friendly_name') }}
                 **Host Name:** {{ state_attr('device_tracker.kitchen_sonos_play1_right',
              'host_name') }}
                 **IP Address:** {{ state_attr('device_tracker.kitchen_sonos_play1_right',
              'ip') }}
                 **MAC:** {{ state_attr('device_tracker.kitchen_sonos_play1_right', 'mac') }}

              ### Office

              **Connection:** SonosNet

              1. **Model:** {{
              state_attr('device_tracker.office_sonos_one_left',
              'friendly_name') }}
                 **Host Name:** {{ state_attr('device_tracker.office_sonos_one_left',
              'host_name') }}
                 **IP Address:** {{ state_attr('device_tracker.office_sonos_one_left', 'ip') }}
                 **MAC:** {{ state_attr('device_tracker.office_sonos_one_left', 'mac') }}
              2. **Model:** {{
              state_attr('device_tracker.office_sonos_one_right',
              'friendly_name') }}
                 **Host Name:** {{ state_attr('device_tracker.office_sonos_one_right',
              'host_name') }}
                 **IP Address:** {{ state_attr('device_tracker.office_sonos_one_right', 'ip')
              }}
                 **MAC:** {{ state_attr('device_tracker.office_sonos_one_right', 'mac') }}
      - type: vertical-stack
        cards:
          - type: markdown
            style:
              ha-markdown:
                $: |
                  ha-markdown-element { /* body */
                    font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
                    font-size: 14px;
                    line-height: 1.42857143;
                    color: #333;
                    padding-bottom: 40px;
                  }
                  p {
                    padding-top: 5px;
                    padding-bottom: 5px;
                  }
            content: >-
              <a href="https://community.roonlabs.com"
              target="_blank">Community</a> - <a
              href="https://help.roonlabs.com" target="_blank">Help Center</a>
          - type: logbook
            style: |
              ha-card {
                    font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
                    font-size: 14px;
                    line-height: 1.42857143;
                    color: #333;
                    padding-bottom: 40px;
              }
              h1, h2, h3, h4, h5, h6 {
                    font-family: inherit;
                    line-height: 1.1;
                    color: inherit;
              }
              h1 {
                    font-size: 24px;
                    font-weight: 400;
                    margin-top: 10px;
                    margin-bottom: 10px;
                    padding-top: 20px; /* modification */
              }
            entities:
              - binary_sensor.fritzbox_7490_connectivity
              - media_player.roon_bathroom
              - media_player.roon_bedroom
              - media_player.roon_headphones
              - media_player.roon_kitchen
              - media_player.roon_livingroom
              - media_player.roon_office
              - sensor.rock_total_consumption
              - sensor.rock_current_power
              - switch.fritzbox_7490_wifi
              - switch.fritzbox_7490_wifi_5ghz
              - switch.rock
            hours_to_show: 24
            title: System Logbook
          - type: markdown
            style:
              ha-markdown:
                $: |
                  ha-markdown-element { /* body */
                    font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
                    font-size: 14px;
                    line-height: 1.42857143;
                    color: #333;
                  }
                  h1, h2, h3, h4, h5, h6 {
                    font-family: inherit;
                    line-height: 1.1;
                    color: inherit;
                  }
                  h4, h5, h6 {
                    margin-top: 10px;
                    margin-bottom: 10px;
                  }
                  h1 { /* h3 */
                    font-size: 24px;
                    font-weight: 400;
                    margin-top: 10px;
                    margin-bottom: 10px;
                    padding-top: 20px; /* modification */
                  }
                  h2, ha-markdown-element h2 { /* h6 */
                    font-size: 12px;
                    font-weight: normal;
                    margin-top: 10px;
                    margin-bottom: 10px;
                  }
                  h3 { /* .statusheader */
                    font-size: 1.2em;
                    font-weight: 700;
                    margin-top: 40px;
                    margin-bottom: 0;
                  }
                  p {
                    margin-top: 0;
                  }
                  img { /* Pseudo image to create spaces */
                    height: 2px;
                  }
            content: >-
              ![]()

              ### Last.fm

              Playing {{ states('sensor.lastfm') }}.

              Last played {{ state_attr('sensor.lastfm', 'last_played') }}.

              {{ state_attr('sensor.lastfm', 'play_count') }} scrobbles since
              May 6, 2008.

              # Other Network Devices

              ### Router

              **Model:** {{ state_attr('device_tracker.fritz_box',
              'friendly_name') }}

              **Internet:** {{ states('sensor.fritz_netmonitor') }}

              **Downstream:** {{ state_attr('sensor.fritz_netmonitor',
              'max_byte_rate_down') }}

              **Upstream:** {{ state_attr('sensor.fritz_netmonitor',
              'max_byte_rate_up') }}

              **IP Address:** {{ state_attr('device_tracker.fritz_box', 'ip') }}

              **MAC:** {{ state_attr('device_tracker.fritz_box', 'mac') }}

              ### Tablet

              **Model:** {{
              state_attr('device_tracker.mobile_lenovo_tab_2_a10_70f',
              'friendly_name') }}
              ([Info](https://pcsupport.lenovo.com/de/en/products/tablets/a-series/a10-70-2/solutions/pd104137))

              **OS:** Android 6

              **Akku:** {{ states('sensor.lenovo_tab_2_a10_70f_akkufullstand')
              }}%

              **Free Internal Storage:** {{
              states('sensor.lenovo_tab_2_a10_70f_interner_speicher') }} {{
              state_attr('sensor.lenovo_tab_2_a10_70f_interner_speicher',
              'unit_of_measurement') }}

              **Connection:** {{
              states('sensor.lenovo_tab_2_a10_70f_wlan_frequenz') }} {{
              state_attr('sensor.lenovo_tab_2_a10_70f_wlan_frequenz',
              'unit_of_measurement') }}, {{
              states('sensor.lenovo_tab_2_a10_70f_wlan_geschwindigkeit') }} {{
              state_attr('sensor.lenovo_tab_2_a10_70f_wlan_geschwindigkeit',
              'unit_of_measurement') }}

              **Host Name:** {{
              state_attr('device_tracker.mobile_lenovo_tab_2_a10_70f',
              'host_name') }}

              **IP Address:** {{
              state_attr('device_tracker.mobile_lenovo_tab_2_a10_70f', 'ip') }}

              **MAC:** {{
              state_attr('device_tracker.mobile_lenovo_tab_2_a10_70f', 'mac') }}

              ### Phone

              **Model:** {{ state_attr('device_tracker.mobile_zuk_z1',
              'friendly_name') }}
              ([Info](https://support.lenovo.com/pl/en/solutions/pd104309))

              **OS:** LineageOS 17.0 (Android 10)

              **Akku:** {{ states('sensor.zuk_z1_akkufullstand') }} %

              **Free Internal Storage:** {{
              states('sensor.zuk_z1_interner_speicher') }} {{
              state_attr('sensor.zuk_z1_interner_speicher',
              'unit_of_measurement') }}

              **Connection:** {{ states('sensor.zuk_z1_wlan_frequenz') }} {{
              state_attr('sensor.zuk_z1_wlan_frequenz', 'unit_of_measurement')
              }}, {{ states('sensor.zuk_z1_wlan_geschwindigkeit') }} {{
              state_attr('sensor.zuk_z1_wlan_geschwindigkeit',
              'unit_of_measurement') }}

              **Host Name:** {{ state_attr('device_tracker.mobile_zuk_z1',
              'host_name') }}

              **IP Address:** {{ state_attr('device_tracker.mobile_zuk_z1',
              'ip') }}

              **MAC:** {{ state_attr('device_tracker.mobile_zuk_z1', 'mac') }}

              ### Laptop

              **Model:** HP 350 G1

              **OS:** Manjaro Linux with Roon Desktop Version

              **Connection:** WLAN 2,4

              **Host Name:** {{ state_attr('device_tracker.mobile_laptop',
              'host_name') }}

              **IP Address:** {{ state_attr('device_tracker.mobile_laptop',
              'ip') }}

              **MAC:** {{ state_attr('device_tracker.mobile_laptop', 'mac') }}

              ### TV

              **Model:** TCL

              **OS:** Android

              **Connection:** 1GB digital

              **Host Name:** {{ state_attr('device_tracker.livingroom_tv',
              'host_name') }}

              **IP Address:** {{ state_attr('device_tracker.livingroom_tv',
              'ip') }}

              **MAC:** {{ state_attr('device_tracker.livingroom_tv', 'mac') }}

              #### Connected Computer

              **Model:** Intel NUC i5

              **OS:** Manjaro Linux with Roon Desktop Version

              **Connection:** 1GB digital

              **Host Name:** {{ state_attr('device_tracker.nuc', 'host_name') }}

              **IP Address:** {{ state_attr('device_tracker.nuc', 'ip') }}

              **MAC:** {{ state_attr('device_tracker.nuc', 'mac') }}
 ```
