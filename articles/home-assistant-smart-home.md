# My Smart Home project with Home Assistant

You can find some of my Home Assistant configuration files and possibilities [here](https://github.com/florib779/homeassistant-config).

## Dashboards

Some details about some of my dashboards:

* [Screenshots](https://github.com/florib779/homeassistant-config/tree/master/screenshots)
* [Home Assistant Roon ROCK Dashboard](home-assistant-roon-rock-view.md)
* [Modified version of the Roon Web Display](roon-web-display.md)

## Installation

I am currently running Home Assistant Supervised on an Intel NUC with [Debian Bullseye](https://www.debian.org/releases/bullseye/index.en.html), because my RaspberryPi 3 was a bit sluggish.

1. `sudo apt install -y network-manager jq`
2. `sudo curl -Lo installer.sh https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh`
3. `sudo bash installer.sh --machine qemux86-64`

After a while, the script will ask the following question:

`Do you want to proceed with overwriting the /etc/network/interfaces file? [N/y]`

Choose "Yes".

4. `sudo rm installer.sh`

[Source](https://peyanski.com/how-to-install-home-assistant-supervised-official-way/#Home_Assistant_Supervised_method)

### Install HACS

`sudo docker exec -ti homeassistant /bin/bash`

`wget -q -O - https://install.hacs.xyz | bash -`

After that go go `Settings > Integrations > Add Integration` and enable it. Follow the instructions.

[Source](https://hacs.xyz/docs/installation/installation/)

## Links
* [Awesome Home Assistant](https://www.awesome-ha.com)
* [HACS Repositories](https://hacs-repositories.web.app/)
* [Sonos Dashboard](https://community.home-assistant.io/t/sonos-dashboard/18843)
* [HA-Sonos](https://github.com/vmcosco/HA-Sonos)
