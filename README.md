PokeAlarm is a third party extension of [PokemonGo-Map](https://github.com/PokemonGoMap/PokemonGo-Map) that allows you to receive external notifications via one or more message services.  Customized notifications are available by configuring the `alarms.json` file.

We currently support the following services:
* [Pushbullet](https://github.com/kvangent/PokeAlarm/wiki/Pushbullet) (support likely be discontinued soon due to changes in the API pricing structure)
* [Pushover] (https://github.com/kvangent/PokeAlarm/wiki/Pushover)  
* [Slack](https://github.com/kvangent/PokeAlarm/wiki/Slack)
* [Telegram](https://github.com/kvangent/PokeAlarm/wiki/Telegram) 
* [Twilio (SMS)](https://github.com/kvangent/PokeAlarm/wiki/Twilio-(SMS))
* [Twitter](https://github.com/kvangent/PokeAlarm/wiki/Twitter)

## Support

### [Discord Link](https://discordapp.com/invite/am66rag) <---- Visit us here first!!!
For questions about set up, please visit us at our [Discord channel](https://discordapp.com/invite/am66rag). Stick to the #general and #troubleshooting chats and avoid sending private messages to devs. We're working hard, we promise!

If you are experiencing issues with the alarm or would like to see new features, please open a ticket on github [here](https://github.com/kvangent/PokeAlarm/issues/new). Be sure to complete the included suppport template and provide as much information as possible.  **Support tickets that do not fully complete the request template may be closed without notice.**

Our PokeAlarm reddit thread is located [here](https://www.reddit.com/r/pokemongodev/comments/4wl5my/pokealarm_v21_external_alerts_from_your_favorite).


## Upcoming Features

PokeAlarm is under development. Though school, work, and a few other big life events are quickly approaching, I still plan to add updates and provide support in my free time. If you are interested in helping out, please contact me via the [discord channel](https://discordapp.com/invite/am66rag).

## FAQ

#### Which version of PokemonGo-Map do I need?

* Use the develop branch.  Most work in PokemonGo-Map is being done there.  They do not currently have a master. PokeAlarm is a webhook - an extension of PokemonGo-Map. We can update PokeAlarm without affecting your PokemonGo-Map installation, or vice-versa.  

#### Will you be adding support for XYZ?
* Please make a request in the [NEW/UPCOMING SERVICE MEGA-THREAD](https://github.com/kvangent/PokeAlarm/issues/147).  New standalone issue tickets will be closed without notice.

#### Man I wish this could do XYZ!
* Open an issue on github and fill out the appropriate issue template and we'll look into it.

#### I am receiving XYZ error from PokemonGo-Map! What do I do?
* Visit our [Discord channel](https://discordapp.com/invite/am66rag), Checkout the [PokemonGo-Map Wiki](https://github.com/kvangent/PokeAlarm/wiki) or the reddit thread to see if anyone has any suggestions for you.

#### I am receiving an error about JSON input from PokeAlarm (e.g., "expecting delimiter"). What gives?

* If you are a Windows user, stop using notepad and start using Notepad++. Make a fresh copy of the alarms.json and remake your changes. If you aren't a Windows user (or you are already using Notepad++) check your JSON format with a JSON formatter for issues ([jsoneditoronline.org](http://www.jsoneditoronline.org) is an excellent site to start.)

#### Can I run multiple simultaneous alarms services?

* Yes. You may configure as few or as many simultaneous alarm services in `alarms.json` like Twitter, Slack and Telegram.  For example, you can post to 2 Twitter accounts, 3 Slack channels and have a Twilio SMS service running from one `alarms.json` configuration. Visit the Alarm Configuation wiki for details.

Alternatively, you can run PokemonGo-Map with multiple webhooks and have multiple instances of PokeAlarm assigned to a different http://host:port (e.g., http://127.0.0.1:4000, http://127.0.0.1:4001, http://127.0.0.1:4002).

#### I'm having issues with setting a location, it is not showing distance, maps are not showing up, walking directions, etc.

* These errors are all map related.  Sign up for a Google Maps API key and enable Static Maps in the console. See the Google Maps documentation [here](https://developers.google.com/maps/documentation/static-maps/intro). To test if your key is working, visit the URL below and replace `YOUR_API_KEY` with your Google Maps API key.

```javascript
https://maps.googleapis.com/maps/api/staticmap?center=Brooklyn+Bridge,New+York,NY&zoom=13&size=600x300&maptype=roadmap&markers=color:blue%7Clabel:S%7C40.702147,-74.015794&markers=color:green%7Clabel:G%7C40.711614,-74.012318&markers=color:red%7Clabel:C%7C40.718217,-73.998284&key=YOUR_API_KEY
```
If your key is valid, you should see this same static map image in your browser:
![](images/staticmaptest.png)

If your key has issues, you will get the error `The Google Maps API server rejected your request. The provided API key is invalid.`



#### Problems with receiving in UTC time or Notifications not sending because 'time_left has passed'.

* This error should now be corrected. Please make sure you have updated to the latest version of PokemonGo-Map. If you are still experiencing issues, please open a ticket. 

#### Windows: socket.error: [Errno 10053] An established connection was aborted by the software in your host machine OR Linux: socket.error: [Errno 32] Broken pipe

* This error should now be corrected. Please make sure you have updated to the latest version of PokemonGo-Map. If you are still experiencing issues, please open a ticket.