## Example Config

<pre>
{
    "type":"slack",
    "active":"True",
    "api_key":"YOUR_API_KEY_HERE",
    "channel":""
}
</pre>

## Parameters
| Parameters     | Description                            | Required  |
| -------------- |----------------------------------------|:---------:|
| type           | must be 'pushbullet'                   | yes       |
| active         | 'True' for alarm to be active          | yes       |
| api_key        | Your API key                           | yes       |
| channel        | Pushes to this channel instead of user | yes       |

## How to get an API Key

1. Go to slack.com. Enter your email address and click 'Create your team'. Follow the instructions to setup and activate your account. 

2. Go to the [create a bot page](https://my.slack.com/services/new/bot). Enter a username and click create.

3. Copy the API Token given. Fill out any more information you want, and click 'Save Integration'.