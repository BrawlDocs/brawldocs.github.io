# Syriinge

[Syriinge](https://github.com/Sammi-Husky/Syriinge) allows you to create plugins using C++ that hook to locations in memory and execute code. Unlike ASM codes, it does not require hardcoding an address - you can specify what REL the code within the plugin is hooking to, and an offset from where that REL is loaded in memory. This means it can dynamically link your code to REL code, so even if the module's location in memory changes, your plugin will still be pointing to the right place.

Because Syriinge plugins are so dynamic and can be written in C++, they are very powerful and one of the most versatile methods of making code changes for Brawl.

Syriinge plugins are generally included in the `pf/plugins` folder of a build. When plugins are installed to this location, if the build has Syriinge integrated, they should be applied automatically.

#### Syriinge Resources
- [Syriinge](https://github.com/Sammi-Husky/Syriinge) - The Syriinge frameworkf or creating plugins.
- [Ghidra](tools?id=ghidra) - Used to navigate the game's code to better understand it for your modifications.
- [Dolphin Memory engine](tools?id=dolphin-memory-engine) - Used to monitor the game's memory to better understand the game's code for your modifications.
- [BrawlHeaders](https://github.com/Sammi-Husky/BrawlHeaders) - Repository of header files containing Brawl functions. Necessary for calling the game's functions from a plugin.
