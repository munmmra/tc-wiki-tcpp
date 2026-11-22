---
title: access_requirement
description: 
published: true
date: 2025-11-16T13:34:47.361Z
tags: database, world, 3.3.5, 3.3.5a, 335, 335a, wotlk
editor: markdown
dateCreated: 2021-08-30T22:02:30.676Z
---

This table contains the access requirements to enter an instance.

## Structure

| Field | Type | Attributes | Key | Null | Default | Extra | Comment |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| [`mapId`](#mapId) | int(10) unsigned | unsigned | PRI | NO | NULL |  |  |
| [`difficulty`](#difficulty) | tinyint(3) unsigned | unsigned | PRI | NO | 0 |  |  |
| [`level_min`](#level_min) | tinyint(3) unsigned | unsigned |  | NO | 0 |  |  |
| [`level_max`](#level_max) | tinyint(3) unsigned | unsigned |  | NO | 0 |  |  |
| [`item`](#item) | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`item2`](#item2) | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`quest_done_A`](#quest_done_A) | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`quest_done_H`](#quest_done_H) | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`completed_achievement`](#completed_achievement) | int(10) unsigned | unsigned |  | NO | 0 |  |  |
| [`heroic_exclusive`](#heroic_exclusive) | tinyint(1) |  |  | YES | 0 |  |  |
| [`comment`](#comment) | text |  |  | YES | NULL |  |  |

&nbsp;
## Description of fields
### mapId
MapID of the map which should have access requirements
References to: [Map.db2](https://wago.tools/db2/Map)
&nbsp;

### difficulty
Difficulty id of the access requirement
References to: [Difficulty.db2](https://wago.tools/db2/Difficulty)
&nbsp;

### level_min
The minimum level that you must be in order to enter the instance.
&nbsp;

### level_max
The maximum level that you can be in order to enter the instance.
&nbsp;

### item
An [item](https://wago.tools/db2/itemsparse) that you must have in your inventory to enter the instance. This item can not be in the bank.
&nbsp;

### item2
A second [item](https://wago.tools/db2/itemsparse) that you must have in your inventory. This item can not be in the bank.
&nbsp;

### quest_done_A
A [quest](/database/master/world/quest_template#id-alt) that you must have completed. This field is only for alliance.
&nbsp;

### quest_done_H
A [quest](/database/master/world/quest_template#id-alt) that you must have completed. This field is only for horde.
&nbsp;

### completed_achievement
An [achievement](https://wago.tools/db2/achievement) that must be completed by the player to enter an instance.
&nbsp;

### heroic_exclusive
?
&nbsp;

### comment
This field is for any comment you want to make about the requirements. It is arbitrary text.
&nbsp;


