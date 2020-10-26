<p>Local Roon files have some special features over streamed content:</p>

<ul>
<li>You have a nice looking waveform.</li>
<li>The dynamic range of an album will be shown.</li>
<li>You can group tracks.</li>
<li>You can tag your tracks with <code>ROONRADIOBAN</code> (set to values 1 or true or yes), so the tracks will no longer be selected by Roon-Radio.</li>
<li>You can edit tracks.</li>
<li>When playing you are not dependent on a stable internet connection.</li>
</ul>
<h2>Tagging (meta data)</h2>
<p>Roon cleans up your music library and updates the metadata associated with your music.</p>
<p>Although Roon has a rich metadata database, it sometimes happens, especially for less popular albums, that they can not be identified. Here it is helpful to tag these to supplement the missing data.</p>
<p>Software for editing meta data:</p>
<ul>
<li><a href="https://picard.musicbrainz.org/">MusicBrainz Picard</a></li>
<li><a href="https://beets.io/">Beets</a></li>
</ul>
<p>See also <a href="https://kb.roonlabs.com/File_Tag_Best_Practice">File Tag Best Practice</a> for further information.</p>
<h2>Converting</h2>
<h3>5.1 flac to Stereo flac</h3>
<p><code>ffmpeg -i /audio/5.1-input.flac -ac 2 /audio/stereo.flac</code></p>
<h3>DTS wav to other lossless formats</h3>
<p>If necessary simply replace .wav with another file format: <code>for file in *.wav; do name=$(echo $file | sed "s/\\.wav//g"); ffmpeg -acodec dts -i "$name".wav -vn -sn -acodec flac "$name".flac; done</code></p>
<h2>Grouping tracks in Roon</h2>
<p>This procedure is currently a bit awkward. First, all pieces that are to be grouped must be tagged with an external (not within Roon) tag editor according to the following scheme:</p>
<ul>
<li><code>WORK</code>: The Dark Ages/Babylon</li>
<li><code>PART</code>: I. The Dark Ages</li>
<li><code>WORK</code>: The Dark Ages/Babylon</li>
<li><code>PART</code>: II. Babylon</li>
</ul>
<p>In some cases the album has to be edited in Roon:</p>
<p>Metadata Preferences → Multi-part Composition Group → Choose Prefer File</p>
<h2>Editing, Cutting of audio files</h2>
<p>Free software for editing audio files (for most plattforms):</p>
<ul>
<li><a href="https://www.audacity.de/">Audacity</a></li>
<li><a href="https://www.ocenaudio.com/">Ocenaudio</a></li>
</ul>
<h2>Links</h2>
<ul>
<li><a href="https://community.roonlabs.com/t/music-on-local-storage-versus-music-on-qobuz-tidal/78834">Music on local storage versus music on Qobuz/Tidal</a></li>
</ul>
