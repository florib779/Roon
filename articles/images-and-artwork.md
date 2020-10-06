# Images and Artwork in Roon

In Roon, all the images embedded in the file tags, are stored next to the audio files or stored in a folder called `artwork` or `scans` next to the files are displayed. This includes all images that include `cover`, `front` or `folder`.

Related to [this post](https://community.roonlabs.com/t/has-liner-notes/55822/7) images will be showed in the following order on the album page:

* folder `scans` or `artwork`
  * `cover.jpg` or `front.jpg` or `folder.jpg`
    * `back.jpg`
      1. `booklet1.jpg` or `liner1.jpg`
      2. `booklet2.jpg` or `liner2.jpg`

## Artists, Composers

Setpoints of the images to take advantage of the full width of the display:


* resolution examples
  * 1900 x 1000 or larger in the same aspect ratio
  * 1728 x 1080
  * 1600 x 1000
  * 1280 x 720
* [at least 960px and aspect ratio greater than 1.55](https://community.roonlabs.com/t/artist-images-size-and-scale-and-cropping-is-unpredictable/10018/7)

## Sources for images

* Cover
  * [Coveralia](https://www.coveralia.com/)
  * [Discogs](https://www.discogs.com/)
  * [Fanart.tv](https://fanart.tv/)
    * Front-Cover, CD
    * There is a [Plugin for MusicBrainz Picard]() available. To use this an API key for Fanart.tv must be entered.
* Band/Artist-Fotos
  * [Fanart.tv](https://fanart.tv/)
  * [Wikipedia](https://wikipedia.org/)
  
## Clear TIDAL Image Cache

1. Quit Roon (or RoonServer)
2. Find and open your [Roon or RoonServer folder](https://kb.roonlabs.com/Database_Location)
3. Locate and delete only the cache folder (Roon/Cache)
4. Restart Roon
