## Overview
* [Prerequisities](#prerequisites)
* [Introduction](#introduction)
* [Basic Config](#basic-config)
  * [Required Parameters](#required-parameters)
  * [Example: Basic Alarm Configuration using Required Parameters](#example-basic-alarm-configuration-using-required-parameters)
* [Advanced Config](#advanced-config)
  * [Optional Parameters](#optional-parameters)
  * [Example: Alarm Configuration Using Optional Parameters](#example-alarm-configuration-using-optional-parameters)
  * [Mini Map Configuration](#mini-map-configuration)
  * [Formatting alarms text](#formatting-alarms-text)
* [How to Enable Discord Webhooks](#how-to-enable-discord-webhooks)

## Prerequisites
This guide assumes

1. You are familiar with [JSON formatting](https://www.w3schools.com/js/js_json_intro.asp)
2. You have read and understood the [Alarms](alarms) Wiki
3. You are comfortable with the layout of `alarms.json`.
4. You are using the latest version of PokeAlarm.

Please familiarize yourself with all of the above before proceeding.

## Introduction

**Discord** is a free voice and text chat app designed specifically for gaming. Available on Windows, Mac OS X, iOS and Android. It is also usable from any Chrome, Firefox or Opera browser.

PokeAlarm offers the following for Discord:

* Custom username for posting
* High resolution icons for pokemon, gym, or pokestop notifications
* Personalized notifications via [Dynamic Text Substitution](Dynamic-Text-Substitution)


## Basic Config

### Required Parameters
The parameters below are required to enable the Discord alarm service:

| Parameters     | Description                             |
|----------------|-----------------------------------------|
| `type`         | Must be `discord`                       |
| `active`       | `True` for alarm to be active           |
| `webhook_url`* | Your Webhook URL for a specific channel |

**Note:** *In PokeAlarm version 3.1, `webhook_url` replaced `api_key`.

### Example: Basic Alarm Configuration using Required Parameters

**Note:** The above below is to be inserted into the alarms section of `alarms.json`. It does not represent the entire `alarms.json` file.

```json
{
	"active":"True",
	"type":"discord",
	"webhook_url":"YOUR_WEBHOOK_URL"
}
```

## Advanced Config

### Optional Parameters
In addition to the required parameters, several optional parameters are available to personalize your notifications.  Below is an example of these optional parameters and how they are incorporated into a functional alarm layout.

These optional parameters are entered at the same level as `"type":"discord"`.

| Parameters         | Description                                  |
|--------------------|----------------------------------------------|
| `startup_message`  | Confirmation post when PokeAlarm initialized |

These optional parameters below are applicable to the `pokemon`, `pokestop`, `gym`, `egg`, and `raid` sections of the JSON file.

| Parameters       | Description                                       | Default                                       |
|------------------|---------------------------------------------------|-----------------------------------------------|
| `webhook_url`    | URL of specific channel name.  Overrides `webhook_url` at Alarm level.  Use to post only
| `disable_embed`  | Disables the body to make one line notifications  | `False`                                       |
| `username`       | Username the bot should post the message as       | `<pkmn>`                                      |
| `icon_url`       | URL path to pokemon icon                          |                                               |
| `avatar_url`     | URL path to pokemon avatar                        |                                               |
| `title`          | Notification text to begin the message            | `A wild <pkmn> has appeared!`                 |
| `url`            | Link to be added to notification text             | `<gmaps>`                                     |
| `body`           | Additional text to be added to the message        | `Available until <24h_time> (<time_left>).`   |
| `content`        | Text before the Discord embed                     |                                               |

*Note: Nidorans will be `nidoranf` or `nidoranm`, Farfetch'd will be `farfetchd`, and Mr. Mime will be `mrmime`.

## Example: Alarm Configuration Using Optional Parameters

**Note:** The code below is to be inserted into the alarms section of `alarms.json`. It does not represent the entire `alarms.json` file.

```json
{
	"active":"True",
	"type":"discord",
	"webhook_url":"YOUR_WEBHOOK_URL",
	"startup_message":"False",
	"pokemon":{
		"webhook_url":"YOUR_WEBHOOK_URL_FOR_POKEMON_CHANNEL",
		"username":"<pkmn>",
		"icon_url*":"<YOUR CUSTOM URL HERE>/<pkmn_id_3>_<form_or_empty>.png",
		"title":"A wild <pkmn> has appeared!",
		"url":"<gmaps>",
		"body":"Available until <24h_time> (<time_left>)."
	},
	"pokestop":{
		"webhook_url":"YOUR_WEBHOOK_URL_FOR_POKESTOP_CHANNEL",
		"username":"Pokestop",
		"icon_url*":"<YOUR CUSTOM URL HERE>/pokestop.png",
		"title":"Someone has placed a lure on a Pokestop!",
		"url":"<gmaps>",
		"body":"Lure will expire at <24h_time> (<time_left>)."
	},
	"gym":{
		"webhook_url":"YOUR_WEBHOOK_URL_FOR_GYM_CHANNEL",
		"username":"Pokemon Gym",
		"icon_url*":"<YOUR CUSTOM URL HERE>/gym_<new_team_id>.png",
		"title":"A Team <old_team> gym has fallen!",
		"url":"<gmaps>",
		"body":"It is now controlled by <new_team>."
	},
	"egg":{
		"webhook_url":"DISCORD_WEBHOOK_URL_FOR_EGG_CHANNEL",
		"username":"Egg",
		"icon_url*":"<YOUR CUSTOM URL HERE>/egg_<raid_level>.png",
		"avatar_url*":"<YOUR CUSTOM URL HERE>/egg_<raid_level>.png",
		"title":"Raid is incoming!",
		"url":"<gmaps>",
		"body":"A level <raid_level> raid will hatch <begin_24h_time> (<begin_time_left>)."
	},
	"raid":{
		"webhook_url":"DISCORD_WEBHOOK_URL_FOR_RAID_CHANNEL",
		"username":"Raid",
		"icon_url*":"<YOUR CUSTOM URL HERE>/<pkmn_id_3>_<form_or_empty>.png",
		"avatar_url*":"<YOUR CUSTOM URL HERE>/egg_<raid_level>.png",
		"title":"Level <raid_level> Raid is available against <pkmn>!",
		"url":"<gmaps>",
		"body":"The raid is available until <24h_time> (<time_left>)."
	}
}
```
**Note:** *THESE LINES ARE USED TO OVERRIDE DEFAULT VALUES. IF YOU DO NOT WISH TO USE CUSTOM IMAGES, DO NOT ADD THESE LINES TO YOUR ALARMS.JSON.

### Mini Map Configuration
![](images/minimap.png)

You can enable a small Google Static Maps image after your post, showing the location of the alarmed pokemon, gym, or pokestop.  This is done by adding the `map` parameter at the Alarm level (which will apply maps for any notification), or individually to the `pokemon`, `pokestop`, `gym`, `egg`, or `raid` sections of your alarm.

Below is an example of enabling the mini map for pokemon.
```json
	"pokemon":{
		"webhook_url":"YOUR_WEBHOOK_URL_FOR_POKEMON_CHANNEL",
		"username":"<pkmn>",
		"title":"A wild <pkmn> has appeared!",
		"url":"<gmaps>",
		"body":"Available until <24h_time> (<time_left>).",
		"map":{
			"enabled":"true",
			"width":"250",
			"height":"125",
			"maptype":"roadmap",
			"zoom":"15"
		}
	},
```

| Parameters     | Description                                       | Default                                       |
|----------------|---------------------------------------------------|-----------------------------------------------|
| `enabled`      | Turns the map on or off                           | `True`                                        |
| `width`        | Width of the map                                  | `250` px                                      |
| `height`       | Height of the map                                 | `150` px                                      |
| `maptype`      | Link to be added to notification text             | `roadmap`                                     |
| `zoom`         | Specifies the zoom of the map                     | `15`                                          |

### Formatting alarms text

Here is a basic guide to apply custom styles to alarm text:

| Style                              | Example                          |
|------------------------------------|----------------------------------|
| `*italics*`                        | *italics*                        |
| `**bold**`                         | **bold**                         |
| `***bold italics***`               | ***bold italics***               |
| `__underline__`                    | __underline__                    |
| `__*underline italics*__`          | __*underline italics*__          |
| `__**underline bold**__`           | __**underline bold**__           |
| `__***underline bold italics***__` | __***underline bold italics***__ |
| `~~Strikethrough~~`                | ~~Strikethrough~~                |

You can see other options in the official Discord information about formatting text [here](https://support.discordapp.com/hc/en-us/articles/210298617-Markdown-Text-101-Chat-Formatting-Bold-Italic-Underline-).

## How to enable Discord webhooks

1. You must have the role permission 'Manage Webhooks', or be an administrator for the server.

2. Go into channel settings, into the Webhooks tab.

3. Click "Create Webhook", 'Save'

4. The webhook URL listed is the key you need.
