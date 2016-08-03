#Pushbullet

**Warning:** Do to the recent changes requiring Pushbullet premium, Pushbullet support may not be continued in the future
## Example Config
```json 
{
    "type":"pushbullet",
    "active":"True",
    "api_key":"YOUR_API_KEY_HERE",
    _"channel":""_
}
```

## Parameters
| Parameters     | Description                            | Required  |
| -------------- |----------------------------------------|:---------:|
| type           | must be 'pushbullet'                   | yes       |
| active         | 'True' for alarm to be active          | yes       |
| api_key        | Your API key                           | yes       |
| channel        | Pushes to this channel instead of user | no        |

Parameters surrounded by red blocks are optional.

## How to get API Key

1. Go to Pushbullet.com and click one of the 'Sign up' options.

2. In the top right corner, click on the letter and select 'My Account'.

3. Scroll down to 'Create Access Token`. Copy this token and place it in api_key parmater. 