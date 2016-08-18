#PokeAlarm

The alarm is a third party extension of [PokemonGo-Map](https://github.com/PokemonGoMap/PokemonGo-Map) that allows you to received external notifications via the service of your choice.

We currently support the following services:
* Pushbullet
* Slacker
* Telegram. 
* Twilio (SMS)

Pushbullet support will likely be discontinued after August 1st because of the change of services to premium. 

If you are experience issues with the alarm or would like to see new features, please open a ticket here on github. 

If you are experiencing trouble with setup or other user difficulties, please see the reddit thread.

##Command Line Arguments

'-H', '--host' - Set web server listening host, default is 127.0.0.1  

'-P', '--port' - Set web server listening port, default is 4000  

'-l', '--location' - Location, can be an address or coordinates. If no locations are set, distances will always calculate as 0.  

'-L', '--locale' - Locale for Pokemon names: default is en, check locale folder for more options 

'-d', '--debug', - Debug Mode, allows extra output to console  

'-sl', '--skip_lured', - Do not alert for a lured Pokemon. 

## Common Problems

#### Unable to decode JSON object

Make sure you aren't using notepad to edit the files (Notepad++ is a good alternative). Also, check to make sure your json formatting is correct. You can check your format [here] (http://www.jsoneditoronline.org/).

#### Problems with receiving in UTC time or Notifications not sending because 'time_left has passed'.

This error should now be corrected. Please make sure you have updated to the latest version of PokemonGo-Map. If you are still experiencing issues, please open a ticket. 

#### Windows: socket.error: [Errno 10053] An established connection was aborted by the software in your host machine OR Linux: socket.error: [Errno 32] Broken pipe

This error should now be corrected. Please make sure you have updated to the latest version of PokemonGo-Map. If you are still experiencing issues, please open a ticket.


