# Soundbanks

Sound effects in Brawl live in **soundbanks**, files that group related sound effects together and are individually loaded when the game needs them. When a soundbank is loaded, any entity in the game can call on a sound effect contained within that soundbank.

## BRSAR

In the vanilla game, all soundbanks are contained within a large **BRSAR** file called `smashbros_sound.brsar` and located in the `sound` folder at the root of the disk. This file contains the various banks as well as headers for them. When modifying the vanilla game, you need to open this BRSAR file using Super Sawndz, and from there you can modify the sounds within, replacing them with your own sounds.

If you don't have the BRSAR, you can get it by [extracting Brawl's files](extracting-brawl-files.md) from the disk.