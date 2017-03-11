## Overview
* [Prerequisites](#prerequisites)
* [Introduction](#introduction)
* [Gym Filters](#gym-filters)
* [Pokestop Filters](#pokestop-filters)
* [Pokemon Filters](#pokemon-filters)
    * [Pokemon Level Options](#pokemon-level-options)
    * [Specific Pokemon Level Options](#specific-pokemon-level-options)
      * [Example Pokemon Config](#example-pokemon-config)
      * [List of Optional Parameters for Specific Pokemon](#list-of-optional-parameters-for-specific-pokemon)
      * [Example Specific Pokemon Config](#example-specific-pokemon-config)
        * [Multifilters](#multifilters)
* [Final Words](#final-words)
## Prerequisites
This guide assumes:

1. You have a working RocketMap installation
2. You are familiar with [JSON formatting](http://www.w3schools.com/json/default.asp)

## Introduction

**Note:** PokeAlarm version 3.1 contains significant changes to `filters.json` compared to previous versions.

The `filters.json` configuration file filters Pokemon, Gym, and Pokestop notifications so that you receive only the notifications you want.

The basic structure of `filters.json` contains 3 sections:

```
[
	"gyms":{
	    GYM_FILTERS_ARE_HERE
	},
	"pokestops":{
	    POKESTOP_FILTERS_ARE_HERE
	},
	"pokemon":{
	    POKEMON_FILTERS_ARE_HERE
	}
]
```


**Note for location:** To utilize the distance feature of PokeAlarm, set your location set by passing `-l LOCATION` at the command line or adding `location:YOUR_LOCATION` in `config.ini`, located in the `config` directory of your PokeAlarm installation.

**Note for locale:** PokeAlarm will only notify on correctly spelled Pokemon for the selected locale.

## Gym Filters
You may filter on gyms based on teams, and within a minimum / maximum distance from your set location.  Gyms within these parameters will trigger your Gym alarm notification.  For example:
```json
    "gyms":{
        "enabled":"True",
        "ignore_neutral":"False",
        "filters":[
            {
                "from_team":["Valor", "Instinct", "Mystic"], "to_team":["Valor", "Instinct", "Mystic"],
                "min_dist":"0", "max_dist":"inf"
            }
        ]
    },
```
* `"ignore_neutral"`, if set to `"True"`, will prevent the "is now controled by team Neutral" gym notifications. It is recommended to set this value to `True`.

## Pokestop Filters
You may filter on lured pokestops within a minimum and maximum distance from your set location.  Lured pokestops within this range will trigger your Pokestop alarm notification.

```json
    "pokestops":{
        "enabled":"True",
        "filters":{ "min_dist":"0", "max_dist":"inf" }
    },
```

## Pokemon Filters
You may set filters for Pokemon at 2 levels of the `"Pokemon":` section of `filters.json`:

1. Default level
2. Specific Pokemon level, e.g., at the bulbasaur line

Filters at the Default level will act as the defaults for all Pokemon.  Filters at the Specific Pokemon level will only apply to that particular Pokemon.

### Pokemon Level Options
The first 5 parameters - `<min_dist>`, `<max_dist>`, `<min_iv>`, `<max_iv`>, and `<ignore_missing>` - set default limits for all Pokemon based on distance, percent IV, or webhooks missing pokemon stat information. These same values can be overridden at the specific Pokemon level.

Below is an example of the Default level options:

```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"inf", "min_iv":"0", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
```

| Parameter  | Default | Description |
|:-----------|:--------|:------------------------------------------------------------|
| `min_dist` | `"0"`   | Minimum distance from current location by which all Pokemon will trigger configured alarm(s).  Overrides Pokemon level default. Pokemon farther than this value will not trigger configured alarm(s). Can be an integer, e.g., `"1000".
| `max_dist` | `"inf"  | Maximum distance from current location by which the specific Pokemon will trigger configured alarm(s). Overrides Pokemon level default. Pokemon farther than this value will not trigger configured alarm(s). Can be an integer, e.g., `"1000"`, or `"inf"` for unlimited range.
| `min_iv`   | `"0"`   | Minimum percent IV for all Pokemon. 0 to 100.
| `max_iv`   | `"100"` | Maximum percent IV for all Pokemon. 0 to 100.
| `min_atk` | "0" | Value, 0-15, corresponding to the attack IV 
| `max_atk` | "15"| Value, 0-15, corresponding to the attack IV 
| `min_def` | "0" | Value, 0-15, corresponding to the defense IV 
| `max_def` | "15"| Value, 0-15, corresponding to the defense IV 
| `min_sta` | "0" | Value, 0-15, corresponding to the stamina IV 
| `max_sta` | "15"| Value, 0-15, corresponding to the stamina IV
 | `quick_move`   | `"all"` | Quick moves for the specific Pokemon.  Can contain multiple moves for the specific Pokemon, separated by whitespace. Set to `"all"` to notify on any quick moves.  Leaving out this parameter is the equivalent of notifying on all quick moves.
| `charge_move`   | `null` | Charge moves for the specific Pokemon.  Can contain multiple moves for the specific Pokemon, separated by whitespace. Set to `"all"` to notify on any charge moves.  Leaving out this parameter is the equivalent of notifying on all charge moves.
| `moveset` | `null` | Combination of `quick_move` and `charge_move`, useful for filtering on best attacking or defending moves. Format is`"moveset":[ "QUICK_MOVE_NAME/CHARGE_MOVE_NAME" ]`. Example - `"moveset":[ "Dragon Breath/Dragon Claw", "Steel Wing/Dragon Pulse" ]`
| `ignore_missing` | `True` | Prevents PokeAlarm from notifying on Pokemon without moves or IVs.  WARNING: enabling this could potentially result in losing a snorlax, lapras, dragonite, etc., if RocketMap screws up and sends the webhook without info. A better way is to configure your blacklist or whitelist in RocketMap and set the unwanted Pokemon in filters.json to `False`.
| `size` | null| Useful for the tiny Rattata and big Magikarp badges.  Filter with  `"Tiny`, `"Small"`, `"Normal"`, `"Large"`, and `"Big"`
| `ignore_missing` | `True` | Prevents PokeAlarm from notifying on Pokemon without moves or IVs.  WARNING: enabling this could potentially result in losing a snorlax, lapras, dragonite, etc., if RocketMap errors and sends the snorlax webhook without info. A better way is to configure your blacklist or whitelist in RocketMap and set the unwanted Pokemon in filters.json to `False`.
     
### Example Pokemon Level Configs

By default, PokeAlarm will notify on any Pokemon set to `"True"`, at any distance and with any %IV.  A config to notify for any Bulbasaur or Venusaur would look like below:
```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"inf", "min_iv":"0", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":"True",
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```
**Setting Default Distance for all Pokemon.** Let's say we want to be notified of any Pokemon within **5000m** from our current location.  We update `"max_dist"` to accomplish this:
```json
    "pokemon":{
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"0", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":"True",
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```
**Setting Default Minimum IV for all Pokemon.** Now we want to be notified of any **90%** IV Pokemon within **5000m** from our current location.  The `"max_dist"` and `"min_iv"` parameters apply to all Pokemon that are set to `"True"`. Our config would look like below:
```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":"True",
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```
## Specific Pokemon Level Options
At the lower specific Pokemon level, each Pokemon can have a configuration that will override the defaults that was set at the Default level.



### Example Specific Pokemon Config

**Filtering on a maximum range for a specific Pokemon.**  Add a `max_dist` key-value pair to the specific Pokemon.  Remember this will override the `max_dist` at the top `"pokemon":` level.  In the example below, Bulbasaur within 1000m will trigger the alarm.  A Venusaur at any distance will trigger the alarm.
```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":{ "max_dist":"1000" },
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```

**Filtering on minimum %IV for a specific Pokemon.**  Add a `min_iv` key-value pair to the specific Pokemon.  Remember this will override the `min_iv` at the top `"pokemon":` level.  In the example below, a 100% perfect Bulbasaur  will trigger the alarm.  Any Venusaur will trigger the alarm.
```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":{ "min_iv":"100" },
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```

**Filtering on quick and charge moves.** Add the `move_1` and/or `charge_move` key-value pair to the specific Pokemon.  Wrap each move in double quotes.  Separate multiple moves with a comma. In the example below, We want to be notified of Bulbasaur with either Power Whip or Seed Bomb as a charge move. Separate each move by a comma, and wrap the list in brackets `[ ]`. The Pokemon example configuration for Bulbasaur would be as below:

```json
        "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":{ "quick_move": ["Power Whip", "Seed Bomb"] },
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```



**Filtering on a moveset.** A `moveset` is a combination of `move_1` and `charge_move`, useful for filtering on best attacking or defending moves.  Below is an example Pokemon configuration for Bulbasaur with two movesets:

```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":{ "moveset": ["Vine Whip/Seed Bomb", "Tackle/Power Whip"] },
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```

**Filtering on a combination of parameters.** Let's say we want to be notified of any Pokemon with at least 90% IVs within 5000m of our set location. We also want to be notified of 100% IV Bulbasaur within 1000m of our location with either Power Whip or Seed Bomb as a charge move.  We don't want Ivysaur or Charmander.  We do want 90%+ Venusaurs within 5000m. The Pokemon configuration would be as below:
```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur":{ "max_dist":"1000", "min_iv":"100", "charge_move":["Power Whip", "Seed Bomb"] },
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```

**Filtering on multiple combinations of parameter, a.k., "Multifiltering".** You can have multiple.  For example, we want either:

1) A perfect Bulbasaur within 100m that has either Power Whip or Seed Bomb as a charge move
2) Any Bulbasaur within 150m

To accomplish this within the same `filters.json`, use the following as a template:

```json
    "pokemon":{
        "enabled":"True",
        "default": {
            "min_dist":"0", "max_dist":"5000", "min_iv":"90", "max_iv":"100",
            "min_atk": "0", "max_atk":"15", "min_def": "0", "max_def":"15", "min_sta": "0", "max_sta":"15",
            "quick_move": null, "charge_move": null, "moveset": null,
            "size": null, "ignore_missing": "False"
        },
        "Bulbasaur": [
            { "max_dist":"1000", "min_iv":"100", "charge_move":["Power Whip", "Seed Bomb"] },
            { "max_dist":"150" }
        ]
        "Ivysaur":"False",
        "Venusaur":"True",
        "Charmander":"False"
    }
```

**Filtering on size.**
Want those tiny Rattata and big Magikarp badges?  Here's how to add them to your `filters.json`.  (Note, you'll need to use multifiltering or two different filters.json files if you're looking for either high IV or big Magikarp.)
```json
"Rattata":{"size":["Tiny"] },
"Magikarp":{ "size":["Big"] },
```


## Final Words
The `filters.json.example` file contains the entire list of generation 1 and 2 Pokemon, and includes some examples of how the various parameters can be used to fit your needs.  Add the optional key-value pairs for each of your specific Pokemon. Remember that keys such as `max_dist` and `min_iv` set at the specific Pokemon level will override the values of `max_dist` and `min_iv` set at the Default level.
