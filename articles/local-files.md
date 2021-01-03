# Local Files

Local Roon files have some special features over streamed content:

* You have a nice looking waveform.
* The dynamic range of an album will be shown.
* You can add [lyrics](roon-lyrics.md).
* You can group tracks.
* You can tag your tracks with `ROONRADIOBAN` (set to values 1 or true or yes), so the tracks will no longer be selected by Roon-Radio.
* You can edit tracks.
* When playing you are not dependent on a stable internet connection.

## Tagging (meta data)
Roon cleans up your music library and updates the metadata associated with your music.

Although Roon has a rich metadata database, it sometimes happens, especially for less popular albums, that they can not be identified. Here it is helpful to tag these to supplement the missing data.

### Software for editing meta data:

* [MusicBrainz Picard](https://picard.musicbrainz.org/)
* [Beets](https://beets.io/)

See also <a href="https://kb.roonlabs.com/File_Tag_Best_Practice">File Tag Best Practice</a> for further information.

## Converting files

### 5.1 flac to Stereo flac

`ffmpeg -i /audio/5.1-input.flac -ac 2 /audio/stereo.flac`

### DTS wav to other lossless formats

If necessary simply replace .wav with another file format: `for file in *.wav; do name=$(echo $file | sed "s/\\.wav//g"); ffmpeg -acodec dts -i "$name".wav -vn -sn -acodec flac "$name".flac; done`

## Grouping tracks in Roon

This procedure is currently a bit awkward. First, all pieces that are to be grouped must be tagged with an external (not within Roon) tag editor according to the following scheme:

* `WORK`: The Dark Ages/Babylon
* `PART`: I. The Dark Ages
* `WORK`: The Dark Ages/Babylon
* `PART`: II. Babylon

In some cases the album has to be edited in Roon:

Metadata Preferences → Multi-part Composition Group → Choose Prefer File

## Editing, Cutting of audio files

Free software for editing audio files (for most plattforms):

* <a href="https://www.audacity.de/">Audacity</a>
* <a href="https://www.ocenaudio.com/">Ocenaudio</a>
  
## Links

* [Streaming vs ripping](https://community.roonlabs.com/t/streaming-vs-ripping/128331)
* [Music on local storage versus music on Qobuz/Tidal](https://community.roonlabs.com/t/music-on-local-storage-versus-music-on-qobuz-tidal/78834)
