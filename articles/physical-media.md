# Physical Media
<h2>CDs/DVDs</h2>
<h3>Ripping</h3>
<ul>
<li><a href="https://github.com/TheAppgineer/roon-extension-cd-ripper">roon-extension-cd-ripper</a></li>
<li><a href="https://kb.roonlabs.com/Roon_OS_CDROM">Roon OS CDROM</a></li>
<li><a href="http://www.exactaudiocopy.de/">Exact Audio Copy</a> (works also with <a href="https://www.winehq.org/">wine</a>)</li>
<li><a href="https://github.com/thomasvs/morituri">Morituri</a><br>
<ul>
<li><code>rip offset find</code></li>
<li><code>rip cd rip --offset=6 --output-directory="/home/user/flac/" --track-template="%t %n" --disc-template="%A - %d" --working-directory="/tmp/"</code></li>
</ul>
</li>
<li><a href="https://www.dvdae.com/">DVD Audio Extractor</a> (commercial)</li>
<li><a href="https://ubuntuforums.org/showthread.php?t=1849260">How to Rip a DTS "5.1 Music Disc" to FLAC and keep the surround sound</a>
<ul>
<li>
<pre>for file in *.wav; do name=$(echo $file | sed "s/\.wav//g"); dcadec -o wavall "$file" &gt; "$name"_decoded.wav; ffmpeg -i "$name"_decoded.wav "$name".flac; rm -f "$file" "$name"_decoded.wav; done</pre>
</li>
</ul>
</li>
</ul>
