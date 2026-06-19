# Stages

This section explains how stage modding works in Brawl.

---

## Stage Slots

Every stage exists within a stage **slot**. If you're using vanilla Brawl, these stage slots and their IDs are hardcoded for each stage. If you're using a custom build with the Stage Expansion system, these slots are determined either by an ASM table or a custom `RSS` file.

Stage slots are essentially made up of a couple of IDs.

#### Stage ID

The main ID of the stage. This is how the stage is referenced everywhere else.

#### Cosmetic ID

This ID is used in texture names and as the frame index for the stage's cosmetics.

## Stage PAC Files

The main component that makes up a stage is its **PAC file**. Every stage has a PAC file associated with it. The PAC file contains all of the models, animations, and graphics you see in the stage while you're playing it, and in some cases can also dictate some of the stage's behavior.

<img src="images/StagePacExample.png" alt="Screenshot of a stage PAC file" width="700"/>

In most stage PAC files, the majority of the relevant content is located in the `2` archive. This section will go over a few of the important components of a stage PAC file, but it is not comprehensive.

### Models, Animations, and Textures

The stages models are located in **Model Data** archives throughout the `2` archive. Each Model Data archive can (typically) have any number of models in it, but generally, only one animation in each Model Data will play at a given time. As such, if you want multiple different animations playing at once, you probably need to split them throughout different Model Datas.

Which Model Datas will be loaded for the stage is determined entirely by the stage [module](coding?id=modules). If you're unsure which Model Datas work for your stage, you should check what the original stage that your stage's module is based upon uses - those Model Datas should work for your custom stage as well. If you need different Model Datas, you can use a different module or create a custom one.

Generally, Model Data [100] contains a stagePosition (or similarly named) model which controls some of the basic positioning of elements in your stage. The bones of this model control things like camera limits, death and respawn positions, item spawn positions, and more.

<img src="images/StagePositionExample.png" alt="Screenshot of the stage position of a stage" width="700"/>

Model Data [101] is generally used for the placement of Pokemon Trainer.

Textures for a stage are usually all placed within a single `Texture Data` archive in the PAC file.

### Collision Data

Every stage has collision data, which controls the stage's collision behavior with fighters, items, etc. Some stages might have more than one collision data.

<img src="images/StageCollisionExample.png" alt="Screenshot of a stage's collision data" width="700"/>

### Effect Bank

Some stages have an effect bank. This effect bank is usually named something like `ef_StgBattlefield`, where `Battlefield` is the name of the stage. This is not always accurate, however. The effect bank is at the root of the PAC file in it's own archive.

#### Stage PAC Guides
- [Brawl/PM Stage Modding Tutorial](https://www.youtube.com/watch?v=COikXif5cQ4) by Electropolitan - A detailed video guide on how to create your own stage, this video focuses on how to construct the stage mostly within the PAC file.

## Stage Modules

The actual code of a stage is controlled by its **module**. This dictates custom behavior like hazards and autoscrolling, but it also controls simple things like which models will actually appear in the stage.

Stage modules are very powerful and can do just about anything, from spawning simple hazards or playing animations to completely changing the game's behavior.

Stage modules are generally located in `pf/module` and usually named something like `st_stage.rel`, where `stage` is the name of the stage.

Unlike other modules, stage modules have been fully decompiled, meaning new modules can be created from scratch in C++. See the coding [modules](coding?id=modules) section for more details.

#### Stage Module Resources
- [BrawlStageModule](https://github.com/ilazoja/BrawlStageModule) repository by ilazoja - A repository of custom stage modules written in C++. A great resource if you want to create your own stage modules in C++.
- [BrawlHeaders](https://github.com/Sammi-Husky/BrawlHeaders) - Repository of header files containing Brawl functions. Useful for identifying what functions are available for use, and necessary when creating custom modules.

## Param Files

If your build uses the Stage Expansion system, then instead of stage details (such as IDs, PACs, and modules) being hardcoded, they are controlled with customizable `.param` files. These files can be found in `pf/stage/stageinfo`, and are generally named after the stage.

<img src="images/StageParamExample.png" alt="An example of a stage param file" width="700"/>

Param files can be edited in BrawlCrate. Here is a quick overview of what the fields within a param do:
- **IsFlat** - If true, makes fighters render as flat 2D planes while playing on the stage, similar to the Flat Zone stages.
- **IsFixedCamera** - If true, the camera will remain in a fixed position at all times and will not move.
- **IsSlowStart** - Unknown
- **StageName** - The name used for the stage's PAC file, prepended with `STG`. For example, if this field is `Battlefield`, then when this param is selected, `STGBATTLEFIELD.pac` will load.
- **TrackList** - The name of the tracklist to load for this stage. For example, if this field is `Battlefield`, then when is param is selected, songs from `Battlefield.tlst` will play.
- **Module** - The module to load for this stage. This is the full filename of the module - for example, `st_battle.rel`.
- **CharacterOverlay** - An RGB color to be overlayed over all characters when the stage is played.
- **SoundBank** - The soundbank to load when the stage is played. This is the soundbank InfoIndex.
- **EffectBank** - The ID of the effect bank the stage uses. This must match up with the effect bank name in the PAC file.
- **MemoryAllocation** - The amount of extra memory to allocate for the stage module to use. Whatever number is entered here will be subtracted from the stage's memory pool and made accessible for the module to load resources in the `StageResource` heap. Generally only used when you have custom module behavior.
- **WildSpeed** - Stage speed modifier when "Wild Mode" is enabled in builds that have it.

### Substages

Param files also allow you to add **substages**.

<img src="images/SubstageExample.png" alt="An example of a param file with substages set up" width="700"/>