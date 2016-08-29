
## Basic Config
```json
{
	"active":"True",
	"type":"pushbullet",
	"api_key":"YOUR_API_KEY"
}
```

## Advanced Config
```json
{
	"active":"True",
	"type":"pushbullet",
	"api_key":"YOUR_API_KEY",
	"channel":"DEFAULT_CHANNEL",
	"pokemon":{
		"title":"A wild <pkmn> has appeared!",
		"url":"<gmaps>",
		"body":"Available until <24h_time> (<time_left>).",
		"channel":"OVERRIDES_DEFAULT_CHANNEL"
	},
	"pokestop":{
		"title":"Someone has placed a lure on a Pokestop!",
		"url":"<gmaps>",
		"body":"Lure will expire at <24h_time> (<time_left>).",
		"channel":"OVERRIDES_DEFAULT_CHANNEL"
	},
	"gym":{
		"title":"A Team <old_team> gym has fallen!",
		"url":"<gmaps>",
		"body":"It is now controlled by <new_team>.",
		"channel":"OVERRIDES_DEFAULT_CHANNEL"
	}
}
```



**------ Everything below this line is possibly outdated. Please refrain from opening issue's for incorrect information below this line ------**

### Required Parameters

| Parameters     | Description                            |
| -------------- |----------------------------------------|
| type           | must be `pushbullet`                   |
| active         |`True` for alarm to be active           |
| api_key        | Your Pushbullet API key                |

### Optional Parameters
| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| channel        | Channel tag of the target channel                 | Sends to all devices                          |
| title          | Notification title  attached to the push          | `A wild <pkmn> has appeared!`                 |
| url            | Link to be attached to the push                   | `<gmaps>`                                     |
| body           | Message attched to the push                       | `Available until <24h_time> (<time_left>).`   |                                  

For more information on text substitutions, please see the main configuration page.

## How to get an API Key

1. Go to Pushbullet.com and click one of the 'Sign up' options.

2. In the top right corner, click on the letter and select 'My Account'.

3. Scroll down to 'Create Access Token`. Copy this token and place it in api_key parmater. 