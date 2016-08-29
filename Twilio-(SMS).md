
## Basic Config
```json
{
	"active": "True",
	"type":"twilio",
	"account_sid":"YOUR_API_KEY",
	"auth_token":"YOUR_AUTH_TOKEN",
	"from_number":"YOUR_FROM_NUM",
	"to_number":"YOUR_TO_NUM"
}
```

## Advanced Config
```json
{
	"active": "True",
	"type":"twilio",
	"account_sid":"YOUR_API_KEY",
	"auth_token":"YOUR_AUTH_TOKEN",
	"from_number":"YOUR_FROM_NUM",
	"to_number":"YOUR_TO_NUM",
	"pokemon":{
		"from_number":"YOUR_FROM_NUM",
		"to_number":"YOUR_TO_NUM",
		"message": "A wild <pkmn> has appeared! <gmaps> Available until <24h_time> (<time_left>).",
	},
	"pokestop":{
		"from_number":"YOUR_FROM_NUM",
		"to_number":"YOUR_TO_NUM",
		"message": "Someone has placed a lure on a Pokestop! <gmaps> Lure will expire at <24h_time> (<time_left>).",
	},
	"gym":{
		"from_number":"YOUR_FROM_NUM",
		"to_number":"YOUR_TO_NUM",
		"message": "A Team <old_team> gym has fallen! It is now controlled by <new_team>. <gmaps>",
	}
}
```



**------ Everything below this line is possibly outdated. Please refrain from opening issues for incorrect information below this line ------**

### Required Parameters
| Parameters     | Description                            | 
| -------------- |----------------------------------------|
| type           | must be 'twilio'                       |
| active         | 'True' for alarm to be active          |
| account_sid    | Your Account SID from Twilio           |
| auth_token     | Your Auth Token from Twilio            |
| from_number    | Your Twilio number to send from        |
| to_number      | Your number to receive texts from      |


### Optional Parameters
| Parameters     | Description                                       | Default                                       |
| -------------- |---------------------------------------------------|-----------------------------------------------|
| message   | Text message to be sent via Twilio                | "A wild <pkmn> has appeared! <gmaps> Available until <24h_time> (<time_left>)."                 |

## How to get the Account SID, Auth Token, and Twilio Number

1. Go to [Twilio] (https://www.twilio.com) and click 'Get a free API key'. Fill out the following form, and enter your phone number to verify your account.

2. On the left hand side, click the Home Button and then click Dashboard. The **Account SID** and **Auth Token** will be listed. To reveal the Auth Token, click on the lock next to it.

3. Scroll down and click on '# Phone Numbers'. Then click 'Get Started' to get your free number. 

4. If you wish to text to different numbers, you need to register each before you are allowed to message them. This can be done from the 'Verified Caller ID's' page.