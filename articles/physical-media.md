# Physical Media

## CDs/DVDs

### Ripping

* [Roon OS CDROM](https://kb.roonlabs.com/Roon_OS_CDROM) (only CDs can be ripped)
* [roon-extension-cd-ripper](https://github.com/TheAppgineer/roon-extension-cd-ripper)
* [Exact Audio Copy](http://www.exactaudiocopy.de/) (works also with [wine](https://www.winehq.org/))
* [Morituri](https://github.com/thomasvs/morituri)
  * `rip offset find`
  * `rip cd rip --offset=6 --output-directory="/home/user/flac/" --track-template="%t %n" --disc-template="%A - %d" --working-directory="/tmp/"`
* [DVD Audio Extractor](https://www.dvdae.com/) (commercial)
* [How to Rip a DTS "5.1 Music Disc" to FLAC and keep the surround sound](https://ubuntuforums.org/showthread.php?t=1849260)
  * `for file in *.wav; do name=$(echo $file | sed "s/\.wav//g"); dcadec -o wavall "$file" > "$name"_decoded.wav; ffmpeg -i "$name"_decoded.wav "$name".flac; rm -f "$file" "$name"_decoded.wav; done`
