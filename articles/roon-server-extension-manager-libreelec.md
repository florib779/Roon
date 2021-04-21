# RoonServer and roon-extension-manager on LibreElec (Kodi)

## Kodi
### Addons

* Chrome
* Docker
  * RoonServer

## Roon

Login to your LibreElec instance with ssh.

### Roon Server

[https://hub.docker.com/r/steefdebruijn/docker-roonserver](https://hub.docker.com/r/steefdebruijn/docker-roonserver)

It uses Docker volumes for the app, the data(base), the music and backups. The app volume is used to pull the Roon Server software from Roonlabs on first run if this volume is empty. This is useful if you use a scheme of recreating application containers on every restart. Selfupdates from Roonlabs work as expected. Adjust startup parameters (volume mappings) to your liking.

`chown -cR root:root /media/Backups` (my USB stick for backups)

```
docker run -d \
  --net=host \
  -e TZ=Europe/Berlin \
  -v /storage/roon-app:/app \
  -v /storage/roon-data:/data \
  -v /media/sdb1-usb-SABRENT_SABRENT_/Music_Roon:/music \
  -v /media/Backups/RoonBackups:/backup \
  steefdebruijn/docker-roonserver:latest
```

`touch /storage/.config/system.d/roonserver.service`

```
[Unit]
Description=Roon
After=docker.service
Requires=docker.service

[Service]
TimeoutStartSec=0
TimeoutStopSec=180
ExecStartPre=-/storage/.kodi/addons/service.system.docker/bin/docker kill %n
ExecStartPre=-/storage/.kodi/addons/service.system.docker/bin/docker rm -f %n
ExecStartPre=/storage/.kodi/addons/service.system.docker/bin/docker pull steefdebruijn/docker-roonserver
ExecStart=/storage/.kodi/addons/service.system.docker/bin/docker \
  run --name %n \
  --net=host \
  -e TZ=Europe/Berlin \
  -v /storage/roon-app:/app \
  -v /storage/roon-data:/data \
  -v /media/sdb1-usb-SABRENT_SABRENT_/Music_Roon:/music \
  -v /media/Backups/RoonBackups:/backup \
  steefdebruijn/docker-roonserver
ExecStop=/storage/.kodi/addons/service.system.docker/bin/docker stop %n
Restart=always
RestartSec=10s

[Install]
WantedBy=multi-user.target
```

Change CEC settings in Kodi to keep roon-server alive when the tv is off.
