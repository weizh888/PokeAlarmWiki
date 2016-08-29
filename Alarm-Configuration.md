## About Configuration Files
To add, edit, or remove alarms, edit the `alarms.json` file. If you haven't created an `alarms.json` file before, you can make a copy of `alarms.json.{locale}.default` and rename it appropriately.

If you wish to specify an alarms configuration, you can use the `-c FILENAME` parameter to specify the location of the alarms configuration file you want to use. 
 
Alarms should be provided in JSON format. It is highly suggested that you a [JSON Editor](http://www.jsoneditoronline.org/) to check for errors.. 

## Editing or Adding Alarms

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

Each alarm has required and optional parameters, so make sure you check the service you are setting up to make sure you have the proper config.

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
		"icon_url" : "https://raw.githubusercontent.com/kvangent/PokeAlarm/master/icons/<id>.png",
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
For more information about Dynamic Text Substitutions (the <text>), please see the specific wiki page. 

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