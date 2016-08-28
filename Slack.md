## Example Config

```json
{
    "type":"slack",
    "active":"True",
    "api_key":"YOUR_API_KEY_HERE"
}
```

### Required Parameters
| Parameters     | Description                            |
| -------------- |----------------------------------------|
| type           | must be `slack`                        |
| active         | `True` for alarm to be active          |
| api_key        | Your API key                           |

### Optional Parameters
| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| title          | Notification text to begin the message            | `A wild <pkmn> has appeared!`                 |
| url            | Link to be added to notification text             | `<gmaps>`                                     |
| body           | Additional text to be added to the message        | `Available until <24h_time> (<time_left>).`   | 
| username       | Username the bot should post the message as       | `<pkmn>`                                      | 
| channel        | Send messages to this channel.. `#<pkmn>` pushes to pokemon name* | `#general`                    |
| map            | Specify a json object to describe the map         | See map section for more details              |
*Note: Nidorans will be `nidoranf` or `nidoranm`, Farfetch'd will be `farfetchd`, and Mr. Mime will be `mrmime`. Channels that do not exist (channels cannot be created by bots) will default to general instead.

### Mini Map configuration
```json
{
	"active": "True",
	"type":"slack",
	"api_key":"YOUR_API_KEY",
	"map": { 
		"enabled":"true",
		"width":"250",
		"height":"125",
		"maptype":"roadmap",
		"zoom": "15"
	}
},
```

| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| enabled        | Turns the map on or off                           | `True`                                        |
| width          | Width of the map                                  | `250` px                                      |
| height         | Height of the map                                 | `150` px                                      | 
| maptype        | Link to be added to notification text             | `roadmap`                                     |
| zoom           | Specifies the zoom of the map                     | `15`                                          | 

 
## How to get an API Key

1. Go to slack.com. Enter your email address and click 'Create your team'. Follow the instructions to setup and activate your account. 

2. Go to the [create a bot page](https://my.slack.com/services/new/bot). Enter a username and click create.

3. Copy the API Token given. Fill out any more information you want, and click 'Save Integration'.