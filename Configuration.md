## Alarms Configuration

To add, edit, or remove alarms, edit the `alarms.json` file. If you haven't created an `alarms.json` file before, you can make a copy of `alarms.json.{locale}.default` and rename is appropriately.

You can have as many or as few alarms as you want, of any combination of services. 

#### Dynamic Substitutions
You can now customize your alarms to give any message you prefer, based on what you would like to see. For example, a Pushbullet notification text might be `<pkmn> is <dist> away!`. This would send the alert "Bulbasuar is XXm away" when a Bulbasaur is detected.

 For what fields you have the option to change, please see the specific alarm.  A list of text substitutions are below:

| text           | Description                            |
| -------------- |----------------------------------------|
| <id>           | ID of the alerted pokemon              |
| <pkmn>         | Name of the alerted pokemon            |
| <addr>         | Nearest street address of the pokemon  |
| <loc>          | Latitude, Longitude of the pokemon     |
| <gmaps>        | Gmaps link to a pin of the pokemon     |
| <dist>         | *Distance from set location in meters  |
| <time_left>    | Time remaining for the pokemon         |
| <12h_time>     | Dissapear time in 12hour format        |
| <24h_time>     | Dissapear time in 24hour format        |

## Example Alarms Config

```json
"alarms":[
		{
			"active": "True",
			"type":"slack",
			"api_key":"YOUR_API_KEY",
			"channel":"#general"
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

