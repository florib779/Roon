## Operation System

Debian Bullseye Netinstall

Advanced

`/etc/fstab`
```
@audio - rtprio 99
#@audio - memlock unlimited # This may be why the memory was always full.
@audio - nice -10

### Post-install

~`sudo apt update && sudo apt install -y apt-transport-https ca-certificates gnupg lsb-release python3-pip python-rgain smartmontools lm-sensors`~

## Roon server

1. `sudo apt update && sudo apt install -y ffmpeg cifs-utils curl`
2. `wget http://download.roonlabs.com/builds/roonserver-installer-linuxx64.sh`
3. `chmod +x roonserver-installer-linuxx64.sh`
4. `sudo ./roonserver-installer-linuxx64.sh`
5. `rm roonserver-installer-linuxx64.sh`

### Audio tuning

1. `sudo apt update && sudo apt install -y linux-image-rt-amd64`
2. `sudo nano /etc/security/limits.conf`
```
@audio - rtprio 99
#@audio - memlock unlimited # This may be why the memory was always full.
@audio - nice -10
``` 
3. `sudo reboot`
4. `uname -r # Check which kernel is running`
5. `sudo apt remove linux-image-5.10.0-8-amd64

### Docker

For Home Assistant and poss. roon-extension-manager.

1. `sudo apt install -y docker.io`
2. `sudo usermod -aG docker user # Add our linux user to the Docker group`
3. `docker --version # Check if Docker is running

## Home Assistant

[See here.](https://github.com/florib779/Roon/blob/master/articles/home-assistant-smart-home.md)

## Beets

[See here.](https://github.com/florib779/beets-config)

## Dropbox

1. `sudo wget -O /usr/local/bin/dropbox "https://www.dropbox.com/download?dl=packages/dropbox.py"`
2. `sudo chmod +x /usr/local/bin/dropbox`
3. `dropbox start -i`

## Links

* [Intel NUC/Debian Linux based RoonServer success story](https://community.roonlabs.com/t/intel-nuc-debian-linux-based-roonserver-success-story/14074)
