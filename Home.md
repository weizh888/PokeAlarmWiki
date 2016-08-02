# PokeAlarm

The alarm is a third party extenstion of [AHAAAAAAA's PokemonGo-Map](https://github.com/AHAAAAAAA/PokemonGo-Map) that allows you to received external notifications via the service of your choice.

We currently support the following services:
* Pushbullet
* Slacker
* Twilio (SMS)
* Telegram. 

Pushbullet support will likely be discontinued after August 1st because of the change of services to premium. 

If you are experience issues with the alarm or would like to see new features, please open a ticket here on github. 

If you are experiencing trouble with setup or other user difficulties, please see the reddit thread.

## Common Problems

### Problems with receiving in UTC time or Notifications not sending because 'time_left has passed'.

I have implemented a client side fix for this issue. Simply run the webserver with the --time_fix command to have your times corrected. The command will be `python runwebhook.py --time_fix`. If the PokemonGo-Map ever gets the issue corrected, just drop the extra argument.

If you see this issue after updating to the latest version, please open an issue ticket here on github.

### Windows: socket.error: [Errno 10053] An established connection was aborted by the software in your host machine OR Linux: socket.error: [Errno 32] Broken pipe

This issue should now be correctly caught from the client side. If you still experience this issue, please open an issue ticket on github.


