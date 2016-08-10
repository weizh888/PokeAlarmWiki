**Warning:** Do to the recent changes requiring Pushbullet Pro for API usage, Pushbullet support may not be continued in the future.
## Example Config
```json
{
    "type":"pushbullet",
    "active":"True",
    "api_key":"YOUR_API_KEY_HERE"
}
```

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