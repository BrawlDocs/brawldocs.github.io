# Replacement Soundbank Engine

The **Replacement Soundbank Engine** or RSBE is a system that allows the game to load external **SAWND** files from `pf/sfx` instead of loading all sounds from a single **BRSAR** file in the `sound` folder. When a soundbank is loaded, the system first checks if a corresponding SAWND exists in `pf/sfx`, and if it is not found, the game will attempt to load the bank from the BRSAR instead.

Most modern builds implement this system.

To learn more about working with SAWNDs, see [Soundbanks](docs/soundbanks.md).