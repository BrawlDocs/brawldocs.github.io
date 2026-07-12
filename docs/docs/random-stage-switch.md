# Random Stage Switch

If you're using the latest version of the Stage Expansion system, you can also modify which stages are enabled/disabled by default for random selection, whether or not hazards are enabled for them, and you can add presets that players can swap between on the random stage switch (RSS) screen in-game.

## RSS Files

!> Requires the latest Stage Expansion system!

**RSS** files control which stages are listed on the stage select screen, which stages are available from random stage selection, and which stages have hazards enabled or disabled by default. These files are located in `pf/stage/switch` in the build. They are named `Switch##.rss`, where `##` is the index (in hexadecimal format) of the preset that will load that switch file. For example, `Switch00.rss` would be the RSS file that's loaded by default, while `Switch01.rss` would be the first preset you can switch to from the RSS screen. `SwitchFF.rss` is the exception to this - this file is always the default in netplay only, rather than using `Switch00.rss`.

RSS files cannot currently be edited using BrawlCrate. However, [BrawlInstaller](/intro/tools?id=BrawlInstaller) can edit these files like any other stage list. See the BrawlInstaller wiki for more information.

## Presets

!> Requires the latest Stage Expansion system!

The modern Stage Expansion system lets you have multiple RSS **presets**, each tied to an RSS file. These presets can be swapped between from the RSS screen in-game using L or R. Pressing these buttons cycles through the presets, changing what stages are available on the stage list, in random, and which stages have hazards enabled.

For example, if you have a `Switch00.rss` and a `Switch01.rss`, when you first arrive on the RSS screen, the preset associated with `Switch00.rss` will be loaded, but pressing R will automatically switch to `Switch01.rss`. Swapping between them will swap what stages are available.

### Changing Preset Count

Adding or removing an RSS file alone is not enough to change how many presets show up in-game. If you change how many RSS files are in your build, you probably want to change the preset count in your build as well.

This count is controlled by a code, usually in `Source/Project+/Random.asm`. In this code you will see a line that reads `.alias NUM_PRESETS = 0x7 # Change for more presets`.

<img src="images/PresetCount.png" alt="Screenshot of the preset count alias in code" width="700"/>

Change the value after `NUM_PRESETS` to match the number of presets you want to use in your build (in hexadecimal format). For example, if I were to add one preset, I would change the line to read `.alias NUM_PRESETS = 0x8`.

Once this change is made, you need to recompile your codeset.

### Changing Preset Names

If you are changing the number of presets, or just want to change the names of existing presets, you also need to alter the preset name list. By default, this list is located in two separate files - `pf/menu2/mu_menumain.pac` (for the main menu rules) and `pf/menu2/sc_selcharacter2.pac` (for the CSS rules). In both of these files, the list of preset names can be found in `MenuRule_en/Misc Data [1]`.

<img src="images/PresetList.png" alt="Screenshot of a preset name list" width="700"/>

In BrawlCrate, you can click this node to see the list of preset names. Note that this list contains not only the preset names, but also the names of the stages, which all follow the presets. The presets start at index 0, and the number of presets listed will be equal to the preset count.

You can click any entry in the list to reveal a textbox where you can change the name that will display in-game. If you wish to remove a preset, you can select it and click the `-` button. If you want to add one, make sure you have the _last preset_ in the list selected, not a stage name or anything else, and click the `+` button. In the above example, if I wanted to add a new preset, I would select the entry that reads `All Stages` (as it is the 7th entry) and click the `+` to add my new, eigth preset.