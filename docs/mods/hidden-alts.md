# Hidden Alts

**Hidden alts** are costumes hidden behind a button press. In most builds, these are accessible by holding `R` or `Z` while transitioning from the character select screen to the stage select screen after pressing `Start`. The buttons must be held until the SSS loads and displays.

Hidden costumes are enabled by a code called `[Legacy TE] Hold Z for AltZ Characters, R/C for AltR Characters V3.2 [PyotrLuzhin, codes, ASF1nk, Yohan1044, DukeItOut]` in older builds, generally located in `AltCostume.asm` in `Source/LegacyTE`. Newer builds are instead generally enabled by `HiddenAltSets.asm` in `Source/P+Ex`, which has more features.

Hidden costumes work like other costumes, but they don't require an entry in the fighter's [CSSSlot config](docs/exconfigs?id=cssslotconfig). Instead, you simply add the costume's PAC file, named in the format `FitFighterAltR.pac` or `FitFighterAltZ.pac` (where `Fighter` is the fighter's file name) for costumes accessed by holding `R` and `Z`, respectively. See [fighter costume files](docs/fighter-files?id=costume-files) for more information on costume files.

## Hidden Alt Sets

Newer builds allow for **hidden alt sets** by using the code generally located in `HiddenAltSets.asm` in `Source/P+Ex`. With hidden alt sets, you can have additional hidden alts tied to each _costume_ instead of just a single AltR and AltZ per _character_. These costumes are accessed by holding `R+Z` when transitioning from CSS to SSS, similar to accessing regular hidden alts.

Hidden alt set costumes are tied to a specific costume. Like regular hidden alts, they only require adding a PAC file. The naming format is `FitFighterAltXX.pac`, where `Fighter` is the fighter file name and `XX` is the costume ID you want to tie the hidden alt to.

To load a hidden alt set costume, you simply have the base costume ID selected and then hold `R+Z` while transitioning to the SSS. For example, to access Mario's hidden costume `FitMarioAlt00.pac`, you would select his first costume (ID `00`) and hold `R+Z` while transitioning from CSS to SSS.