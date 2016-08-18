You can now customize your alarms to give any message you prefer, based on what you would like to see. For example, a Pushbullet notification text might be `<pkmn> is <dist> away!`. This would send the alert "Bulbasuar is XXm away" when a Bulbasaur is detected.

The templates for the individual services are located in the alarms folder and use the file structure &lt;service_name&gt;_alarm.py.  

For what fields (title, message, etc) you have the option to change, please see the file for the specific service.  A list of text substitutions are below:

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



### Sample Notification Template - Slack

Below is notification template for Slack.  In this example of **alarm.json**, we want one active alarm, Slack.  Let's say that a dratini spawns nearby.  You want PokeAlarm to post to your Slack **#general** channel with the format below:

>Dratini (#147) at 830 5th Avenue 10065 (328m SW) until 17:40:37 (13m 57s remaining)!

In other words, there is a dratini, pokemon number 147, at the given address, 328 meters southwest of your stated location when you launched `runwebhook.py` _(assuming you ran with the `-l` argument and provided an address or coordinates)_.  It will be there until 17:40:37 (5:40pm), and you have 13 minutes and 57 seconds to catch it.

To use this format, edit the beginning of your **alarms.json** like so, near the top where `"alarms"` is:

```
    "alarms":[
        {
            "active": "True",
            "type":"slack",
            "api_key":"YOUR_SLACK_API_KEY_GOES_HERE",
            "channel":"#general",
            "title":"<pkmn> (#<id>) at <addr> <postal>",
            "url":"<gmaps>",
            "body":"(<dist> <dir>) until <24h_time> (<time_left> remaining)!"
        }
    ],
```

From above, we've taken advantage of the `<pkmn>`, `<id>`, `<addr>`, `<postal>`, `<gmaps>`, `<dist>`, `<dir>`, `<24h_time>`, and `<time_left>` variables to customize our notification message of the nearby dratini.

* Add your own [Slack API Key](https://get.slack.help/hc/en-us/articles/215770388-Creating-and-regenerating-API-tokens) after `"api_key"`.
* Change "general" in `"Channel":"#general"` to whatever channel you'd like PokeAlarm to post to.
* Edit the` "title"` key to whatever you'd like, using the above text substitutions to customize your messages.
* The `"url"` key will hyperlink your title to google maps directions.
* The `"body"` key is additional text in slack that will not be hyperlinked.
* Be conscious about quotes and commas! 

Great.  Now that you have your formatting perfect, you want to handpick your pokemon to be notified of.  You can see in the pokemon list below that some are set to `"True"` (Lapras, Kabutops) while others are set to a numeric value, e.g. `"75"` (eevee) or `"1000"` (dragonite, etc.) The numeric values indicate to PokeAlarm that you want to be notified only if that pokemon is within x meters of a given location (again, assuming `python ./runwebhook.py -l 'your location'`).  If you don't supply a location then any of the pokemon in the list with numeric values default to `"True"`, and you'll get notified of that Eevee and Dragonite, no matter how far away.


Below is a complete **alarms.json** for Slack:

```
{
	"alarms":[
		{
			"active": "True",
			"type":"slack",
			"api_key":"YOUR_SLACK_API_KEY_GOES_HERE",
			"channel":"#general",
			"title":"<pkmn> (#<id>) at <addr> <postal>",
			"url":"<gmaps>",
			"body":"(<dist> <dir>) until <24h_time> (<time_left> remaining)!"
		}
	],
	"pokemon":{
		"Bulbasaur":"75",
		"Ivysaur":"75",
		"Venusaur":"1000",
		"Charmander":"75",
		"Charmeleon":"75",
		"Charizard":"1000",
		"Squirtle":"75",
		"Wartortle":"75",
		"Blastoise":"1000",
		"Caterpie":"False",
		"Metapod":"False",
		"Butterfree":"False",
		"Weedle":"False",
		"Kakuna":"False",
		"Beedrill":"False",
		"Pidgey":"False",
		"Pidgeotto":"False",
		"Pidgeot":"False",
		"Rattata":"False",
		"Raticate":"False",
		"Spearow":"False",
		"Fearow":"False",
		"Ekans":"False",
		"Arbok":"75",
		"Pikachu":"75",
		"Raichu":"100",
		"Sandshrew":"False",
		"Sandslash":"75",
		"Nidoran♀":"False",
		"Nidorina":"False",
		"Nidoqueen":"75",
		"Nidoran♂":"False",
		"Nidorino":"False",
		"Nidoking":"75",
		"Clefairy":"False",
		"Clefable":"75",
		"Vulpix":"75",
		"Ninetales":"75",
		"Jigglypuff":"False",
		"Wigglytuff":"75",
		"Zubat":"False",
		"Golbat":"False",
		"Oddish":"False",
		"Gloom":"75",
		"Vileplume":"75",
		"Paras":"False",
		"Parasect":"75",
		"Venonat":"False",
		"Venomoth":"75",
		"Diglett":"False",
		"Dugtrio":"75",
		"Meowth":"False",
		"Persian":"75",
		"Psyduck":"False",
		"Golduck":"75",
		"Mankey":"False",
		"Primeape":"False",
		"Growlithe":"False",
		"Arcanine":"1000",
		"Poliwag":"False",
		"Poliwhirl":"75",
		"Poliwrath":"1000",
		"Abra":"False",
		"Kadabra":"False",
		"Alakazam":"1000",
		"Machop":"False",
		"Machoke":"75",
		"Machamp":"1000",
		"Bellsprout":"False",
		"Weepinbell":"75",
		"Victreebel":"75",
		"Tentacool":"False",
		"Tentacruel":"75",
		"Geodude":"False",
		"Graveler":"75",
		"Golem":"75",
		"Ponyta":"75",
		"Rapidash":"75",
		"Slowpoke":"75",
		"Slowbro":"False",
		"Magnemite":"False",
		"Magneton":"75",
		"Farfetch'd":"False",
		"Doduo":"False",
		"Dodrio":"75",
		"Seel":"False",
		"Dewgong":"False",
		"Grimer":"False",
		"Muk":"False",
		"Shellder":"False",
		"Cloyster":"75",
		"Gastly":"False",
		"Haunter":"75",
		"Gengar":"75",
		"Onix":"75",
		"Drowzee":"False",
		"Hypno":"False",
		"Krabby":"False",
		"Kingler":"75",
		"Voltorb":"False",
		"Electrode":"False",
		"Exeggcute":"False",
		"Exeggutor":"75",
		"Cubone":"False",
		"Marowak":"False",
		"Hitmonlee":"False",
		"Hitmonchan":"False",
		"Lickitung":"False",
		"Koffing":"False",
		"Weezing":"False",
		"Rhyhorn":"False",
		"Rhydon":"False",
		"Chansey":"1000",
		"Tangela":"False",
		"Kangaskhan":"False",
		"Horsea":"False",
		"Seadra":"False",
		"Goldeen":"False",
		"Seaking":"75",
		"Staryu":"False",
		"Starmie":"75",
		"Mr. Mime":"False",
		"Scyther":"False",
		"Jynx":"False",
		"Electabuzz":"False",
		"Magmar":"False",
		"Pinsir":"False",
		"Tauros":"False",
		"Magikarp":"False",
		"Gyarados":"1000",
		"Lapras":"True",
		"Ditto":"False",
		"Eevee":"75",
		"Vaporeon":"1000",
		"Jolteon":"1000",
		"Flareon":"1000",
		"Porygon":"1000",
		"Omanyte":"1000",
		"Omastar":"1000",
		"Kabuto":"1000",
		"Kabutops":"True",
		"Aerodactyl":"1000",
		"Snorlax":"1000",
		"Articuno":"1000",
		"Zapdos":"1000",
		"Moltres":"1000",
		"Dratini":"1000",
		"Dragonair":"1000",
		"Dragonite":"1000",
		"Mewtwo":"1000",
		"Mew":"1000"
	}
}
```