To add, edit, or remove alarms, edit the `alarms.json` file. If you haven't created an `alarms.json` file before, you can make a copy of `alarms.json.{locale}.default` and rename is appropriately.

You can have as many or as few alarms as you want, of any combination of services. 

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