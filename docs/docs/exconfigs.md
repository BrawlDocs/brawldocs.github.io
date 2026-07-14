# EX Configs

!> This section is only applicable if you're using a BrawlEx build

**EX Configs** are configuration files used by [BrawlEx](/mods/brawlex.md) to map fighters to IDs and properties so the game knows which characters to load and what to do with them. Every fighter, in theory, should have 4 configs - each of a different type - although some of the values of these configs are hardcoded into BrawlEx, so vanilla fighters can sometimes be missing some and still function correctly. When adding a new fighter, you'll need to make sure they have these configs as well.

There are 4 types of configs:
- FighterConfig
- CosmeticConfig
- SlotConfig
- CSSSlotConfig

Each of these configs has their own ID associated. Most EX fighters use one ID, which is shared across all of their configs, but some fighters use different IDs for each config.

Configs are usually located in `pf/BrawlEx` in a subfolder matching the cosmetic type listed above. However, in some newer builds they are located in an `ExConfigs.pac` at the same location, within an ARC node with a name matching the cosmetic type listed above.

## CosmeticConfig

<img src="images/CosmeticConfig.png" alt="Cosmetic config screenshot" width="700"/>

The **CosmeticConfig** sets up various cosmetic components of the fighter, including the the character's display name on various screens, their [cosmetic ID](cosmetics?id=conventions), franchise icon ID, and announcer call ID.

CosmeticConfigs are stored in `pf/BrawlEx/CosmeticConfig` and are named `CosmeticXX.dat`, where `XX` is the cosmetic config ID of the fighter. In some builds it is stored in `pf/BrawlEx/ExConfigs.pac` under the `CosmeticConfig` ARC node, with a `FileIndex` equal to the cosmetic config ID.

#### Cosmetic Config Fields

- **CharacterName** - The name of the character that is displayed in-game on screens like the results screen.
- **Set Primary/Secondary** - If set to true, when this fighter is loaded, the game will load the SlotConfig with an ID matching the **Primary Character Slot** field instead of loading the SlotConfig with an ID matching the CosmeticConfig.
- **Primary Character Slot** - The ID of the SlotConfig to load if the **Set Primary/Secondary** field is true.
- **Secondary Character Slot** - Should always be `0xFF`.
- **Cosmetic ID** - [The ID used to find the fighter's cosmetics](cosmetics?id=cosmetic-id). Can be anything, as long as it is not in use.
- **Franchise Icon** - The ID used to find the fighter's franchise icon, another type of fighter cosmetic. The value entered here is actually 1 less than the ID used in franchise icon texture names. For example, Mario's franchise icon is `0x00`, but the ID used in the texture name for the Super Mario franchise icon is `1`.
- **Announcer Call** - The [info index](soundbanks?id=sfx-info) of the SFX to play when the character is selected on the CSS.

## CSSSlotConfig

<img src="images/CSSSlot.png" alt="CSSSlot config screenshot" width="700"/>

The **CSSSlotConfig** sets up Wiimote SFX and the costumes associated with the fighter.

CSSSlotConfigs are stored in `pf/BrawlEx/CSSSlotConfig` and are named `CSSSlotXX.dat`, where `XX` is the CSS slot config ID of the fighter. In some builds it is stored in `pf/BrawlEx/ExConfigs.pac` under the `CSSSlotConfig` ARC node, with a `FileIndex` equal to the CSS slot config ID.

#### CSSSlot Config Fields

- **Set Primary/Secondary** - If set to true, when this fighter is loaded, the game will load the SlotConfig with an ID matching the **Primary Character Slot** field instead of loading the SlotConfig with an ID matching the CSSSlotConfig.
- **Primary Character Slot** - The ID of the SlotConfig to load if the **Set Primary/Secondary** field is true.
- **Secondary Character Slot** - Should always be `0xFF`.
- **Record Bank** - The ID of the record bank to use when saving record data for the character. For example, if set to Mario's (`0x00`), the characters record KOs will be stored as Mario's KOs on the records screen.
- **Set Cosmetic Slot** - If set to true, when this fighter is loaded, the game will load the CosmeticConfig with an ID matching the **Cosmetic Slot** field instead of loading the CosmeticConfig with an ID matching the CSSSlotConfig.
- **Cosmetic Slot** - The ID of the CosmeticConfig to load if the **Set Cosmetic Slot** field is true.
- **Wiimote SFX** - The [info index](soundbanks?id=sfx-info) of the SFX to play from the Wiimote when the character is selected on CSS.

### Costumes

<img src="images/CSSSlotCostume.png" alt="Screenshot of a costume node in a CSSSlot config" width="700"/>

In addition to the fields on the root node, the CSSSlotConfig contains a list of all of the costumes available to the fighter. This is how the game knows what files to use for each of the fighter's costumes.

Every costume is a child node of the root. To add a new costume entry, right-click the root node and select **Add New Entry**. Costumes have the following properties:

- **Costume ID** - The ID associated with the PAC file to load for the costume. For example, if configuring Mario with a costume ID of 6, this costume would load `FitMario06.pac`.
- **Color** - The color associated with the costume. These colors are displayed on certain screens like tournament mode. Some of these colors are team colors and thus used to determine if the costume is available in team battles.

## FighterConfig

<img src="images/FighterConfig.png" alt="Screenshot of a fighter config" width="700"/>

The **FighterConfig** sets up many details of the fighter, most importantly which files are loaded for that fighter.

FighterConfigs are stored in `pf/BrawlEx/FighterConfig` and are named `FighterXX.dat`, where `XX` is the fighter config ID of the fighter. In some builds it is stored in `pf/BrawlEx/ExConfigs.pac` under the `FighterConfig` ARC node, with a `FileIndex` equal to the fighter config ID.

#### Fighter Config Fields

**Fighter**
- **Fighter File Name** - The base name to use for all of the [fighter's files](fighter-files.md) and their [module](fighter-modules.md). Changing this field updates all of the other fields in the same section of the config in BrawlCrate.
- **Pac File Name** - The relative path and naming scheme used for the PAC files associated with the fighter, relative to `pf/fighter` in most builds. For example, setting this path to `mario/FitMario.pac` means that the fighter's moveset PAC will be `pf/fighter/mario/FitMario.pac`. All other PAC files, such as costumes, Entry, Motion, Etc, and the like will be derived from this filename.
- **Kirby Pac File Name** - Similar to the **Pac File Name**, this is the relative path and naming scheme used for the PAC files associated with the fighter's Kirby hat. For example, setting it to `kirby/FitKirbyMario.pac` means that the fighter's Kirby hat PAC will be `pf/fighter/kirby/FitKirbyMario.pac`. All other Kirby hat PAC files, such as costumes, will be derived from this filename. Usually, this is `kirby/FitKirbyFightername.pac`, where `Fightername` is the same as the **Fighter File Name**.
- **Module File Name** - The name of the rel file to use for the fighter's [module](fighter-modules.md). Usually `ft_fightername.rel`, where `fightername` is the **Fighter File Name**. For example, `ft_mario.rel` would load `pf/module/ft_mario.rel`.
- **Internal Fighter Name** - An internal name for the fighter. Usually the same as the **Fighter File Name**, but in all caps.
**Abilities**
- **Can Crawl** - Specifies whether the fighter can crawl.
- **Forward Tilt Count** - Specifies how many forward tilts the fighter has.
- **Can Glide** - Specifies whether the fighter can glide.
- **Can Wall Cling** - Specifies whether the fighter can cling to walls.
- **Can Wall Jump** - Specifies whether the fighter can wall jump.
- **Can Z-Air** - Specifies whether the fighter can execute an aerial tether using Z.
**Characteristics**
- **Air Jump Count** - Specifies the number of mid-air jumps for the fighter.
- **Dash Attack Into Crouch** - Specifies whether the fighter will enter the crouch position after a dash attack.
- **Forward Smash Count** - Specifies how many times the fighter can chain their forward smash.
- **Has Rapid Jab** - Specifies whether the fighter will use a rapid jab at the end of their combo.
- **Jab Count** - Specifies the number of hits for the fighter's jab combo.
- **Jab Flag** - Unknown.
**Costumes**

This section is used to specify how many costumes your character has, but in modern builds this is mostly controlled via the CSSSlotConfig anyway. If your character has more than 12 costumes, set all of these parameters to true.

**Resources**
- **Has Pac** - Whether or not the fighter has a .pac file. Normally only set to false for unused characters.
- **Has Module** - Whether or not the fighter has a module file. Normally only set to false for unused characters.
- **MotionEtc Type** - Value determines how the fighter's [MotionEtc](fighter-files?id=motionetc-files) files are loaded.
    - **SingleSeparate** - A single Motion and a single Etc file will be used regardless of the costume loaded for the fighter. For example, for Mario, this would mean he has a single `FitMarioMotion.pac` and `FitMarioEtc.pac`.
    - **SingleMerged** - A single MotionEtc file will be used regardless of the costume loaded for the fighter. For example, for Mario, this would mean he has a single `FitMarioMotionEtc.pac`.
    - **PerCostumeSeparate** - A single Motion file will be used regardless of the costume loaded for the fighter, but each costume will have it's own Etc file. For example, for Mario, this would mean he has a single `FitMarioMotion.pac`, but each costume will have it's own Etc, like `FitMarioEtc00.pac`.
    - **PerCostumeSet** - A single Motion file will be used regardless of the costume loaded for the fighter, but each costume *set* will use it's own `Etc` file. Costume set ranges start at costume IDs `00 - 19`, and then proceed in intervals of ten (`20 - 29`, `30 - 39`, etc). For example, for Mario, this would mean he has a single `FitMarioMotion.pac`, but costumes `00 - 19` would all share `FitMarioEtc00.pac`.
    - **Unknown Load Flag A** - Unknown.
    - **Unknown Load Flag B** - Unknown.
- **Entry Load Type** - Value determines how the fighter's [Entry](fighter-files?id=entry-files) files are loaded.
    - **None** - No FitEntry file will be loaded.
    - **Single** - A single FitEntry file will load regardless of costume. For example, Mario would load `FitMarioEntry.pac`.
    - **PerColor** - A separate FitEntry file will load for each costume. For example, Mario's costume `00` would load `FitMarioEntry00.pac`.
- **Results Load Type** - Value determines how the fighter's [Result](fighter-files?id=result-files) files are loaded.
    - **None** - No FitResult file will be loaded.
    - **Single** - A single FitResult file will load regardless of costume. For example, Mario would load `FitMarioResult.pac`.
    - **PerColor** - A separate FitResult file will load for each costume. For example, Mario's costume `00` would load `FitMarioResult00.pac`.
- **Kirby Hat Load Type** - Value determines how the fighter's [Kirby hat](fighter-files?id=kirby-hat-files) files are loaded.
    - **None** - No Kirby hat PAC file will be loaded.
    - **Single** - A single Kirby hat PAC file will load regardless of costume. For example, Mario would load `FitKirbyMario.pac`.
    - **PerColor** - A separate Kirby hat PAC file will load for each of *Kirby's* costumes. For example, Kirby's `00` costume, when facing Mario, would load `FitKirbyMario00.pac`. Used for characters like DK and Falco, whose hats change Kirby's whole body.
- **Final Load Type** - Value determines how the fighter's [Final](fighter-files?id=final-files) files are loaded.
    - **None** - No FitFinal file will be loaded.
    - **Single** - A single FitFinal file will load regardless of costume. For example, Mario would load `FitMarioFinal.pac`.
    - **PerColor** - A separate FitFinal file will load for each costume. For example, Mario's costume `00` would load `FitMarioFinal00.pac`.
    - **UseFitFoxFinal** - `FitFoxFinal.pac` will always be loaded instead of the fighter's own PAC. Used by Falco.

**Sound**
- **Final Smash Music Flag** - Normally set to false for characters whose Final Smash is accompanied by music.
- **Sound Bank** - The [info index](soundbanks?id=sawnd-naming) of the soundbank to load for the fighter.
- **Kirby Sound Bank** - The [info index](soundbanks?id=sawnd-naming) of the soundbank to load for the fighter's Kirby hat.

**Fighter Config**
- **Version** - The version of BrawlEx the config was made under. Only 1 and 2 are valid versions.

**Misc**
- **AI Controller** - Which character's AI for CPUs to use in-game.
- **Entry Flag** - Unknown.
- **Ik Physics Flag** - Normally set to true for Ice Climbers and Olimar.
- **Texture Loader** - Specifies what texture loader to use when loading the fighter's entry articles.
- **Thrown Type** - Sets the specific animation set to be used when the character is thrown. These values are `Default`, `Small`, `Big`, and `Girl`.
- **Grab Size** - Used to change the animation when this character and victims are held in a grab. Values are `Tall` and `Short`.
- **Work Manage Flag** - Normally set to False for Mario, Luigi, Popo, Nana, and Pit.

## SlotConfig

<img src="images/SlotConfig.png" alt="Screenshot of a slot config" width="700"/>

The **SlotConfig** is used mainly to set up the character's victory theme and announcer call.

SlotConfigs are stored in `pf/BrawlEx/SlotConfig` and are named `SlotXX.dat`, where `XX` is the slot config ID of the fighter. In some builds it is stored in `pf/BrawlEx/ExConfigs.pac` under the `SlotConfig` ARC node, with a `FileIndex` equal to the slot config ID.

#### Slot Config Fields
- **Set Slot Characters** - If set to true, when this fighter is loaded, the game will load the FighterConfig with an ID matching the **Character Slot 1** field instead of loading the FighterConfig with an ID matching the SlotConfig.
- **Character Slot 1** - The ID of the FighterConfig to load if **Set Slot Characters** is true.
- **Character Slot 2** - Leave as `0xFFFFFFFF`.
- **Character Slot 3** - Leave as `0xFFFFFFFF`.
- **Character Slot 4** - Leave as `0xFFFFFFFF`.
- **Record Bank** - The ID of the record bank to use when saving record data for the character. For example, if set to Mario's (`0x00`), the characters record KOs will be stored as Mario's KOs on the records screen.
- **Victory Theme** - The [song ID](music?id=songid) to use for your fighter's victory theme which plays on the results screen.
- **Announcer Call** - The [info index](soundbanks?id=sfx-info) of the SFX to play to announce the character's name in some modes.
- **Camera Distance 1 - 4** - These parameters adjust the camera position on the results screen when the character wins.

## Roster File

In order for your character to actually display on the CSS, you also need to modify a roster file that controls who displays. In most builds, this is located in `pf/BrawlEx` and is named something like `CSSRoster.dat` or `css.bx`.

<img src="images/CSSRosterExample.png" alt="Example of a roster file" width="700"/>

The roster file usually contains two folders in it - **Character Select** and **Random Character Select**. The former controls which characters actually appear on the CSS, while the latter controls which characters are available when you select random. If you want a character available in either roster, you simply need to right-click the respective folder and select "Add New Entry". Then, highlight the new entry and change it's "CSS Slot ID" to match the fighter you are trying to add.

---

## Resources

#### EX Config Guides

- [BrawlEx Guide for P+Ex](https://docs.google.com/document/d/1ZoL_qDcwUpUXg82cKaUp-6D_AcfpFctoW6GXFY74_0k/edit?usp=sharing) by KingJigglypuff, originally by Robintjuh - A general-purpose guide for installing BrawlEx characters to P+Ex builds, but goes into great detail about configuring EX configs and the roster.
- [Internal ID References](https://docs.google.com/document/d/1mQaRwM4dh9g1owel6_ZFNSVwmllbO1pcC7IaYtmJBzM/edit?usp=sharing) by KingJigglypuff - A list of all fighter IDs in Brawl, Project+, and P+Ex. Useful for knowing which configs are used by which fighters.

#### EX Config Resources

- [P+Ex Config Templates](https://drive.google.com/file/d/19rv-2aUKViQu9autyLLmJA-JLQ-hPgII/view?usp=sharing) - EX configs for the entire P+Ex cast which can be copied and edited to use as a base for new characters.
- [BrawlEx Clone Engine v2.0.0.0](https://www.dropbox.com/scl/fi/cfhky1qei05tgh2i9h9e4/BrawlEx-Clone-Engine-v2.0.0.0.zip?rlkey=19j941xh8voem46x712q5vaoh&e=1&dl=0) - The original BrawlEx archive, containing vBrawl EX configs for the vanilla cast.
- [ProjectM + BrawlEx Resources](https://www.mediafire.com/file/5funzwc4prer6fe/ProjectM%252BBrawlEx_Resources.zip/file) - An archive of the EX configs and EX modules for Project M + BrawlEx.