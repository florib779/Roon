## Operation System

Debian Bullseye Netinstall

### Post-install

`sudo apt-get update`

`sudo apt-get install linux-image-rt-amd64`

`sudo reboot`

`sudo apt install sudo curl apt-transport-https ca-certificates curl gnupg lsb-release ffmpeg cifs-utils autofs python3-pip python-rgain smartmontools lm-sensors`

`curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`

```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
`sudo apt-get update`

`sudo apt-get install docker-ce docker-ce-cli containerd.io`

#### [Debian-Multimedia](https://www.deb-multimedia.org/)

`wget https://www.deb-multimedia.org/pool/main/d/deb-multimedia-keyring/deb-multimedia-keyring_2016.8.1_all.deb`

`sudo dpkg -i deb-multimedia-keyring_2016.8.1_all.deb`

`rm deb-multimedia-keyring_2016.8.1_all.deb`

Login as root:

1. `usermod -aG sudo USERNAME`
2. `reboot`

https://confluence.jaytaala.com/display/TKB/Mount+drive+in+linux+and+set+auto-mount+at+boot

`/etc/security/limits.conf`

```
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -10
``` 

## Roon server

1. `curl http://download.roonlabs.com/builds/roonserver-installer-linuxx64.sh`
2. `chmod +x roonserver-installer-linuxx64.sh`
3. `sudo ./roonserver-installer-linuxx64.sh`
4. `roonserver-installer-linuxx64.sh`

## [Roon-Extension-Manager](https://github.com/TheAppgineer/roon-extension-manager/wiki/Installation#linux)

1. `curl https://github.com/TheAppgineer/roon-extension-manager/raw/v1.x/rem-setup.sh`
2. `chmod +x rem-setup.sh`
3. `sudo ./rem-setup.sh`
4. `rm rem-setup.sh`

### Extensions

- [x] [roon-extension-alarm-clock](https://github.com/TheAppgineer/roon-extension-alarm-clock)
  - [ ] Possible with Home Assistant
- [x] [roon-extension-cd-ripper](https://github.com/TheAppgineer/roon-extension-cd-ripper)

## Beets (pip)

## Home Assistant

## Dropbox

1. `sudo wget -O /usr/local/bin/dropbox "https://www.dropbox.com/download?dl=packages/dropbox.py"`
2. `sudo chmod +x /usr/local/bin/dropbox`
3. `dropbox start -i`

## Links

* [Intel NUC/Debian Linux based RoonServer success story](https://community.roonlabs.com/t/intel-nuc-debian-linux-based-roonserver-success-story/14074)
