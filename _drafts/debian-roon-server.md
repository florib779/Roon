## Operation System

Debian Bullseye Netinstall

### Post-install

1. `su -`
2. `apt update && apt install sudo -y`
3. `adduser username sudo`

~`sudo apt install sudo curl apt-transport-https ca-certificates curl gnupg lsb-release ffmpeg cifs-utils autofs python3-pip python-rgain smartmontools lm-sensors`~

#### Create mount points

`sudo apt install autofs`

## Roon server

1. `wget http://download.roonlabs.com/builds/roonserver-installer-linuxx64.sh`
2. `chmod +x roonserver-installer-linuxx64.sh`
3. `sudo ./roonserver-installer-linuxx64.sh`
4. `roonserver-installer-linuxx64.sh`

### Audio tuning

`sudo apt update && sudo apt install linux-image-rt-amd64`

`sudo nano /etc/security/limits.conf`

```
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -10
``` 

## Beets

## Home Assistant

### Docker

`wget -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`

```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

`sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io`

## Dropbox

1. `sudo wget -O /usr/local/bin/dropbox "https://www.dropbox.com/download?dl=packages/dropbox.py"`
2. `sudo chmod +x /usr/local/bin/dropbox`
3. `dropbox start -i`

## Links

* [Intel NUC/Debian Linux based RoonServer success story](https://community.roonlabs.com/t/intel-nuc-debian-linux-based-roonserver-success-story/14074)
