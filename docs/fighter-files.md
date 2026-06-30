# Fighter Files

Every fighter in Brawl has a number of different types of **fighter files**. These are various PAC files that load whenever the fighter is loaded. Understanding what each of these files is for is critical to understanding how fighters work in Brawl.

All fighter files are usually located in `pf/fighter/fightername`, where `fightername` corresponds to the fighter's file name.

## Moveset File

The fighter's main moveset file is the file containing their [PSA](psa.md). It also contains their [effect bank](effectbanks.md). It is the core of the fighter, and usually aligns to the [Fighter File Name](exconfigs?id=fighter-config-fields) in [BrawlEx](brawlex.md) builds.

Usually this file is named `FitFightername.pac`, where `Fightername` is the fighter's file name.

## Costume Files

Every costume has a model, which is contained in the costume's corresponding **costume file**. These files are usually named `FitFighternameXX.pac`, where `Fightername` is the fighter's file name and `XX` is the [costume ID](exconfigs?id=costumes).

## MotionEtc Files

All fighters have animations, and some have miscellanous models that must be loaded along with the fighter. Often, these things are combined into one `MotionEtc` file, usually named `FitFighternameMotionEtc.pac`, where `Fightername` is the fighter's file name. However, in some cases, these files are split into a separate `Motion` and `Etc` file, aptly named `FitFighternameMotion.pac` and `FitFighternameEtc.pac`. If the fighter is set up with [costume-specific](exconfigs?id=fighter-config-fields) `MotionEtc` files, these could be named ending in a costume ID as well.

## Entry Files

Sometimes, fighters will load extra models for their entry animation - the animation that plays when the match first starts. Files containing these models are usually named `FitFighternameEntry.pac`, where `Fightername` is the fighter's file name. If the fighter has [costume-specific](exconfigs?id=fighter-config-fields) entry files, these will be named `FitFighternameEntryXX.pac`, where `Fightername` is the fighter's file name and `XX` is the costume ID.

## Result Files

Sometimes, fighters will load extra models for their results animation - the animation that plays on the results screen when the fighter wins. Files containing these models are usually named `FightFighternameResult.pac`, where `Fightername` is the fighter's file name. If the fighter has [costume-specific](exconfigs?id=fighter-config-fields) results files, these will be named `FitFighternameResultXX.pac`, where `Fightername` is the fighter's file name and `XX` is the costume ID.

## Final Files

Sometimes, fighters will load extra models for their final smash. Files containing these models are usually named `FitFighternameFinal.pac`, where `Fightername` is the fighter's file name. If the fighter has [costume-specific](exconfigs?id=fighter-config-fields) final files, these will be named `FitFighternameFinalXX.pac`, where `Fightername` is the fighter's file name and `XX` is the costume ID.

## Kirby Hat Files

When a fighter is loaded in a match with Kirby, the models and data for their Kirby hat must also be loaded. These files are usually located in `pf/fighter/kirby`, instead of the fighter's own folder, and are named `FitKirbyFightername.pac`, where `Fightername` is the fighter's file name. If the fighter has [costume-specific](exconfigs?id=fighter-config-fields) Kirby hat files, these will be named `FitKirbyFighternameXX.pac`, where `Fightername` is the fighter's file name and `XX` is the costume ID.