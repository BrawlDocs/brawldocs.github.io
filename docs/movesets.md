# Movesets

This section goes over some of the essentials to understand moveset modding in Brawl. Due to the extensive nature of moveset modding, this page serves mostly as a landing spot, linking more detailed resources.

Movesets are the lifeblood of a fighter - they control everything that happens when you press a button during a match. Which animations play, the shape and size of hitboxes, the sounds and graphics that display - with moveset modding, you can control all of these things.

---

## PSA

**PSA** is the colloquial term for the primary way modders work with fighter movesets. Named after "Project Smash Attacks", the original program that was used for editing fighter movesets in the modding scene, today the term PSA is essentially shorthand for editing the fighter moveset data that is contained in the fighter's PAC file. In reality, this data is actually officially referred to as "AnimCmd", but the community generally uses the term PSA.

PSA is a sort of pseudo-coded scripting language. When working with PSA, you are generally selecting fighter animations (referred to as "Motion" in game code and "Sub Actions" in PSA software) and adding "events" that trigger when those animations play.

<img src="images/PSAExample.png" alt="An example of some PSA scripting" width="700"/>

_Example of some PSA scripting._

Fighter PSA is located within the fighter's main PAC file, usually located in `pf/{fighterName}/{fighterName}.pac`, where {fighterName} is replaced with the fighter's name. When this file is viewed in BrawlCrate, the actual PSA data can be found in `Misc Data [0]`.

<img src="images/FighterPacExample.png" alt="An example of a fighter PAC" width="700"/>

_Example of a fighter PAC. Misc Data [0] generally contains the actual PSA code for the fighter._

#### PSA Resources
- [PSACompressor](tools?id=psacompressor) - The primary tool for editing fighter PSA.

#### PSA Guides
- [PSA Coding Guide](https://gamebanana.com/mods/533181) by Montimers - A series of PDFs explaining PSA coding at a high level, this is the best starting point for learning PSA.

## Modules

Like most things in Brawl, fighters also have code stored in their [modules](coding?id=modules). While PSA controls the high-level functionality of the fighter linked to their animations, modules dictate what functionality is available for the fighter to use in PSA.

Fighter modules can be found in `pf/module` within a build, and usually are named `ft_{fighterName}.rel`, where {fighterName} is the fighter's name.