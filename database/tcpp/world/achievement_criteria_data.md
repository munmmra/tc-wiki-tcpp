---
title: achievement_criteria_data
description: ''
tags: database, world, 3.3.5, 3.3.5a, 335, 335a, wotlk
published: true
editor: markdown
date: 2025-12-15T00:34:46.161Z
dateCreated: 2021-08-30T22:02:33.368Z
---

This table contains the data that a player needs to obtain / complete in order to receive a given achievement.

## Structure

| Field | Type | Attributes | Key | Null | Default | Extra | Comment |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| [`criteria_id`](#criteria_id)  | int(11) |  | PRI | NO | NULL |  |  |
| [`type`](#type)  | tinyint(3) unsigned | unsigned | PRI | NO | 0 |  |  |
| [`value1`](#value1)  | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`value2`](#value2)  | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`ScriptName`](#ScriptName)  | varchar(64) |  |  | NO | NULL |  |  |

&nbsp;
## Description of fields

### criteria_id
This is the [AchievementCriteria ID](/files/DBC/335/achievement_criteria#id-alt).
&nbsp;

### type
Depending on this value, it will determine how **value1** and **value2** are used.

Depending on this value, it will determine how value1 and value2 are used.
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_NONE (0)</summary>

|value1|value2|
| :-- | :-- |
| 0 | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_CREATURE (1)</summary>

|value1|value2|
| :-- | :-- |
| [creature_template.entry](#creature_template) | 0|

</details>

<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_PLAYER_CLASS_RACE (2)</summary>

|value1|value2|
| :-- | :-- |
| [ChrClass ID](https://trinitycore.info/files/DBC/335/chrclasses#id-alt) | [ChrRace ID](https://trinitycore.info/files/DBC/335/chrraces#id-alt) |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_PLAYER_LESS_HEALTH (3)</summary>

|value1|value2|
| :-- | :-- |
| The percentage of health that the target must reach | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_PLAYER_DEAD (4) </summary>

|value1|value2|
| :-- | :-- |
| own_team (0, 1) | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_AURA (5) </summary>

|value1|value2|
| :-- | :-- |
| The [Spell ID](https://trinitycore.info/files/DBC/335/spell#id-alt) | Effect Index of the aura |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_AREA (6) </summary>

|value1|value2|
| :-- | :-- |
| [AreaTable ID](https://trinitycore.info/files/DBC/335/areatable#id-alt) | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_AURA (7) </summary>

|value1|value2|
| :-- | :-- |
| The [Spell ID](https://trinitycore.info/files/DBC/335/spell#id-alt) of the aura that must be on the target | Effect Index of the aura |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_VALUE (8) </summary>

|value1|value2|
| :-- | :-- |
| Value to compare needed to attain achievement | [enum ComparisonType](https://github.com/TrinityCore/TrinityCore/blob/3.3.5/src/common/Utilities/Util.h#L505-L513) |

value2: options
| ID | Form | Name | Comment|
| :--- | :--- | :--- | :--- |
| 0 | == | COMP_TYPE_EQ	| amount must be equal to value1 |
| 1	| > | COMP_TYPE_HIGH | amount must be higher than value1 |
| 2	| < | COMP_TYPE_LOW | amount must be lower than value1 |
| 3	| >= | COMP_TYPE_HIGH_EQ | amount must be higher or equal to value1 |
| 4	| <= | COMP_TYPE_LOW_EQ | amount must be lower or equal to value1 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_LEVEL (9) </summary>

|value1|value2|
| :-- | :-- |
| The minimum level of the target. | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_GENDER (10) </summary>

|value1|value2|
| :-- | :-- |
| [enum Gender] | 0 |

value1: options
| ID | Name |
| :-- | :-- |
| 0 | GENDER_MALE |
| 1 | GENDER_FEMALE |
| 2 | GENDER_NONE |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_SCRIPT (11) </summary>

|value1|value2|
| :-- | :-- |
| 0 | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_MAP_DIFFICULTY (12) </summary>

|value1|value2|
| :-- | :-- |
| [enum Difficulty] | 0 |

value1: options
| Value | Name |
| :-- | :-- |
| 0 | RAID_DIFFICULTY_10MAN_NORMAL / DUNGEON_DIFFICULTY_NORMAL / REGULAR_DIFFICULTY |
| 1 | RAID_DIFFICULTY_25MAN_NORMAL / DUNGEON_DIFFICULTY_HEROIC |
| 2 | RAID_DIFFICULTY_10MAN_HEROIC |
| 3 | RAID_DIFFICULTY_25MAN_HEROIC |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_MAP_PLAYER_COUNT (13) </summary>

|value1|value2|
| :-- | :-- |
| count | 0 |

"with less than %u people in the zone"

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_T_TEAM (14) </summary>

|value1|value2|
| :-- | :-- |
| The target must be on this team: [enum Team ](https://github.com/TrinityCore/TrinityCore/blob/e490cad2b0cb538c554006a7a8842b39f7ca143e/src/server/shared/SharedDefines.h#L851-L861) (a [Faction ID](https://trinitycore.info/files/DBC/335/faction#id)) | 0 |

value1: options
| ID | Name |
| :-- | :-- |
| 67 | HORDE |
| 469 | ALLIANCE |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_DRUNK (15) </summary>

|value1|value2|
| :-- | :-- |
| How drunk the player must be: [enum DrunkenState](https://github.com/TrinityCore/TrinityCore/blob/d7329e3d3a713404d8ecbd91ae5f988fd143b793/src/server/game/Entities/Player/Player.h#L334-L340) | 0 |

value1: options 
| ID | Name |
| :-- | :-- |
| 0 | DRUNKEN_SOBER|
| 1	| DRUNKEN_TIPSY|
| 2	| DRUNKEN_DRUNK|
| 3 | DRUNKEN_SMASHED|

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_HOLIDAY (16) </summary>

|value1|value2|
| :-- | :-- |
| [Holiday ID.](https://trinitycore.info/files/DBC/335/holidays#id-alt) Must be an active holiday | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_BG_LOSS_TEAM_SCORE (17) </summary>

|value1|value2|
| :-- | :-- |
| min. score | max. score |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_INSTANCE_SCRIPT (18) </summary>

|value1|value2|
| :-- | :-- |
| 0 |0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_EQUIPPED_ITEM (19) </summary>

|value1|value2|
| :-- | :-- |
| [item_template.ItemLevel](https://trinitycore.info/database/335/world/item_template#itemlevel) | [item_template.Quality](https://trinitycore.info/database/335/world/item_template#quality) |

for equipped item in slot to check item level and quality<br>
nota: la tabla item_template no esta en tcpp

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_MAP_ID (20) </summary>

|value1|value2|
| :-- | :-- |
| Player must be on [Map ID](https://trinitycore.info/files/DBC/335/map#id-alt) | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_PLAYER_CLASS_RACE (21) </summary>

|value1|value2|
| :-- | :-- |
| [ChrClass ID](https://trinitycore.info/files/DBC/335/chrclasses#id-alt) | [ChrRace ID](https://trinitycore.info/files/DBC/335/chrraces#id-alt) |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_NTH_BIRTHDAY (22) </summary>

|value1|value2|
| :-- | :-- |
| N | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_KNOWN_TITLE (23) </summary>

|value1|value2|
| :-- | :-- |
| [CharTitle ID](https://trinitycore.info/files/DBC/335/chartitles#id-alt) | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_GAME_EVENT (24) </summary>

|value1|value2|
| :-- | :-- |
| [game_event.eventEntry](#game_event) | 0 |

</details>
<details><summary>ACHIEVEMENT_CRITERIA_DATA_TYPE_S_ITEM_QUALITY (25) </summary>

|value1|value2|
| :-- | :-- |
| [item_template.Quality](https://trinitycore.info/database/335/world/item_template#quality) | 0 |

nota: la tabla item_template no esta en tcpp
</details>

&nbsp;

### ScriptName
The ScriptName for when scripting it in the core.
&nbsp;
