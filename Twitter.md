**Warning:** Do to the recent changes requiring Pushbullet Pro for API usage, Pushbullet support may not be continued in the future.
## Example Config
```json
{
	"active": "False",
	"type": "twitter",
	"access_token": "YOUR_ACCESS_TOKEN",
	"access_secret": "YOUR_ACCESS_SECRET",
	"consumer_key": "YOUR_CONSUMER_KEY",
	"consumer_secret": "YOUR_CONSUMER_SECRET"
}
```

### Required Parameters

| Parameters     | Description                            |
| -------------- |----------------------------------------|
| type           | must be `twitter`                      |
| active         |`True` for alarm to be active           |
| access_token   | Your twitter access token              |
| access_secret  | Your twitter access secret             |
| consumer_key   | Your twitter consumer key              |
| consumer_secret| Your twitter consumer secret           |

### Optional Parameters
| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| message        | Message to post as status                         | `A wild <pkmn> has appeared! Available until <24h_time> (<time_left>). <gmaps>`                      |
                                

For more information on text substitutions, please see the main configuration page.

## How to get an API Key

Coming soon...