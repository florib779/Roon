# Roon Components

<p>By separating core and control and output components, you get the greatest possible freedom and flexibility.</p>

<p>The strict separation of the three following components has the advantage that the graphics-intensive control app runs with the user interface on another device and the central Roon computer is relieved of the complex graphics operations. This constellation brings clearly audible advantages over a full installation of Roon.</p>
<p>In general, it does not hurt if the device (core and bridge) is turned on around the clock. Of course, this assumes that you use an energy-efficient device as core and/or output. Since Roon Bridge requires very little CPU, there is little CPU activity (heat) and power consumption. On RaspberryPis it's also possible to limit the maximum processor performance. Shutting down a device, allowing all components to cool down (contraction), then rebooting and re-heating the components will probably do more harm than running it at a constant temperature.</p>
<h2>Roon Core/R.O.C.K.</h2>
<p><a href="https://community.roonlabs.com/t/what-are-the-differences-roon-endpoint-os-options-roon-server-vs-rock/26448">What are the differences (Roon Endpoint OS Options, Roon Server vs R.O.C.K.)?</a></p>
<h3>Fritz!Box</h3>
<ul>
<li>R.O.C.K. can be started by the Fritz!Box (WOL)
<ul>
<li>Network → Network Connections → Gerät bearbeiten (Pen) → Wake on LAN (at the bottom) → Start Computer</li>
</ul>
</li>
<li>If a hard drive is used as NAS storage, it can be put on some routers (for example Fritz! Box) in the energy saving mode.
<ul>
<li><a href="https://community.roonlabs.com/t/roon-core-idle-activity/30465/11">ROCK does not spin down drives as a choice. Spinning up and down drives decreases their longevity quite a bit, and in some circumstances can use more power.</a></li>
</ul>
</li>
<li>NAS-URLs for file managers
<ul>
<li><code>\\fritz.nas\FRITZ.NAS</code></li>
<li><code>smb://fritz.nas/FRITZ.NAS/</code></li>
</ul>
</li>
<li>Access via FTP from the computer.</li>
<li>Fritz!Box does not index automatically.</li>
<li>It may happen that FRITZ.NAS does not recognize albums, despite many attempts to scan / copy the albums again, etc.
<ul>
<li>To counter such limitations, it is best to connect the external storage directly to the core.</li>
</ul>
</li>
</ul>
<h3>External Storage</h3>
<p>ROCK: Storage Basics</p>
<ul>
<li>In the case of a drive failure easy to replace.</li>
<li>Easy to update at a later date.</li>
<li>External storage can be easily removed, for example, before updating (to make sure that the music files are not deleted). This should not be the case, but who know's?</li>
<li>External storage has a more favorable effect on the heat development within the housing than an internal hard drive.</li>
<li>R.O.C.K. also works with NTFS, FAT32 and ext2/3/4 drives, but if you're new to USB storage, Roon's recommendation is exFAT.
<ul>
<li>With FAT32 no "Watching for new files in real time" works -&gt; ext4 works.</li>
</ul>
</li>
</ul>
<h2>Possible Roon-Outputs</h2>
<ul>
<li>Always use Ethernet between core and output.
<ul>
<li>Roon offers comprehensive and robust support for WiFi, but the sound quality is often not the same. For your highest quality rooms, plan for wired Gigabit Ethernet connections between the core and the outputs.</li>
</ul>
</li>
<li><a href="https://www.audiostream.com/content/electrically-isolate-your-networked-audio">Electrically Isolate Your Networked Audio</a><br>
<ul>
<li>Therefore, do not state as a categorical fact that Ethernet cables do not make a difference: you can, but not to the degree that you envisioned, and longer cables could accommodate more RF. This does not mean that you have to spend a fortune to solve the problem - far from it - but well-made and double-shielded (shielded twisted-pair plus shielded sheath) Ethernet cables are worth considering.</li>
</ul>
</li>
</ul>
<h3>RaspberryPi</h3>
<ul>
<li><a href="https://community.roonlabs.com/t/raspberry-pi-384-khz-32-bit-playback/16529">Raspberry Pi 384 kHz/32 bit playback</a><br>
<ul>
<li>Hifiberry: Dedicated S/PDIF interface chip supports up to 192kHz/24bit resolution. While the hardware can output DTS/Dolby Digital, the software must be customized to support this.
<ul>
<li>192kHz playback in S/PDIF is not officially supported over TOSLink (due to bandwidth limitations of TOSLink). Although this could work in some cases. It also depends on your cable.</li>
</ul>
</li>
<li><a href="http://www.pi2design.com/502hta.html">Raspberry Pi Tube HAT - Pi 2 Design</a></li>
</ul>
</li>
</ul>
<h4>Linux-Distributions for Roon Bridge</h4>
<ul>
<li><a href="https://community.roonlabs.com/t/dietpi-creating-a-lean-and-mean-roon-bridge/13908/2">DietPi:</a> Creating a lean-and-mean Roon Bridge</li>
<li><a href="https://www.hifiberry.com/hifiberryos/">HiFiBerryOS:</a> Linux distribution optimized for audio playback.</li>
<li><a href="https://ropieee.org/">Ropieee:</a> A RoonBridge ready-to-go image for Raspberry Pi
<ul>
<li><a href="https://community.roonlabs.com/t/ropieee-beginners-guide/36844">RoPieee Beginner’s Guide (PDF)</a></li>
</ul>
</li>
</ul>
<h3>Amazon Echo</h3>
<ul>
<li>Playback of Roon via Bluetooth possible.</li>
<li>Echo 3-Band Equalizer.
<ul>
<li>Can be controlled by voice command too.</li>
</ul>
</li>
</ul>
