# reltools Guide

This is a basic guide on how to use [reltools](tools?id=reltools). This guide just covers how to use reltools, not how to code in PowerPC Assembly to actually make your changes.

Note that reltools uses the standard PPC assembler. If you're used to GCTRM, the syntax is slightly different. [See here](https://mariokartwii.com/showthread.php?tid=1083) for the syntax used.

---

## Prerequisites
In order to get started, you’ll want to make sure you have the following:
- [reltools](tools?id=reltools) by Sammi Husky
- [The game’s map files](https://www.mediafire.com/file/k8jilon7g0zcri8/maps.zip/file)
- The module file you want to edit

Optionally, you may want the following:
- [Ghidra](tools?id=ghidra) and the [GameCube Loader](https://github.com/Cuyler36/Ghidra-GameCube-Loader)

## Disassembling

To get started, you need to disassemble your module file. To do so, open a command line window and enter the following command:

`"path\to\reltools\reltools.exe" -x  "path\to\module\ft_module.rel" -m "path\to\maps"`

This command will disassemble the provided rel with reltools.exe, mapping code using the game’s map files. It’s important to disassemble using the map files because it will make the disassembled code easier to understand.

The module will get disassembled into multiple .asm files, each named “Section” with an associated number.

## Assembling

After you’ve made your code changes, you’ll want to recompile the module. To do so, you’ll run the following:

`"path\to\reltools\reltools.exe" -r  "path\to\reltools\dump\ft_module\ft_module.json" -o "module" -m "path\to\maps"`

## Relocation Commands

There are some extra commands you can use in your disassembled .rel files to retrieve data or perform functions in other files. To use these, place them to the right of any instruction in your code, ideally separated by tabs. With each of these commands, you can put a set of parentheses after them including a few arguments:
- The module name to access, in quotes - for example, even if I am editing Mario’s module, I could put “sora_melee” in quotes to access a function of the game itself.
- The section # of the module to access - for example, if I want a function from Section [1] of sora_melee, I would enter 1.
- The location in the .asm code to access, in quotes - the disassembled code is usually separated into locations. These locations are marked with labels. Some will have names because of the maps you used when decompiling, but some may only be labeled by their address (e.g. loc_1DAC28). You should enter the label you’re trying to go to for this argument.

With arguments, your commands will likely end up looking something like this: `[R_PPC_REL24("sora_melee", 1, "Weapon__reflect")]`

Below are all the commands you can use in this manner.

`[R_PPC_ADDR16_HA]`
Gets the upper bytes of the designated address and uses them in your instruction. For example, placing this after an instruction of lis r3, 0x0 will use the upper bytes of the address in place of the 0x0.

`[R_PPC_ADDR16_LO]`
Like above, gets the lower bytes of the designated address and uses them in your instruction.

`[R_PPC_ADDR32]`
Like above, gets the full address from the designated location. This overwrites the whole byte, so you generally use it to store pointers rather than using it with instructions.

`[R_PPC_REL24]`
When used after a branch instruction such as b or bl, this command replaces the branch location with the location specified in the command. This is useful for making function calls, for example, allowing you to branch to a location in another file to execute code from that file. Generally, you should place this after instructions that branch to an `__unresolved` label so that if the relcommand fails to be found it can branch to a default function in your module.