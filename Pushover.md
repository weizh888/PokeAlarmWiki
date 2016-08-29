
## Basic Config
```json
{
	"active":"True",
	"type":"pushover",
	"app_token":"YOUR_API_KEY",
	"user_key":"DEFAULT_CHANNEL",
}
```

## Advanced Config
```json
{
	"active":"True",
	"type":"pushover",
	"app_token":"YOUR_API_KEY",
	"user_key":"DEFAULT_CHANNEL",
	"startup_message":"True",
	"pokemon":{
		"title":"A wild <pkmn> has appeared!",
		"url":"<gmaps>",
		"url_title":"Google Maps Link",
		"message":"Available until <24h_time> (<time_left>)."
	},
	"pokestop":{
		"title":"Someone has placed a lure on a Pokestop!",
		"url":"<gmaps>",
		"url_title":"Google Maps Link",
		"message":"Lure will expire at <24h_time> (<time_left>)."
	},
	"gym":{
		"title":"A Team <old_team> gym has fallen!",
		"url":"<gmaps>",
		"url_title":"Google Maps Link",
		"message":"It is now controlled by <new_team>."
	}
}
```