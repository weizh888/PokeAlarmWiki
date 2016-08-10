## Example Config

```json
{
    "type":"telegram",
    "active":"True",
    "api_key":"YOUR_BOT_TOKEN",
    "chat_id":"YOUR_CHAT_ID"
}
```


### Required Parameters
| Parameters     | Description                            |
| -------------- |----------------------------------------|
| type           | must be `telegram`                     |
| active         | `True` for alarm to be active          |
| bot_token      | Your Bot Token from Telegram           |
| chat_id        | Your chat's id from Telegram           |

### Optional Parameters
| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| header         | Header text for the message                       | `A wild <pkmn> has appeared!`                 |
| body     | Additional text to be added to the message              | `"<gmaps> \n Available until <24h_time> (<time_left>)."`| 
| send_map | Pokemon minimap in alerts            | True | 

## How to get API Key

1. Go to [Telegram Web Client] (https://telegram.org/dl/webogram). Enter your phone number and follow the instructions to create your account. 

2. Talk to the [BotFather] (https://telegram.me/botfather) to create a new bot. Use the `/newbot`command and follow his instructions. It will give you an API Token when you are finished.

3. Start a conversation with your bot. In the top left click on the menu bars, then click create group. Type in the name of the bot you previously created, then click on it when it appears below. Then click next. Type any message to your bot. 

4. Enter your bot_token in to replace the `<BOT_TOKEN_HERE>` in the following url `https://api.telegram.org/bot<BOT_TOKEN_HERE>/getUpdates`. Then go to it, and find the section that says `"chat":{"id":<CHAT_ID>`. This number is your chat_id. 


## How to create a custom channel

1. Create a Public Channel (Currently doesn't work from the web app).

2. Add your bot as an administrator for the channel.

3. The chat_id for your bot will be `@channel_url`.