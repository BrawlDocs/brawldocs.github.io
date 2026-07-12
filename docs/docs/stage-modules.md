# Stage Modules

The actual code of a stage is controlled by its **module**. This dictates custom behavior like hazards and autoscrolling, but it also controls simple things like which models will actually appear in the stage.

Stage modules are very powerful and can do just about anything, from spawning simple hazards or playing animations to completely changing the game's behavior.

Stage modules are generally located in `pf/module` and usually named something like `st_stage.rel`, where `stage` is the name of the stage.

Unlike other modules, stage modules have been fully decompiled, meaning new modules can be created from scratch in C++. See the coding [modules](modules.md) section for more details.

---

## Resources

#### Stage Module Resources
- [BrawlStageModule](https://github.com/ilazoja/BrawlStageModule) repository by ilazoja - A repository of custom stage modules written in C++. A great resource if you want to create your own stage modules in C++.
- [BrawlHeaders](https://github.com/Sammi-Husky/BrawlHeaders) - Repository of header files containing Brawl functions. Useful for identifying what functions are available for use, and necessary when creating custom modules.