## Overview
* [Prerequisites](#prerequisites)
* [Introduction](#introduction)
* [Pokemon Level Options](#pokemon-level-options)
* [Specific Pokemon Level Options](#specific-pokemon-level-options)
  * [Example Pokemon Config](#example-pokemon-config)
  * [List of Optional Parameters for Specific Pokemon](#list-of-optional-parameters-for-specific-pokemon)
  * [Example Specific Pokemon Config](#example-specific-pokemon-config)
* [Final Words](#final-words)
## Prerequisites
This guide assumes:

1. You have a working PokemonGo-Map installation
2. You are familiar with [JSON formatting](http://www.w3schools.com/json/default.asp)

## Introduction

In the `alarms.json` configuration file, PokeAlarm can notify on a desired set of Pokemon.  This may be based on distance from your set location, percent IV, or moveset.  Editing is done in the **top level** `"pokemon":` section of the `alarms.json` configuration file.

It is easy to confuse the `"pokemon"` top level key, described in this article, with the `"pokemon"` key at the alarm level described in the [Alarm Configuration](https://github.com/kvangent/PokeAlarm/wiki/Alarm-Configuration) wiki article.  Recall the structure of `alarms.json`:

```
{
	"alarms":[
		{
			ALARM_CODE_GOES_HERE
		}
	],
	"gyms":{
	},
	"pokestops":{
	},
	"pokemon":{
		LIST_OF_POKEMON_IS_HERE
	}
}
```

Here, we will be configuring the list of pokemon to notify, so please ensure that you are editing the correct section of your `alarms.json` file.

**Note for location:** To utilize the distance feature of PokeAlarm, set your location set by passing `-l LOCATION` at the command line or adding `location:YOUR_LOCATION` in `config.ini`, located in the `config` directory of your PokeAlarm installation.

**Note for locale:** PokeAlarm will only notify on correctly spelled Pokemon for the selected locale.

## Pokemon Level Options
At the top `"Pokemon"` level, two parameters are available to set default limits for all Pokemon based on distance and/or percent IV.  These values can be overridden at the specific Pokemon level.
 
| Parameter     | Default | Desecription                                          |
|:--------------|:--------|-------------------------------------------------------|
| `max_dist`    | `"inf"` | Default maximum range from current location for all Pokemon.  Pokemon farther than this value will not trigger configured alarm(s). Can be numeric, e.g., `"1000"`, or `"inf"` for unlimited range.                                                      |
| `min_iv`      | `"0"`   | Default minimum percent IV for all Pokemon. 0 to 100. |

### Example Pokemon Config

By default, PokeAlarm will notify on any Pokemon set to `"True"`, regardless of distance or %IV.  A config to notify for Bulbasaur and Venusaur would look like below:
```json
	"pokemon":{
		"max_dist":"inf",
		"min_iv":"0",
		"Bulbasaur":"True",
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```
**Setting Default Distance for all Pokemon.** Let's say we want to be notified of any Pokemon within **5000m** from our current location.  We update `"max_dist"` to accomplish this:
```json
	"pokemon":{
		"max_dist":"5000",
		"min_iv":"0",
		"Bulbasaur":"True",
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```
**Setting Default Minimum IV for all Pokemon.** Now we want to be notified of any **90%** IV Pokemon within **5000m** from our current location.  The `"max_dist"` and `"min_iv"` parameters apply to all Pokemon that are set to `"True"`. Our config would look like below:
```json
	"pokemon":{
		"max_dist":"5000",
		"min_iv":"90",
		"Bulbasaur":"True",
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```
## Specific Pokemon Level Options
At the lower specific Pokemon level, each Pokemon can have a configuration that will override the default `max_dist` and `min_iv` that was set at the top Pokemon level.  Each of these keys below are optional, i.e., all 4 keys do not need to be included for each specific pokemon.

### List of Optional Parameters for Specific Pokemon
| Parameter  | Default | Description                                                         |
|:-----------|:--------|:------------------------------------------------------------|
| `max_dist` |         | Maximum distance from current location by which the specific Pokemon will trigger configured alarm(s). Overrides Pokemon level default. Pokemon farther than this value will not trigger configured alarm(s). Can be an integer, e.g., `"1000"`, or `"inf"` for unlimited range.                                          |
| `min_iv`   |         | Minimum percent IV for all Pokemon. 0 to 100.  Overrides Pokemon level default. |
| `move_1`   | `"all"` | Quick moves for the specific Pokemon.  Can contain multiple moves for the specific Pokemon, separated by whitespace. Set to `"all"` to notify on any quick moves.  Leaving out this parameter is the equivalent of notifying on all quick moves.
| `move_2`   | `"all"` | Charge moves for the specific Pokemon.  Can contain multiple moves for the specific Pokemon, separated by whitespace. Set to `"all"` to notify on any charge moves.  Leaving out this parameter is the equivalent of notifying on all charge moves.
| `True`     || Notifies on all occurrences of the specific Pokemon.  Equivalent to `{"max_dist":"inf", "min_iv":"0", "move_1":"all", "move_2":"all"}`
| `False`    || Disables all notifications for the specific Pokemon.

### Example Specific Pokemon Config

**Setting maximum range for a specific Pokemon.**  Add a `max_dist` key-value pair to the specific Pokemon.  Remember this will override the `max_dist` at the top `"pokemon":` level.  In the example below, Bulbasaur within 1000m will trigger the alarm.  Any Venusaur will trigger the alarm.
```json
	"pokemon":{
		"max_dist":"inf",
		"min_iv":"0",
		"Bulbasaur":{ "max_dist":"1000" },
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```

**Setting minimum %IV for a specific Pokemon.**  Add a `min_iv` key-value pair to the specific Pokemon.  Remember this will override the `min_iv` at the top `"pokemon":` level.  In the example below, a 100% perfect Bulbasaur  will trigger the alarm.  Any Venusaur will trigger the alarm.
```json
	"pokemon":{
		"max_dist":"inf",
		"min_iv":"0",
		"Bulbasaur":{ "min_iv":"100" },
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```

**Setting moves.** Add the `move_1` and/or `move_2` key-value pair to the specific Pokemon.  Separate multiple moves with a whitespace. In the example below, We want to be notified of Bulbasaur with either Power Whip or Seed Bomb as a charge move.  The Pokemon configuration would be as below:

```json
	"pokemon":{
		"max_dist":"inf",
		"min_iv":"0",
		"Bulbasaur":{ "move_1":"all", "move_2":"Power Whip Seed Bomb" },
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```
or
```json
	"pokemon":{
		"max_dist":"inf",
		"min_iv":"0",
		"Bulbasaur":{ "move_2":"Power Whip Seed Bomb" },
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```

**Setting a combination of parameters.** Let's say we want to be notified of any Pokemon with at least 90% IVs within 5000m of our set location. We also want to be notified of 100% IV Bulbasaur within 1000m of our location with either Power Whip or Seed Bomb as a charge move.  Finally we want to be notified of any Venusaur. The Pokemon configuration would be as below:

```json
	"pokemon":{
		"max_dist":"5000",
		"min_iv":"90",
		"Bulbasaur":{ "max_dist":"1000", "min_iv":"100", "move_1":"all", "move_2":"Power Whip Seed Bomb" },
		"Ivysaur":"False",
		"Venusaur":"True",
		"Charmander":"False"
	}
```
## Final Words
The top level Pokemon section in the default `alarm.json` already contains the entire list of generation 1 Pokemon.  It is up to your to add the optional key-value pairs for each of your specific Pokemon. Remember that `max_dist` and `min_iv` set at the specific Pokemon level will override the values of `max_dist` and `min_iv` set at the top Pokemon level.