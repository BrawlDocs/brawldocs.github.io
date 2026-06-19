# Coding

This section goes over some of the essentials to understanding how custom codes work in Brawl. Because of the extensive nature of coding, this page is mostly a landing page, linking resources that go into greater detail.

Coding allows you to change the game's core functionality at the deepest level. With enough coding knowledge, the possibilities in Brawl modding are nearly limitless. If your goal is to really change core functionality beyond what's listed in other sections here, coding is probably where you need to start.

---

## Codes

The most basic way to change core functionality in Brawl is writing custom **codes**. "Codes", in this context, refers to patches written in PowerPC Assembly (colloquially referred to as "ASM") or Gecko (a raw hex format primarily used in older codes).

In Brawl modding, codes are written primarily by identifying addresses in memory that you wish to patch to change the game's behavior, then writing some assembly code that patches to that instruction. This code can then be compiled into a Gecko (GCT) format with GCTRealMate, which can then be read by the game.

Most custom codes are written in ASM files located in the `Source` folder at the root of the build. Some may be written directly to `RSBE01.txt` or `BOOST.txt`, also at the root of the build.

Learning to create codes requires you to learn PowerPC Assembly and gain an understanding of how to navigate and debug the game's code.

### Adding Codes

Whether you are creating your own custom codes or adding one someone else created, you need to make sure they're included in your build. There are two methods to doing this:

- Add the codes directly to `RSBE01.txt` or `BOOST.txt`.
- Add the codes to a `.asm` file (or create a new one) in your build and add an `.include` referencing it to `RSBE01.txt` or `BOOST.txt`. The format of an include is `.include path/to/asmfile`, where the `path/to/asmfile` is the relative path to the ASM file from `RSBE01.txt` or `BOOST.txt`. For example, if you want to include `PokeTrainer.asm` located in `Source/Project+` in your build, your include would be `.include Source/Project+/PokeTrainer.asm`.

### Compiling Codes

Whenever you modify any codes, you need to recompile your codeset. The game reads code from `RSBE01.GCT` and `BOOST.GCT`, so these files need to be rebuilt using your new code whenever a change is made. To do this, ensure GCTRealMate.exe is included in your build (for most builds, it should already be there), and drag `RSBE01.txt` and `BOOST.txt` over the `.exe`. When you do, a black window should appear compiling your codeset.

If you get a message indicating it compiled successfully, your code changes should now be applied. If you see an error, or the message closes on its own, there is probably an issue with your codeset.

### Disabling Codes

It is possible to disable a code if you wish to keep it present in your build but don't want it to activate while playing the game. To do so, locate the code in its respective `.txt` or `.asm` file and simply place a `!` at the start of the code's name. For example, if you wish to disable the code `Stock/Frame Control not disabled in 300% Mode 1.1 [wiiztec]` in `RSBE01.txt`, you would simply rename it to `!Stock/Frame Control not disabled in 300% Mode 1.1 [wiiztec]`.

#### Codes Resources
- [GCTRealMate](tools?id=gctrealmate) - Used to compile ASM codes to a GCT file that can be read by the game.
- [Ghidra](tools?id=ghidra) - Used to navigate the game's code to better understand it for your modifications.
- [Dolphin Memory engine](tools?id=dolphin-memory-engine) - Used to monitor the game's memory to better understand the game's code for your modifications.
- [RSBE01.map](https://www.mediafire.com/file/plmu3xqoraz1yo1/RSBE01.map/file) - A map file for Brawl's static functions that can be loaded while running the game in Dolphin to ensure functions are labeled correctly.

#### Codes Guides
- [Learn PowerPC for Wii Cheat Codes Index](https://mariokartwii.com/showthread.php?tid=1114) by Vega on MarioKartWii.com - An index of threads for learning how to use PowerPC Assembly to write codes for Wii games. General-purpose for Wii coding as a whole, but applies to Brawl as well.

## Modules

**Modules** are relocatable chunks of game code used in Brawl. Modules use the `REL` file format. A great deal of the game's code lives in modules.

Editing module code requires you to disassemble the module using reltools, modify the ASM code within, and then reassemble it. Module edits are very similar to writing codes, but because the code is relocatable, it can be a bit harder to find the code in memory during runtime.

Technically, it is possible to edit module code using an ASM code and hardcoding the expected address, but the relocatable nature of modules makes this undesirable. As such, it's preferable to use module edits whenever modifying code that exists in a rel file.

Modules can also be created from scratch in C++, but as of right now the only modules that have been fully reverse-engineered - and thus are properly recreatable in C++ - are stage modules.

Modules are generally located in the `pf/module` folder of a build.

#### Module Resources
- [reltools](tools?id=reltools) - Used to disassemble and reassemble module REL files.
- [Ghidra](tools?id=ghidra) - Used to navigate the game's code to better understand it for your modifications.
- [Dolphin Memory engine](tools?id=dolphin-memory-engine) - Used to monitor the game's memory to better understand the game's code for your modifications.
- [BrawlStageModule](https://github.com/ilazoja/BrawlStageModule) repository by ilazoja - A repository of custom stage modules written in C++. A great resource if you want to create your own stage modules in C++.
- [Brawl Map Files](https://www.mediafire.com/file/k8jilon7g0zcri8/maps.zip/file) - Map files that can be used in conjunction with reltools to ensure disassembled modules have their functions labeled correctly.
- [BrawlHeaders](https://github.com/Sammi-Husky/BrawlHeaders) - Repository of header files containing Brawl functions. Useful for identifying what functions are available for use, and necessary when creating custom modules.

#### Module Resources
- [reltools Guide](guides/reltools-guide.md) - A guide to using reltools to disassemble and reassemble rel files.
- [ItemEx Module Coding Guide](https://docs.google.com/document/d/12ieb0cPkGLjRZdXVSUirTJHD9HSfxf14XR9i2fHvMK4/edit?usp=sharing) - A guide on how to make module edits to integrate ItemEx for fighters.

## Syriinge

[Syriinge](https://github.com/Sammi-Husky/Syriinge) allows you to create plugins using C++ that hook to locations in memory and execute code. Unlike ASM codes, it does not require hardcoding an address - you can specify what REL the code within the plugin is hooking to, and an offset from where that REL is loaded in memory. This means it can dynamically link your code to REL code, so even if the module's location in memory changes, your plugin will still be pointing to the right place.

Because Syriinge plugins are so dynamic and can be written in C++, they are very powerful and one of the most versatile methods of making code changes for Brawl.

Syriinge plugins are generally included in the `pf/plugins` folder of a build. When plugins are installed to this location, if the build has Syriinge integrated, they should be applied automatically.

#### Syriinge Resources
- [Syriinge](https://github.com/Sammi-Husky/Syriinge) - The Syriinge frameworkf or creating plugins.
- [Ghidra](tools?id=ghidra) - Used to navigate the game's code to better understand it for your modifications.
- [Dolphin Memory engine](tools?id=dolphin-memory-engine) - Used to monitor the game's memory to better understand the game's code for your modifications.
- [BrawlHeaders](https://github.com/Sammi-Husky/BrawlHeaders) - Repository of header files containing Brawl functions. Necessary for calling the game's functions from a plugin.
