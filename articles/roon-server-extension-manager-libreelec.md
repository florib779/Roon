# RoonServer and roon-extension-manager on LibreElec (Kodi)
<h2>Kodi</h2>
<h3>Addons</h3>
<ul>
<li>Chrome</li>
<li>Docker
<ul>
<li>RoonServer</li>
<li><a href="https://for-music-lovers.de/chiefmaster/index.php?option=com_weblinks&amp;view=weblink&amp;id=56&amp;catid=33&amp;Itemid=101">roon-extension-manager</a></li>
<li>roon-extension-alarm-clock</li>
</ul>
</li>
</ul>
<h2>Roon</h2>
<p>Login to your LibreElec instance with ssh.</p>
<h3>Roon Server</h3>
<p><a href="https://hub.docker.com/r/steefdebruijn/docker-roonserver">https://hub.docker.com/r/steefdebruijn/docker-roonserver</a></p>
<p>It uses docker volumes for the app, the data(base), the music and backups. The app volume is used to pull the roon server software from roonlabs on first run if this volume is empty. This is useful if you use a scheme of recreating application containers on every restart. Selfupdates from roonlabs work as expected. Adjust startup parameters (volume mappings) to your liking.</p>
<p><code>chown -cR root:root /media/Backups</code> (my USB-Stick for backups)</p>
<pre><code>docker run -d \
  --net=host \
  -e TZ=Europe/Berlin \
  -v /storage/roon-app:/app \
  -v /storage/roon-data:/data \
  -v /media/sdb1-usb-SABRENT_SABRENT_/Music_Roon:/music \
  -v /media/Backups/RoonBackups:/backup \
  steefdebruijn/docker-roonserver:latest
</code></pre>
<p><code>touch /storage/.config/system.d/roonserver.service</code></p>
<pre><code>[Unit]
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
</code></pre>
<p>Change CEC-settings in Kodi to keep roon-server alive when the tv is off.</p>
<h3>roon-extension-manager</h3>
<p><a href="https://github.com/TheAppgineer/roon-extension-manager/wiki/Installation">https://github.com/TheAppgineer/roon-extension-manager/wiki/Installation</a></p>
<p>With docker there are more extensions available.</p>
<p><code>docker pull theappgineer/roon-extension-manager</code></p>
<pre><code>docker run -d \
  --network=host \
  --restart unless-stopped \
  --name roon-extension-manager \
  -v roon-extensions:/root/.RoonExtensions/lib \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -e Europe/Berlin \
  theappgineer/roon-extension-manager:latest
</code></pre>
<h3>roon-extension-alarm-clock</h3>
<p>Did’t work with roon-extension-manager Ropieee's implementation didn’t work too.</p>
<p>So I installed it as docker-image:</p>
<p><code>mkdir /storage/roon-extension-alarm-clock</code></p>
<p><code>touch config.json</code></p>
<p><code>docker pull theappgineer/roon-extension-alarm-clock</code></p>
<pre><code>docker run -d \
  --network=host \
  --restart unless-stopped \
  --name roon-extension-alarm-clock \
  -v /storage/roon-extension-alarm-clock/config.json:/usr/src/app/config.json \
  -e TZ=Europe/Berlin \
  theappgineer/roon-extension-alarm-clock:latest</code></pre>
