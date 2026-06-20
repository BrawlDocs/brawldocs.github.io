# Effect Banks

**Effect banks** (also referred to as Effect.pacs and GFX banks) control what graphical effects (GFX) can play at a given time. If an effect bank is loaded into memory, it's GFX can be played by calling on them by GFX ID.

Effect banks are hardcoded. Every effect bank has an ID, a name, and a number of GFX within it with their own GFX IDs. Usually, effect banks are referenced by name within pac files, and that name is mapped to an ID internally.

Effect banks should be unique to the entities that use them, or else their GFX can conflict. For example, if you have two custom fighters both using the `ef_custom00` effect bank, and they both load into a match at the same time, one of the fighters might play the other fighter's GFX, which could end up looking strange.

## GFX

**GFX** are individual graphical effects that exist in an effect bank. Effects like fireballs, explosions, or bursts of light are usually an individual GFX that resides within an effect bank. Individual GFX all have their own IDs within their corresponding effect bank, which is what is used to play the GFX.

## Traces

**Traces** are a "motion blur" effect that things like swords trail as they're swung. Only certain effect banks have traces in them.

# Resources

#### Effect Bank Resources

- [ICLPX's GFX Lists](https://iclpx.web.fc2.com/GE.html) - A site with multiple lists of different GFX featured in the base game with sample images. This link is to the "Common GFX List", the GFX that are part of the common banks which are always loaded, but the site has numerous other GFX lists as well.
- [Visual dictionary for universal GFXs in PSA](https://www.youtube.com/watch?v=_-mwMQQHDn0) - A video demonstrating all of the common GFX in the base game.
- [JOJI's site](http://ssbbhack.web.fc2.com/index.html) - A site that has numerous resources on effect banks and GFX, including lists of effect bank IDs and some tutorials. Most useful as a resource for learning about the custom Effect.pacs that are part of the Effect.pac Roster Expansion System.

#### Effect Bank Guides

- [EDITING GFX COLORS VIA REFF EDITING AND PSA SHENANIGANS](https://docs.google.com/document/d/1yzk97Ay7nfKFDRYBb0357XUOqOgJgk7edloVvzInyQo/edit?usp=sharing) by extreme - A general guide on how to edit GFX within an effect bank.