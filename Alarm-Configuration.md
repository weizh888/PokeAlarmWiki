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

## Modifying Notification Templates - Dynamic Substitutions
You can now customize your alarms to give any message you prefer, based on what you would like to see. For example, a Pushbullet notification text might be `<pkmn> is <dist> away!`. This would send the alert "Bulbasuar is XXm away" when a Bulbasaur is detected.

The templates for the individual services are located in the alarms folder and use the file structure &lt;service_name&gt;_alarm.py.  

For what fields you have the option to change, please see the specific service.  A list of text substitutions are below:

| text           | Description                            |
| -------------- |----------------------------------------|
| `<id>`         | ID of the alerted pokemon              |
| `<pkmn>`       | Name of the alerted pokemon            |
| `<addr>`       | Nearest street address of the pokemon  |
| `<postal>`     | Postal code of of the pokemon location |
| `<loc>`        | Latitude, Longitude of the pokemon     |
| `<gmaps>`      | Gmaps link to a pin of the pokemon     |
| `<dist>`       | *Distance from set location in meters  |
| `<time_left>`  | Time remaining for the pokemon         |
| `<12h_time>`   | Dissapear time in 12hour format        |
| `<24h_time>`   | Dissapear time in 24hour format        |
| `<dir>`        | Cardinal direction from set location   |
* If no location has been set, dist will always return 0m

### Sample Notification Template

Below is an excerpt of a modified notification template for Pushover.  In this example, we have modified it to use the 12 hour format in the message body, changed some of the wording and added the distance we are from the pokemon (location argument must be called when adding this subsitution, or it will always be set to 0).

Modified alarms/pushover_alarm.py:
```
def __init__(self, settings):
        self.app_token = settings['app_token']
        self.user_key = settings['user_key']
        self.title = settings.get('title',
                "<pkmn> is nearby: <dist>")
        self.url = settings.get('url',
                "<gmaps>")
        self.url_title = settings.get('url',
                "Google Maps Link")
        self.message = settings.get('message',
                "Disappears at <12h_time> (<time_left>).")
        log.info("Pushover Alarm intialized")
        self.send_pushover("PokeAlarm has been activated!")
```