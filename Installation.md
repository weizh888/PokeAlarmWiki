1. Setup and run [PokemonGo-Map](https://github.com/PokemonGoMap/PokemonGo-Map). There is a detailed wiki [here](https://github.com/PokemonGoMap/PokemonGo-Map/wiki). Make sure you have the latest version of Python 2.7 and git installed. 

2. Navigate to the folder you want to store the Alarm in. Use `git clone https://github.com/kvangent/PokeAlarm.git` to create a local copy of the alarm.

3. Go into the alarm folder and run `pip install -r requirements.txt` to install the requirements for the Alarm.

4. Make a copy of the `alarms.json.default` folder and rename it to `alarms.json.` Edit the folder with your alarm configuration settings and set the Pokemon values you want to "True". For more information regarding individual alarm configurations, check out the individual services page. It is perfectly valid to have multiple alarms, even of the same type. 
**Note:** Windows or Mac user's should make sure to not use the default text editors. (ie. Don't use Notepad!)

5. Start the PokeAlarm with `python runwebhook.py`. You should receive a notification right away - letting you know your alarm has been set up correctly. The default listening address is `http://127.0.0.1:4000`. You can use the `-H HOST -P PORT` arguments to set a custom listening address and port. 
**Note:** This address/port should be DIFFERENT then the address/port your map is running on.

6. Start the PokemonGo-Map like normal, but add the `-wh http://127.0.0.1:4000` (or whatever listening address you specified in the last step). You can also put this in the config.ini file as well. You can have multiple alarms all pointing at the same alarm.

7. PokeAlarm should log to console every-time is learns about a pokemon - and will say 'Pokemon notification was triggered!' when a Pokemon on your list was found. If you aren't receiving anything, make sure that you have the correct address running on your Map and try again!