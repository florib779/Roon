## Operation System

https://dietpi.com/downloads/images/DietPi_NativePC-UEFI-x86_64-Bullseye_Installer.7z

## Beets

[Configuration](https://github.com/florib779/beets-config)

## Songkong Remote (Docker)

1. `docker pull songkong/songkong`
2. `docker run --restart unless-stopped -v /mnt/dietpi_userdata:/songkong -v /mnt/music:/music -p 4567:4567 songkong/songkong`

## Backups (Music Files)

### Commands

#### Remote (Dropbox)

* `rclone copy -P /mnt/music Dropbox:Backups/Music/music -v --log-file=rclone.log`

~#### Local~

~* `rclone copy -P /mnt/internal /mnt/external/work/backups -v --log-file=rclone.log`~

~#### Web-GUI~

~* `rclone rcd --rc-web-gui --rc-addr=IP:5572 --rc-user USER --rc-pass PASSWORD # Has to be the IP address, NOT the hostname`~

### ToDo

- [ ] cron job

### Links

[https://github.com/rclone/rclone](https://rclone.org/dropbox/)

## Links

* [Intel NUC/Debian Linux based RoonServer success story](https://community.roonlabs.com/t/intel-nuc-debian-linux-based-roonserver-success-story/14074)
