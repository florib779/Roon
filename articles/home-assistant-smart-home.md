# My Smart Home project with Home Assistant

You can find some of my Home Assistant configuration files and possibilities [here](https://github.com/florib779/homeassistant-config).

## Dashboards

Some details about some of my dashboards:

* [Screenshots](https://github.com/florib779/homeassistant-config/tree/master/screenshots)
* [Home Assistant Roon ROCK Dashboard](home-assistant-roon-rock-view.md)
* [Modified version of the Roon Web Display](roon-web-display.md)

## Installation

I am currently running Home Assistant Supervised on an Intel NUC with [Debian Buster](https://www.debian.org/releases/buster/index.en.html), because my RaspberryPi 3 was a bit sluggish.

1. `sudo usermod -aG docker user # Add our linux user to the Docker group`
2. `docker --version # Check if Docker is running`
3. `sudo curl -Lo installer.sh https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh`
4. `sudo bash installer.sh --machine qemux86-64`

After a while, the script will ask the following question:

`Do you want to proceed with overwriting the /etc/network/interfaces file? [N/y]`

Choose "Yes".

[Source](https://peyanski.com/how-to-install-home-assistant-supervised-official-way/#Home_Assistant_Supervised_method)

### Install HACS

`sudo docker exec -ti homeassistant /bin/bash`

`wget -q -O - https://install.hacs.xyz | bash -`

[Source](https://hacs.xyz/docs/installation/installation/)

### node-sonos-http-api

1. ```mkdir node-sonos-http-api```
2. ```cd node-sonos-http-api```
3.``` mkdir clips```
4. ```mkdir settings```
5. ```mkdir cache```
6. ```mkdir presets```
7. ``` curl https://raw.githubusercontent.com/jishi/node-sonos-http-api/master/presets/example.json > presets/example.json echo {} > settings/settings.json```

```
docker run \
  --net=host \
  --name sonos \
  --restart=always \
  -d \
  -v `pwd`/settings:/app/settings \
  -v `pwd`/clips:/app/static/clips \
  -v `pwd`/cache:/app/cache \
  -v `pwd`/presets:/app/presets \
  chrisns/docker-node-sonos-http-api
```

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
