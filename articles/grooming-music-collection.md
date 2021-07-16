# My procedure of grooming my music collection

I would like to introduce my personal steps and considerations that I do before and after downloading music. This seems a bit complicated and of course much more time-consuming than other options, but has proven itself in the past for me.

Personally, I prefer [local music files](local-files.md) over streaming because it has some advantages for me within Roon.

The first step is to search and compare at my prefered [sources for downloadable audio files](sources-for-downloadable-audio-files.md) in the following aspects:

1. Highest Quality
   1. Sometimes it is better to wait a while before buying a newly released album. In some cases an album is offered in CD quality and later in a higher quality.
2. Lowest Price
3. Bonus Tracks
4. Remastered (is not always better than the original recording)

Now it's time for tagging the music files. It's not really necessary, because [Roon](https://roonlabs.com/r/n6HeIaGsYUKKh60AONYs5Q) (Referral Link) already has a very good detection mechanism. However, I made the experience that the manual tagging partly brings better results. There is also the possibility to add an album that is not yet in the Musicbrainz database, so that it can be identified by Roon. Of course there is also the possibility to automate the tagging with a software like [Beets](http://beets.io/), but I do not know if this gives someone the possibility to add an album to the [MusicBrainz](https://musicbrainz.org/) database. In addition, I think it's better if a person has spotted the data for an album.

Actually I am in the process of creating a [configuration file for Beets](https://github.com/florib779/beets-config) to simplify and automate the process before importing into Roon.

I will probably continue to use [MusicBrainz Picard](https://picard.musicbrainz.org/) and [Songkong](http://www.jthink.net/songkong) for the time being to write additional information into the file tags that Beets can't currently provide, but we'll see.

For this reason, the information below is out of date at the moment.

### 1. Open MusicBrainz Picard and "Add Folder" with the album you wish to identify.
### 2. Select the album.

![](../images/musicbrainz_picard-add_folder.png)

As you can see on the green hooks, this album is already identified, all file meta tags match the MusicBrainz database and it has an album cover.

![](../images/musicbrainz_picard-album_identified.png)

If the album can't be found in the MusicBrainz database it's time to add it.

After adding an album you have to wait one minute or maybe a bit longer and then refresh. Now the album should be identified.

### 3. If already identified you can choose the album version, in case you are not happy with the result.

![](../images/musicbrainz_picard-choose_version.png)

### 4. Add the album to a collection

![](../images/musicbrainz_picard-add_to_collection.png)

### 5. Calculate album gain

![](../images/musicbrainz_picard-calculate_album_gain.png)

During calculation, which can take some time, I search for [additional images and artwork](images-and-artwork.md). Most download providers offer at least the front cover. Because that does not satisfy me, I try to get more pictures and possibly pictures in a better quality. Sometimes you even get a booklet in the form of a PDF file.

### 6. Save

## Links

* [Adding albums to MusicBrainz the “relatively” easy way](https://community.roonlabs.com/t/adding-albums-to-musicbrainz-the-relatively-easy-way/90529)
