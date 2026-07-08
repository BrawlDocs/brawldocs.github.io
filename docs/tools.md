# Tools

There are various tools involved in Brawl modding. This section will go over the most popular and useful tools.

## General-Purpose Modding Tools

### BrawlCrate

<img src="images/BrawlCrate.png" alt="BrawlCrate screenshot" width="700"/>

[BrawlCrate](https://github.com/soopercool101/BrawlCrate) is a Wii file editor specifically made for viewing and editing the file formats associated with Brawl. Most of the files in a build can be modified with BrawlCrate. This is one of the most essential tools to have if you intend to mod the game.

### BrawlInstaller

<img src="images/BrawlInstaller.png" alt="BrawlInstaller screenshot" width="700"/>

[BrawlInstaller](https://github.com/squidgy617/BrawlInstaller) is an all-in-one tool for managing Brawl mods. It allows you to manage fighters, costumes, stages, music, and trophies from a user-friendly interface, and has customizable settings to support most builds.

### VSDSync

<img src="images/VSDSync.png" alt="VSDSync screenshot" width="400"/>

[VSDSync](https://files.catbox.moe/449x3e.zip) is a program for syncing files from an external folder on your computer to a virtual SD card that can be read by Dolphin. Very useful for quick iteration when making lots of changes to a build. Also allows you to generate new virtual SD cards. See Meta's [quick start guide](https://docs.google.com/document/d/10keWiKXYbMt1euIHl99hPukUFDKauqr3Ondf_sW_jgc/edit?usp=sharing) for detailed instructions.

### ImDisk

<img src="images/ImDisk.png" alt="ImDisk screenshot" width="700"/>

[ImDisk](https://sourceforge.net/projects/imdisk-toolkit/) is a program which allows you to mount a virtual SD card as a drive on your computer and modify its contents directly. Good for quick, small edits, though more cumbersome than VSDSync when making larger changes. See extreme's [guide](https://docs.google.com/document/d/1CitPCBgUl5jcqhT9TmwGE0C7FiM3aS_eo2eqVm97mI0/edit?usp=sharing) for detailed instructions.

## Fighter Editing

### PSACompressor

<img src="images/PSACompressor.png" alt="PSACompressor screenshot" width="700"/>

[PSACompressor](https://uu.getuploader.com/iclpxnohokanko1/download/184) is a program that allows you to edit fighter movesets by writing pseudo-coded "command" logic. It is the main tool used for creating and editing movesets.

### BrawlItemEditor

<img src="images/BrawlItemEditor.png" alt="BrawlItemEditor screenshot" width="700"/>

[BrawlItemEditor](https://uu.getuploader.com/iclpxnohokanko1/download/151) is a program that allows you to edit the logic of items and enemies using the same pseudo-coded "command" logic that PSACompressor uses. It is the main tool for editing items and enemies.

### PSA Conversion Tools

[PSA Conversion Tools](https://github.com/TheGag96/pm-hax/tree/master/PSA%20Conversion%20Tools) that allow you to perform various actions on fighter moveset files, such as converting their logic to Gecko codes or mass-updating GFX and SFX IDs within a moveset.

### lavaKirbyHatManagerV2

<img src="images/lavaKirbyHatManager.png" alt="lavaKirbyHatManager screenshot" width="700"/>

[lavaKirbyHatManagerV2](https://github.com/QuickLava/lavaKirbyHatManagerV2) is a tool for modifying, adding, and removing Kirby hat data within a build. Essential for creating custom Kirby hats. Kirby hat data generated with this program is compatible with BrawlInstaller.

## Sounds and Music

### Super Sawndz

<img src="images/SuperSawndz.png" alt="Super Sawndz screenshot" width="700"/>

[Super Sawndz](https://github.com/QuickLava/super-sawndz) is an editor for Brawl's sound files, allowing you to open a Brawl BRSAR file, import `.sawnd` files into it, modify the sounds within, and export them. It is essential if you want to make any changes to the game's sound effects.

### LoopingAudioConverter

<img src="images/LoopingAudioConverter.png" alt="LoopingAudioConverter screenshot" width="700"/>

[LoopingAudioConverter](https://github.com/libertyernie/LoopingAudioConverter) is a tool for converting creating loop points in songs (supporting various file formats) and saving them in the `brstm` format used for music in Brawl.

### Loopatron

<img src="images/Loopatron.png" alt="Loopatron screenshot" width="700"/>

[Loopatron](https://github.com/ilazoja/Loopatron) is a tool for identifying and creating loop points in songs (supporting various file formats) and saving them in the `brstm` format used for music in Brawl. It is backed by LoopingAudioConverter.

## Graphics

### Blender

<img src="images/Blender.png" alt="Blender screenshot" width="700"/>

[Blender](https://www.blender.org/) is free, open-source 3D modeling and animation software used industry-wide. It is a very versatile program, and is also one of the primary tools used for modeling and animating in Brawl modding.

### GIMP

<img src="images/GIMP.png" alt="GIMP screenshot" width="700"/>

[GIMP](https://www.gimp.org/) is a free, open-source image editing software. It is a general-purpose image editor, but is used frequently in Brawl modding, especially for creating character cosmetics. If you're specifically interested in using it for that purpose, you should make sure to get the version of the program included in [CSProject 2.5](https://www.mediafire.com/file/arhkjuufx17jez0/CSProject_2.5.zip/file), which includes custom plugins specifically to make creating fighter UI assets for Brawl.

### Photopea

<img src="images/Photopea.png" alt="Photopea screenshot" width="700"/>

[Photopea](https://www.photopea.com/) is a free browser-based image editing software. Similar to GIMP, but some may find it easier to use. Like GIMP, it is general-purpose, but frequently used in modding Brawl.

### Project M Cosmetics Generator

<img src="images/PMCosmeticsGenerator.png" alt="Project M Cosmetics Generator screenshot" width="700"/>

[Project M Cosmetics Generator](https://github.com/gerarreal/Project-M-Cosmetics-Generator) is a tool for automatically generating UI elements for the names that display in various places in Brawl. It can generate name images in the style of both vanilla Brawl and Project M.

## Coding

### GCTRealMate

[GCTRealMate](https://github.com/CodecSMW/GCTRealMate) is a tool for compiling ASM code into a Gecko format that can be easily used to patch the game with code changes. This tool is already included in most builds.

### reltools

[reltools](https://github.com/Sammi-Husky/reltools) is a tool for disassembling and re-assembling `.rel` files that hold a great deal of Brawl's code. Allows you to edit these files in ASM.

### Ghidra

<img src="images/Ghidra.png" alt="Ghidra screenshot" width="700"/>

[Ghidra](https://github.com/NationalSecurityAgency/ghidra) is a reverse-engineering tool that allows you to connect to a community-hosted server where you can view Brawl's code in a decompiled, pseudo-C++ format for added readability. Extremely useful for understanding the game's code. To use it for Brawl modding, you'll also need the [Ghidra GameCube Loader](https://github.com/Cuyler36/Ghidra-GameCube-Loader).

### Dolphin Memory Engine

<img src="images/DME.png" alt="Dolphin Memory Engine screenshot" width="700"/>

[Dolphin Memory Engine](https://github.com/aldelaro5/dolphin-memory-engine) is a RAM search program that allows you to search, track, and edit the memory of a game running in Dolphin during runtime. Very useful for tracking and testing memory changes when trying to understand the game's code.