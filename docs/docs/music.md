# Music

In Brawl, music files are stored in a **BRSTM** format. Vanilla Brawl stores these in `sound/strm`. In vanilla Brawl, the only way to change music is to replace these files.

## BRSTM Files

BRSTM is the format used by Brawl for music tracks. Music inside a BRSTM file can have defined loop points, allowing the songs to loop seamlessly.

You can create BRSTM files using a number of different programs, including [LoopingAudioConverter](/intro/tools?id=loopingaudioconverter) and [Loopatron](/intro/tools?id=loopatron).

## Tracklists

!> Tracklists are only available in builds that use the Custom Sound Engine (CSE)

Most modern builds use the [Custom Sound Engine (CSE)](/mods/custom-sound-engine.md), allowing you to extensively modify the songs that appear in-game. Songs are controlled mostly via **tracklists**, which are essentially files that hold a list of what BRSTMs can play when that tracklist is loaded.

Tracklists are usually located in `pf/sound/tracklist`, and end with the `.tlst` extension. They can be opened in BrawlCrate.

<img src="images/TracklistExample.png" alt="An example of a tracklist open in BrawlCrate" width="700"/>

Tracklists are loaded when the game calls for them. Many tracklists are tied to a stage (via the stage's [param](stage-slots?id=param-files)), meaning that the songs featured in the tracklist can play when that stage is loaded. Some tracklists are tied to specific screens, like the main menu or results.

To add a new song to a tracklist, you can simply right-click the root node of the tracklist and select **Add New Entry**. This will add a new entry which you can modify to point to a song of your choosing.

### Tracklist Entries

When you select an entry in a tracklist, you can edit a few properties on the right side. Below are the properties of a tracklist entry.

#### SongID

The **song ID** is the ID that the game's code uses to locate the song and play it. In vanilla Brawl, each song has an ID hardcoded to load a specific BRSTM file. For example, the Brawl main theme has a song ID of `0x26F9`, and the BRSTM file for that song is `X01.brstm`, so if you enter `0x26F9` as your song ID, `X01.brstm` will play when that song is picked.

However, you are not limited to the IDs used by the vanilla game. You can instead opt to use a **custom song ID**. Custom song IDs start at ID `0xF000`. Any ID above this will use custom song behavior. Custom song IDs will load a BRSTM you specify in the **SongFileName** field instead of loading a hardcoded BRSTM.

Multiple songs in one tracklist shouldn't share an ID. When you add a new entry, it will automatically use a custom ID that is unused anywhere else in the tracklist.

?> As an additional note, custom fighter victory and credits themes usually use a custom ID starting at `0xFF00` instead.

#### SongDelay

The number of frames to wait before the song starts playing on match start. -1 forces the song to not play until the end of the match start countdown.

#### Volume

The in-game volume to use for the song. Defaults to 80, can range from 0 to 127. Tracks typically have values between 50 and 90. Vanilla Brawl songs will ignore this setting.

#### Frequency

The frequency at which the song will be selected when a song is randomly selected from the tracklist, such as when playing a match. Defaults to 40, can range from 0 to 100, where higher means the song is more likely to play. Changing the song frequency in My Music will change this value in the tracklist if you have SD card writes enabled.

#### SongFileName

The song BRSTM file you want to play for custom tracks. The path entered here is relative to the `strm` folder in the build (usually `pf/sound/strm`). You can include folder names with a `/`. You should leave off the `.brstm` extension in this path.

For example, if I have a BRSTM file in `pf/sound/strm/Mario` named `Rogueport.brstm`, and I wanted this song to play in my tracklist, I would set the SongFileName to `Mario/Rogueport.brstm`.

If you're using a vanilla song ID, you can leave this field blank, as the BRSTM will be located automatically.

#### SongSwitch

This field allows you to configure **pinch mode** for your track. Pinch mode allows tracks to be switched mid-game if any of the following conditions are met:

1) The time specified in SongSwitch is reached
2) Two characters remain, and one is on their last stock (and below 100HP, if in Stamina mode)
3) Playing a Special Versus match in Wild mode, 300% mode, or Bomb Rain mode
4) Sudden Death occurs

If SongSwitch is set to 0, pinch mode will not occur. If it is set to anything else, pinch mode will occur if one of the above conditions is met.

To add a pinch mode track,
1. Set a desired value for SongSwitch (in frames, e.g. 1800 = 30 secs, 3600 = 1 minute)
2. Rename the pinch track to the base brstm followed by _b, (e.g. `Overworld [SMB].brstm` and `Overworld [SMB]_b.brstm`)

#### DisableStockPinch

If true, disables condition (2) for pinch mode listed above., meaning pinch mode does not trigger if a player is on their last stock.

#### HiddenFromTracklist

This setting is currently unused.

---

## Resources

#### Music Resources

- [Song ID List](data/song-ids.md) - A list of all vanilla Brawl song IDs.
- [Smash Custom Music](https://smashcustommusic.net/) - A site that hosts custom-made BRSTM files for Brawl.

#### Music Guides

- [Project+ music modding guide](https://docs.google.com/document/d/1AC4isXShcu9ufUwM5H34dR2orLmsW0xCZXz_lubhixY/edit?tab=t.0) by mawwwk - A guide on adding music to Project+, which is accurate to any builds using the CSE