## Example Config

<pre>
{
    "type":"telegram",
    "active":"True",
    "api_key":"YOUR_BOT_TOKEN",
    "chat_id":"YOUR_CHAT_ID"
}
</pre>


## Parameters
| Parameters     | Description                            | Required  |
| -------------- |----------------------------------------|:---------:|
| type           | must be 'telegram '                    | yes       |
| active         | 'True' for alarm to be active          | yes       |
| bot_token      | Your Bot Token from Telegram           | yes       |
| chat_id        | Your chat's id from Telegram          | yes       |


## How to get API Key

1. Go to [Telegram Web Client] (https://telegram.org/dl/webogram). Enter your phone number and follow the instructions to create your account. 

2. Talk to the [BotFather] (https://telegram.me/botfather) to create a new bot. Use the `/createbot`command and follow his instructions. It will give you an API Token when you are finished.

3. Start a conversation with your bot. In the top left click on the menu bars, then click create group. Type in the name of the bot you previously created, then click on it when it appears below. Then click next. Type any message to your bot. 

4. Enter your bot_token in to replace the `<BOT_TOKEN_HERE>` in the following url `https://api.telegram.org/bot<BOT_TOKEN_HERE>/getUpdates`. Then go to it, and find the section that says `"chat":{"id":<CHAT_ID>`. This number is your chat_id. 