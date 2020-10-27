# RoonServer and roon-extension-manager on LibreElec (Kodi)

## Kodi
### Addons

* Chrome
* Docker
  * RoonServer
  * roon-extension-manager

## Roon

Login to your LibreElec instance with ssh.

### Roon Server

[https://hub.docker.com/r/steefdebruijn/docker-roonserver](https://hub.docker.com/r/steefdebruijn/docker-roonserver)

It uses docker volumes for the app, the data(base), the music and backups. The app volume is used to pull the roon server software from roonlabs on first run if this volume is empty. This is useful if you use a scheme of recreating application containers on every restart. Selfupdates from roonlabs work as expected. Adjust startup parameters (volume mappings) to your liking.

`chown -cR root:root /media/Backups` (my USB-Stick for backups)

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

Change CEC-settings in Kodi to keep roon-server alive when the tv is off.

### roon-extension-manager

[https://github.com/TheAppgineer/roon-extension-manager/wiki/Installation](https://github.com/TheAppgineer/roon-extension-manager/wiki/Installation)

With docker there are more extensions available.

`docker pull theappgineer/roon-extension-manager`

```
docker run -d \
  --network=host \
  --restart unless-stopped \
  --name roon-extension-manager \
  -v roon-extensions:/root/.RoonExtensions/lib \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -e Europe/Berlin \
  theappgineer/roon-extension-manager:latest
```

### roon-extension-alarm-clock

Did’t work with roon-extension-manager Ropieee's implementation didn’t work too.

So I installed it as docker-image:

`mkdir /storage/roon-extension-alarm-clock`

`touch config.json`

`docker pull theappgineer/roon-extension-alarm-clock`

```
docker run -d \
  --network=host \
  --restart unless-stopped \
  --name roon-extension-alarm-clock \
  -v /storage/roon-extension-alarm-clock/config.json:/usr/src/app/config.json \
  -e TZ=Europe/Berlin \
  theappgineer/roon-extension-alarm-clock:latest
  ```
