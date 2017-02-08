Execution is handled through the command `python start_pokealarm.py`.

PokeAlarm defaults to `127.0.0.1:4000`. Ensure that your PokemonGo-Map instance is running with the `-wh http://127.0.0.1:4000` flag or `webhook:http://127.0.0.1:4000` in your PokemonGo-Map `config.ini` file.  Update the Host and Port per your particular installation.

## Command Line Arguments

```
usage: start_pokealarm.py [-h] [-d] [-H HOST] [-P PORT] [-m MANAGER_COUNT]
                          [-M MANAGER_NAME] [-k KEY] [-f FILTERS] [-a ALARMS]
                          [-gf GEOFENCES] [-l LOCATION]
                          [-L {de,en,es,fr,it,zh_hk}] [-u {metric,imperial}]
                          [-tl TIMELIMIT] [-tz TIMEZONE]

Args that start with '--' (eg. -d) can also be set in a config file
(C:\Users\PokeAlarm\config/config.ini). Config file syntax
allows: key=value, flag=true, stuff=[a,b,c] (for details, see syntax at
https://goo.gl/R74nmi). If an arg is specified in more than one place, then
commandline values override config file values which override defaults.

optional arguments:
  -h, --help            show this help message and exit
  -d, --debug           Debug Mode
  -H HOST, --host HOST  Set web server listening host
  -P PORT, --port PORT  Set web server listening port
  -m MANAGER_COUNT, --manager_count MANAGER_COUNT
                        Number of Manager processes to start.
  -M MANAGER_NAME, --manager_name MANAGER_NAME
                        Names of Manager processes to start.
  -k KEY, --key KEY     Specify a Google API Key to use.
  -f FILTERS, --filters FILTERS
                        Filters configuration file. default: filters.json
  -a ALARMS, --alarms ALARMS
                        Alarms configuration file. default: alarms.json
  -gf GEOFENCES, --geofences GEOFENCES
                        Alarms configuration file. default: None
  -l LOCATION, --location LOCATION
                        Location, can be an address or coordinates
  -L {de,en,es,fr,it,zh_hk}, --locale {de,en,es,fr,it,zh_hk}
                        Locale for Pokemon and Move names: default en, check
                        locale folder for more options
  -u {metric,imperial}, --units {metric,imperial}
                        Specify either metric or imperial units to use for
                        distance measurements.
  -tl TIMELIMIT, --timelimit TIMELIMIT
                        Minimum number of seconds remaining on a pokemon to
                        send a notify
  -tz TIMEZONE, --timezone TIMEZONE
                        Timezone used for notifications. Ex:
                        "America/Los_Angeles"
```



## `config.ini`
To facilitate use of PokeAlarm, all of the optional arguments above may be configured in `config.ini`, located in the `config` subfolder of your PokeAlarm installation.  Below is `config.ini.example`.  Copy this file, rename to `config.ini`, and update as necessary for your instance.
```
# Copy this file to config.ini and modify to suit your needs
# Uncomment a line (remove the #) when you want to change its default value. Alternatively, all of these options can be set at the command line
# To run multiple Manager Processes, supply multiple values inside brackets: eg key:[KEY1, KEY2]

# Server Settings
#debug:                     # Enables debugging mode
#host: 						# Address to listen on (default 127.0.0.1)
#port: 						# Port to listen on (default: 4000)
#manager_count:             # Number of Manager Processes to run. default: 1
#manager_name:              # Name used to reference the managers
#key: 						# Google Maps API Key to use
#filter: 					# Specify a file describing filter rules. default: filters.json
#alarms: 					# Specify a file describing Alarm services. default: alarms.json
#geofence: 					# Specify a file describing geofences. default: geofences.json
#location: 					# Location, can be an address or coordinates
#locale: 					# Locale for Pokemon names
#unit: 					    # Specify either metric or imperial
#timelimit: 				# Minimum number of seconds remaining on a pokemon to notify
#timezone:                  # Timezone used for notifications.  Ex: "America/Los_Angeles"
```
