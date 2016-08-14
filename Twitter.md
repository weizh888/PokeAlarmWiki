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

### Step 1: Create a Twitter account
* Go to [Twitter's signup page](https://twitter.com/signup)
* Fill out all details, and **make sure to include your phone number**. This is a requirement for remote access, and you will need that to make the Twitter bot work.

### Step 2: Create a Twitter app
* Go to [app.twitter.com](https://apps.twitter.com)
* Click 'Create New App' button
* Fill out the details on the form. You have to give your app a name, description, and website. This can be a simple place holder like http://www.example.com
* Read the Developer Agreement, and check the box at the bottom if you agree. Then click on the ‘Create your Twitter application’ button.

### Step 3: Keys and Access tokens
* After creating your new app, you were redirected to its own page. If you weren’t, go to [app.twitter.com](https://apps.twitter.com) and click on your apps name.
* On the app’s page, click on the ‘Keys and Access Tokens’ page.
* At the bottom of this page, click on the ‘Create my access token’ button.
* Take note of **Consumer Key (API Key), Consumer Secret (API Secret), Access Token, & Access Token Secret**. These are the are required in the Twitter Config.
