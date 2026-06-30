# BrawlEx

**BrawlEx** is a framework for Brawl that allows users to add fighters and costumes to the game in a standardized way. It is a combination of code, fileset, and module changes that makes it easier and more flexible to add content.

BrawlEx is primarily driven by `bx_fighter.rel` located in `pf/module`. This contains the primary BrawlEx code and also the basic fighter data for all vanilla characters.

Most modern builds integrate BrawlEx in order to add more characters and costumes.

## EX Configs

While bx_fighter.rel is the primary driver of BrawlEx's code, BrawlEx features various config files called [EX Configs](exconfigs.md). These files can be used to configure details about a fighter, such as what files to load for them and how many costumes they have. These configs are usually located in `pf/BrawlEx` in a build.

## EX Modules

BrawlEx also comes with edited modules called **EX modules**. EX modules are [fighter modules](fighter-modules.md) that have been modified to be easier to work with. Regular fighter modules have scattered references to the fighter's ID all throughout the module, while EX modules include only one single reference to the fighter's ID in the module's `Section[8]`. This makes it far easier to change the IDs associated with the fighter.

## 128 vs 242

BrawlEx has had a few different iterations over the years. Most implementations of BrawlEx have a limit of **128** fighters you can have in the game at a given time. However, there have been other implementations that expand this number to **242**. You may see both of these referenced in different builds.

---

## Resources

#### BrawlEx Guides

- [BrawlEx Guide for P+Ex](https://docs.google.com/document/d/1ZoL_qDcwUpUXg82cKaUp-6D_AcfpFctoW6GXFY74_0k/edit?usp=sharing) by KingJigglypuff, originally by Robintjuh - A general-purpose guide for installing BrawlEx characters to P+Ex builds. Goes into great detail on all aspects of BrawlEx.
- [Internal ID References](https://docs.google.com/document/d/1mQaRwM4dh9g1owel6_ZFNSVwmllbO1pcC7IaYtmJBzM/edit?usp=sharing) by KingJigglypuff - A list of all fighter IDs in Brawl, Project+, and P+Ex. Useful for knowing which configs are used by which fighters.

#### EX Config Resources

- [P+Ex Config Templates](https://drive.google.com/file/d/19rv-2aUKViQu9autyLLmJA-JLQ-hPgII/view?usp=sharing) - EX configs for the entire P+Ex cast which can be copied and edited to use as a base for new characters.
- [BrawlEx Clone Engine v2.0.0.0](https://www.dropbox.com/scl/fi/cfhky1qei05tgh2i9h9e4/BrawlEx-Clone-Engine-v2.0.0.0.zip?rlkey=19j941xh8voem46x712q5vaoh&e=1&dl=0) - The original BrawlEx archive, containing vBrawl EX configs and EX modules for the vanilla cast.
- [ProjectM + BrawlEx Resources](https://www.mediafire.com/file/5funzwc4prer6fe/ProjectM%252BBrawlEx_Resources.zip/file) - An archive of the EX configs and EX modules for Project M + BrawlEx.