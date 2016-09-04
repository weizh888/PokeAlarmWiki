## Overview
* [Prerequisites](#prerequities)
* [Introduction](#introduction)
* [Basic Structure of Alarm Configuration File](#basic-structure-of-alarm-configuration-file)
* [Configuring Multiple Different Alarm Services](#configuring-multiple-different-alarm-services)
* [Configuring Multiple of the Same Alarm Services](#configuring-multiple-of-the-same-alarm-services)
* [Editing or Adding Alarms](#editing-or-adding-alarms)
* [Customizing Alerts](#customizing-alerts)
* [Example Alarms Config](#example-alarms-config)
* [Enabling/Disabling Pokemon](#enabling-disabling-pokemon)

## Prerequisites
This guide assumes:

1. You have a working PokemonGo-Map installation
2. You are familiar with [JSON formatting](http://www.w3schools.com/json/default.asp)

## Introduction

In PokeAlarm, an "Alarm" is defined as a supported message service that sends a notification. Slack, Twitter, Telegram, each are considered message service.

PokeAlarm allows you to add as many different supported message services as you'd like (e.g., Slack, Twitter, Telegram), and as many of each message service that you would like (e.g., 3 Slack channels, 10 Twitter feeds, 5 Telegrams.)

You add alarms to the PokeAlarm alarm configuration file, which is `alarms.json` by default.

`alarms.json` is where:

1. Alarms are enable/disabled
2. Notification messages for each alarm are customized
3. Pokemon, gym and pokestop notifications are enabled/disabled



The alarm configuration file follows the JSON format and has 4 sections:

1. `alarms`
2. `pokestops`
3. `gyms`
4. `pokemon`

**Note:** The alarm configuration file is the only file within the PokeAlarm installation that you are **required** to directly edit (`config.ini` file is optional.)  Editing other files in your PokeAlarm installation directory is not supported.

## Basic Structure of Alarm Configuration File
At its most basic, `alarms.json` looks like this:

```json
{
	"alarms":[
	],
	"gyms":{
	},
	"pokestops":{
	},
	"pokemon":{
	}
}
```
Note that there is a pair of square brackets `[]` instead of curly brackets `{}` after `"alarms":`.  This is because PokeAlarm allows you to configure multiple simultaneous alarms.  Also note that a comma `,` follows every set of brackets, except the last in the set (the pair that follows `"pokemon":`).

If we were to add a block of code for an alarm, say, Slack, `alarms.json` would look like this:
```
{
	"alarms":[
		{
			"SLACK_ALARM_CODE_GOES_HERE"
		}
	],
	"gyms":{
	},
	"pokestops":{
	},
	"pokemon":{
	}
}
```
Note that in the above code, new curly brackets `{}` are added between the square brackets `[]`, and that the `SLACK_ALARM_CODE_GOES_HERE` is between the curly brackets.

If we were to add 2 alarms, say, Slack and Twitter, `alarms.json` would look like this:
```
{
	"alarms":[
		{
			"SLACK_ALARM_CODE_GOES_HERE"
		},
		{
			"TWITTER_ALARM_CODE_GOES_HERE"
		}
	],
	"gyms":{
	},
	"pokestops":{
	},
	"pokemon":{
	}
}
```
Note that in the above code, a comma separates the two curly bracket sets between `SLACK_ALARM_CODE_GOES_HERE` and `TWITTER_ALARM_CODE_GOES_HERE`.  Again, note the commas following each of the bracket pairs except the last in a set (after Twitter code block and after pokemon).

The `alarms.json` examples above will not send notifications because it does not enable any alarm types, gym, pokestop, or pokemon to notify. It is just an example a barebones file that follows correct JSON formatting.  A more functional `alarms.json` looks like the code below:

```json
{
	"alarms":[
		{
			"active":"True",
			"type":"slack",
			"api_key":"SLACK_API_KEY"
		}
	],
	"gyms":{
		"To_Valor":"True",
		"To_Mystic":"False",
		"To_Instinct":"False",
		"From_Valor":"False",
		"From_Mystic":"False",
		"From_Instinct":"False"
	},
	"pokestops":{
		"Lured":"True"
	},
	"pokemon":{
		"Lapras":"True",
		"Snorlax":"True",
		"Dragonite":"True"
	}
}
```
The above code enables Slack as the alarm service.  It notifies when:

1. A gym switches to Team Valor
2. Someone places a lure on a pokestop
3. When a lapras, snorlax, or dragonite shows up on your map

Again, note the comma `,` that follows each element, except the last in the list. 

The [`alarms.json.default`](https://github.com/kvangent/PokeAlarm/blob/master/alarms.json.default) file that ships with your PokeAlarm installation is larger than the above examples. (Have a look now.) In [`alarms.json.default`](https://github.com/kvangent/PokeAlarm/blob/master/alarms.json.default), the `gyms`, `pokestops`, and `pokemon` sections already contain the proper options and are set to `False`.  It also already contains the entire list of 151 generation 1 pokemon, also all set to `False`.

What you need to modify in the default `alarms.json` is:
1. Add your desired alarms in the `"Alarms":[],` section, and
2.  Enabled/disable the gyms, pokestops, and pokemon you wish you to be notified.

## Configuring Multiple Different Alarm Services
Coming soon

## Configuring Multiple of the Same Alarm Services
Coming soon
 
## Editing or Adding Alarms
To add, edit, or remove alarms, edit the `alarms.json` file. If you haven't created an `alarms.json` file before, you can make a copy of `alarms.json.{locale}.default` and rename it appropriately.

Pokealarm uses `alarms.json` by default. If you wish to specify a different alarms configuration JSON file, launch PokeAlarm with `python runwebhook.py -c FILENAME`.

Alarms are represented as a list of JSON Objects, inside an array labeled alarms. Each alarm should be surrounded by curly brackets, and the space in between fields should have a comma. Your alarms config should look something like this:
```
"alarms":[
	{
	//ALARM 1 DETAILS
	}, <-----Notice the comma, because there are more alarms to come
	{
	//ALARM 2 DETAILS
	},
	{
	//ALARM 3 DETAILS
	} <----- Last item, so no comma
],
```

Each alarm has required and optional parameters.  Visit the wiki page of the service you are setting up to make sure you have the proper config.

Each alarm setting runs independent of the other alarms, so changes to one alarm do not affect the others (even if they are of the same type).

If is perfectly valid to have any combination of services, including repeats. 

## Customizing Alerts

Most alarms have customizable fields for each alert that allow you to insert your own message. This allows your to override the standard message and provide your own. You may customize as few or as many fields as you want - any field not present in your config will reset to default.

In order to customize an Alert, you must specify what type of alert you want to config: Either `pokemon`, `pokestop`, or `gym`. Each of these has different defaults available. The following is a config where a portion of the Alert has been updated:

```json
{
  "type":"slack",
  "active":"True",
  "api_key":"YOUR_API_KEY_HERE",
	"pokemon":{
		"channel":"Pokemon",
		"username":"<pkmn>",
		"title":"A GIANT <pkmn> jumped out of the grass!",
		"body": "Available until <24h_time> (<time_left>)."
	},
	"gym":{
		"channel":"Gyms",
		"title":"Someone  has placed a lure on a Pokestop!",
		"body":"Better hurry! The lure only has <time_left> remaining!."
	}
}
```
For more information about Dynamic Text Substitutions (the `<text>`), please see the Dynamic Text Substitution wiki. 

For what service has what fields, please check the specific wiki page for that service.

## Example Alarms Config

```json
"alarms":[
	{
		"active": "True",
		"type":"slack",
		"api_key":"YOUR_API_KEY",
		"channel":"#<pkmn>"
	},
	{
		"active": "True",
		"type":"slack",
		"api_key":"YOUR_API_KEY",
		"channel":"#general"
	},
	{
		"active": "False",
		"type":"telegram",
		"bot_token":"YOUR_BOT_TOKEN",
		"chat_id":"YOUR_CHAT_ID"
	}
]
```

Notice that the above config has 3 alarms set up, but only 2 are enabled. This allows you to have alarms set up and ready to go, but only enabled when you want them.

## Enabling/Disabling Pokemon

At the bottom of the default `alarms.json` is the pokemon section is where you would enable/disable/distance-limit pokemon.  It has the list of all 151 generation 1 pokemon.  A portion of this section looks like:
```
	"pokemon":{
		"Bulbasaur":"False",
		"Ivysaur":"False",
		"Venusaur":"False",
```

This is not to be confused with the `"pokemon"` code in the top `"alarms"` section of `alarms.json`. 

Change `"False"` to `"True"` for every pokemon you want an notification.  Visit the wiki article on [Pokemon Configuration](https://github.com/kvangent/PokeAlarm/wiki/Pokemon-Configuration) for more details.