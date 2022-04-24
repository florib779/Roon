# My Debian based Roon Server

## Operation System

[Debian Bullseye netinst](https://www.debian.org/releases/bullseye/debian-installer/index.en.html)

### Advanced

#### /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# systemd generates mount units based on this file, see systemd.mount(5).
# Please run 'systemctl daemon-reload' after making changes here.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p1 during installation
UUID=0f26d3ed-dfaf-41d8-b814-26f1fbeb1a29 /                             ext4    errors=remount-ro       0       1
# /mnt/external/roon-backups was on /dev/sdb1 during installation
UUID=e00cd351-08fe-4094-9e8d-9f8c68ac5da4 /mnt/external/roon-backups    ext4    defaults                0       2
# /mnt/external/work was on /dev/sdc1 after installation
UUID=5d27fa62-e5c2-450f-b8cd-4b3d5ddd810b /mnt/external/work            ext4    defaults                0       2
# /mnt/internal/music was on /dev/sda1 during installation
UUID=bcfec288-aa6d-4c68-86cf-bc85203df7e6 /mnt/internal/music           ext4    defaults                0       2
# swap was on /dev/nvme0n1p5 during installation
UUID=df58f885-93af-4715-917c-9c9754499d5a none                          swap    sw                      0       0
```
#### Allow root login

1. `sudo nano /etc/ssh/sshd_config`
2. `PasswordAuthentication yes`
3. `PermitRootLogin yes`
4. `sudo service ssh restart`
5. `sudo passwd root`

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
#@audio - memlock unlimited # ToDo: This may be why the memory was always full.
@audio - nice -10
``` 
3. `sudo reboot`
4. `uname -r # Check which kernel is running`
5. `sudo apt remove linux-image-5.10.0-8-amd64`

### Docker

For Home Assistant and poss. roon-extension-manager.

1. `sudo apt install -y docker.io`
2. `sudo usermod -aG docker user # Add our linux user to the Docker group`
3. `docker --version # Check if Docker is running

## Home Assistant

[See here.](https://github.com/florib779/Roon/blob/master/articles/home-assistant-smart-home.md)

## Beets

[See here.](https://github.com/florib779/beets-config)

## Homebridge

### Installation

`docker run --net=host --name=homebridge -v $(pwd)/homebridge:/homebridge oznu/homebridge:ubuntu`

### Start script

`/etc/systemd/system/homebridge.service`:

```
[Unit]
Description=Homebridge

[Service]
ExecStart=docker start homebridge

[Install]
WantedBy=multi-user.target
```

## Songkong Remote

### Start script

`/etc/systemd/system/songkong-remote.service`:

```
[Unit]
Description=Songkong Remote
After=network.target

[Service]
Type=simple
WorkingDirectory=/home/flori/songkong/
ExecStart=/bin/bash songkongremote.sh
User=flori

[Install]
WantedBy=multi-user.target
``` 

## Backups (Music Files)

### Installation

* `sudo apt install rclone`

### Commands

#### Remote (Dropbox)

* `rclone copy -P /mnt/internal remote:Backups/Music -v --log-file=rclone.log`

#### Local

* `rclone copy -P /mnt/internal /mnt/external/work/backups -v --log-file=rclone.log`

#### Web-GUI

* `rclone rcd --rc-web-gui --rc-addr=IP:5572 --rc-user USER --rc-pass PASSWORD # Has to be the IP address, NOT the hostname`

### Links

https://github.com/rclone/rclone

## Cockpit

### Applications

#### Navigator (File Manager)

1. `wget https://github.com/45Drives/cockpit-navigator/releases/download/v0.5.5/cockpit-navigator_0.5.5-2focal_all.deb`
2. `sudo apt install ./cockpit-navigator_0.5.5-2focal_all.deb`

## Links

* [Intel NUC/Debian Linux based RoonServer success story](https://community.roonlabs.com/t/intel-nuc-debian-linux-based-roonserver-success-story/14074)
