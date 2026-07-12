# Custom Sound Engine

The **Custom Sound Engine** or CSE is a system created by Dantarion, Pyotr, and DukeItOut that allows playing songs from customizable [tracklist](music?id=tracklists) files instead of hardcoded song IDs. With this system, you can add custom BRSTM files anywhere in `pf/sound/strm` and create a tracklist file in `pf/sound/tracklist` to orchestrate which songs play on certain stages or certain screens.

This system also allows you to create netplay-specific tracklists in `pf/sound/netplaylist`, which will be used during netplay instead of the regular tracklists. This is especially useful to prevent desync, since changing a song's frequency in-game can update the tracklist file, but this will not happen to the netplay tracklists.

This system is included in most modern builds.

To learn more about how to use the Custom Sound Engine, see [Music](docs/music.md).

---

## Resources

#### Custom Sound Engine Guides

- [Project+ music modding guide](https://docs.google.com/document/d/1AC4isXShcu9ufUwM5H34dR2orLmsW0xCZXz_lubhixY/edit?tab=t.0) by mawwwk - A guide on adding music to Project+, which is accurate to any builds using the CSE.