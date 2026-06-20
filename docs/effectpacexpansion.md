# Effect.pac Roster Expansion System

The **Effect.pac Roster Expansion System** is a framework created by JOJI to add more available [effect banks](effectbanks.md) to the game. The system adds **255** new available effect banks, starting at ID 311 and ending at ID 566.

The expansion effect banks are named consistently, all following a pattern of `ef_customXX`, where `XX` starts at `00` for the first custom effect bank and ends at `ef_customFF` for the last one.

Every custom bank comes with [traces](effectbanks?id=traces) as well. Each custom bank has up to 10 traces, which also follow a consistent naming scheme of `TexCustomXXTraceYY`, where `XX` matches the `XX` of the effect bank name and `YY` is the index (zero-indexed) of the trace within the effect bank. For example, the first trace of `ef_custom00` would have a texture named `TexCustom00Trace00`, while the second trace would be `TexCustom00Trace01`.

Trace IDs for custom banks start at 140 for the first trace in the first bank and go up incrementally by 1. This means `ef_custom00` contains trace IDs 140 through 149, while `ef_custom01` contains trace IDs 150 through 159, and so on.

Most modern builds integrate this system.

# Resources

#### Effect.pac Roster Expansion System Resources

- [JOJI's site](http://ssbbhack.web.fc2.com/index.html) - As creator of the system, JOJI's site has a plethora of information on the system, including extensive ID lists and guides on how to use the system.
- [Effect.pac ID List](data/effectpac-ids.md) - A list of Effect.pac IDs, including custom banks from this system.