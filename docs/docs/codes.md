# Codes

The most basic way to change core functionality in Brawl is writing custom **codes**. "Codes", in this context, refers to patches written in PowerPC Assembly (colloquially referred to as "ASM") or Gecko (a raw hex format primarily used in older codes).

In Brawl modding, codes are written primarily by identifying addresses in memory that you wish to patch to change the game's behavior, then writing some assembly code that patches to that instruction. This code can then be compiled into a Gecko (GCT) format with GCTRealMate, which can then be read by the game.

Most custom codes are written in ASM files located in the `Source` folder at the root of the build. Some may be written directly to `RSBE01.txt` or `BOOST.txt`, also at the root of the build.

Learning to create codes requires you to learn PowerPC Assembly and gain an understanding of how to navigate and debug the game's code.

## Adding Codes

Whether you are creating your own custom codes or adding one someone else created, you need to make sure they're included in your build. There are two methods to doing this:

- Add the codes directly to `RSBE01.txt` or `BOOST.txt`.
- Add the codes to a `.asm` file (or create a new one) in your build and add an `.include` referencing it to `RSBE01.txt` or `BOOST.txt`. The format of an include is `.include path/to/asmfile`, where the `path/to/asmfile` is the relative path to the ASM file from `RSBE01.txt` or `BOOST.txt`. For example, if you want to include `PokeTrainer.asm` located in `Source/Project+` in your build, your include would be `.include Source/Project+/PokeTrainer.asm`.

## Compiling Codes

Whenever you modify any codes, you need to recompile your codeset. The game reads code from `RSBE01.GCT` and `BOOST.GCT`, so these files need to be rebuilt using your new code whenever a change is made. To do this, ensure GCTRealMate.exe is included in your build (for most builds, it should already be there), and drag `RSBE01.txt` and `BOOST.txt` over the `.exe`. When you do, a black window should appear compiling your codeset.

If you get a message indicating it compiled successfully, your code changes should now be applied. If you see an error, or the message closes on its own, there is probably an issue with your codeset.

## Disabling Codes

It is possible to disable a code if you wish to keep it present in your build but don't want it to activate while playing the game. To do so, locate the code in its respective `.txt` or `.asm` file and simply place a `!` at the start of the code's name. For example, if you wish to disable the code `Stock/Frame Control not disabled in 300% Mode 1.1 [wiiztec]` in `RSBE01.txt`, you would simply rename it to `!Stock/Frame Control not disabled in 300% Mode 1.1 [wiiztec]`.

---

## Resources

#### Codes Resources
- [GCTRealMate](/intro/tools?id=gctrealmate) - Used to compile ASM codes to a GCT file that can be read by the game.
- [Ghidra](/intro/tools?id=ghidra) - Used to navigate the game's code to better understand it for your modifications.
- [Dolphin Memory engine](/intro/tools?id=dolphin-memory-engine) - Used to monitor the game's memory to better understand the game's code for your modifications.
- [RSBE01.map](https://www.mediafire.com/file/plmu3xqoraz1yo1/RSBE01.map/file) - A map file for Brawl's static functions that can be loaded while running the game in Dolphin to ensure functions are labeled correctly.

#### Codes Guides
- [Learn PowerPC for Wii Cheat Codes Index](https://mariokartwii.com/showthread.php?tid=1114) by Vega on MarioKartWii.com - An index of threads for learning how to use PowerPC Assembly to write codes for Wii games. General-purpose for Wii coding as a whole, but applies to Brawl as well.