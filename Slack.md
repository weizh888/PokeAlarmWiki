## Example Config

```json
{
    "type":"slack",
    "active":"True",
    "api_key":"YOUR_API_KEY_HERE",
    "channel":"#general"
}
```

### Required Parameters
| Parameters     | Description                            |
| -------------- |----------------------------------------|
| type           | must be `pushbullet`                   |
| active         | `True` for alarm to be active          |
| api_key        | Your API key                           |
| channel        | Pushes to this channel instead of user |

### Required Parameters
| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| notify_text    | Notification text to begin the message            | `A wild <pkmn> has appeared!`                 |
| notify_link    | Link to be added to notification text             | `<gmaps>`                                     |
| body_text      | Additional text to be added to the message        | `Available until <24h_time> (<time_left>).`   | 
| username       | Username the bot should post the message as       | `<pkmn>`   | 

## How to get an API Key

1. Go to slack.com. Enter your email address and click 'Create your team'. Follow the instructions to setup and activate your account. 

2. Go to the [create a bot page](https://my.slack.com/services/new/bot). Enter a username and click create.

3. Copy the API Token given. Fill out any more information you want, and click 'Save Integration'.