# Modules

**Modules** are relocatable chunks of game code used in Brawl. Modules use the `REL` file format. A great deal of the game's code lives in modules.

Editing module code requires you to disassemble the module using reltools, modify the ASM code within, and then reassemble it. Module edits are very similar to writing codes, but because the code is relocatable, it can be a bit harder to find the code in memory during runtime.

Technically, it is possible to edit module code using an ASM code and hardcoding the expected address, but the relocatable nature of modules makes this undesirable. As such, it's preferable to use module edits whenever modifying code that exists in a rel file.

Modules can also be created from scratch in C++, but as of right now the only modules that have been fully reverse-engineered - and thus are properly recreatable in C++ - are stage modules.

Modules are generally located in the `pf/module` folder of a build.

## Configuring reltools

Editing modules is primarily done using [reltools](tools?id=reltools). You'll need to install it to make any edits. You'll also need the [game's map files](https://www.mediafire.com/file/k8jilon7g0zcri8/maps.zip/file) to ensure that disassembled have their functions labeled correctly.

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

---

# Resources

#### Module Resources
- [reltools](tools?id=reltools) - Used to disassemble and reassemble module REL files.
- [Ghidra](tools?id=ghidra) - Used to navigate the game's code to better understand it for your modifications.
- [Dolphin Memory engine](tools?id=dolphin-memory-engine) - Used to monitor the game's memory to better understand the game's code for your modifications.
- [BrawlStageModule](https://github.com/ilazoja/BrawlStageModule) repository by ilazoja - A repository of custom stage modules written in C++. A great resource if you want to create your own stage modules in C++.
- [Brawl Map Files](https://www.mediafire.com/file/k8jilon7g0zcri8/maps.zip/file) - Map files that can be used in conjunction with reltools to ensure disassembled modules have their functions labeled correctly.
- [BrawlHeaders](https://github.com/Sammi-Husky/BrawlHeaders) - Repository of header files containing Brawl functions. Useful for identifying what functions are available for use, and necessary when creating custom modules.

#### Module Guides
- [reltools Guide](guides/reltools-guide.md) - A guide to using reltools to disassemble and reassemble modules
- [ItemEx Module Coding Guide](https://docs.google.com/document/d/12ieb0cPkGLjRZdXVSUirTJHD9HSfxf14XR9i2fHvMK4/edit?tab=t.0#heading=h.o0hu77g8ofa5) - A guide to setting up ItemEx on a fighter using reltools