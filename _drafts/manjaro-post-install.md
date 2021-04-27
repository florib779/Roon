# Arch/Manjaro Linux post installation things

## Enable SSH

### Install SSH package

`sudo pacman -S openssh`

### Enable SSH Service

`sudo systemctl start sshd`

### Check SSH Status

`sudo systemctl status sshd`

## Enable ssh root login

`sudo nano /etc/ssh/sshd_config`

### Find the following lines and make some changes to it.

```
#PermitRootLogin prohibit-password
PermitRootLogin yes
PasswordAuthentication yes
```

### Restart SSH service

`sudo systemctl restart sshd`

## Enable AUR repository

`sudo pacman -S pacaur`

## Software

* Audacity
* Home Assistant (Docker)
* node-sonos-http-api
* Karaoke Lyric Editor (karlyric)
* MusicBrainz Picard
* Roon
* Songkong

## Links

* https://manjaro.site/enable-ssh-root-login-arch-linux-2017/
* https://manjaro.site/how-to-install-docker-on-manjaro-18-0/
