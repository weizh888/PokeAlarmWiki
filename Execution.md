Execution is handled through the command `python runwebhook.py`.

PokeAlarm defaults to `127.0.0.1:4000`. Ensure that your PokemonGo-Map instance is running with the `-wh http://127.0.0.1:4000` flag or `webhook:http://127.0.0.1:4000` in your PokemonGo-Map `config.ini` file.  Update the Host and Port per your particular installation.

## Command Line Arguments

```
usage: runwebhook.py [-h] [-H HOST] [-P PORT] [-k KEY] [-c CONFIG]
                     [-l LOCATION] [-L LOCALE] [-u {metric,imperial}] [-d]
                     [-gf GEOFENCE] [-tl TIMELIMIT] [-tz TIMEZONE]

Args that start with '--' (eg. -H) can also be set in a config file
(PokeAlarm/config/config.ini). The recognized syntax for
setting (key, value) pairs is based on the INI and YAML formats (e.g.
key=value or foo=TRUE). For full documentation of the differences from the
standards please refer to the ConfigArgParse documentation. If an arg is
specified in more than one place, then commandline values override config file
values which override defaults.

optional arguments:
  -h, --help            show this help message and exit
  -H HOST, --host HOST  Set web server listening host
  -P PORT, --port PORT  Set web server listening port
  -k KEY, --key KEY     Specify a Google Maps API Key to use.
  -c CONFIG, --config CONFIG
                        Alarms configuration file. default: alarms.json
  -l LOCATION, --location LOCATION
                        Location, can be an address or coordinates
  -L LOCALE, --locale LOCALE
                        Locale for Pokemon names: default en, check locale
                        folder for more options
  -u {metric,imperial}, --units {metric,imperial}
                        Specify either metric or imperial . Default: metric
  -d, --debug           Debug Mode
  -gf GEOFENCE, --geofence GEOFENCE
                        Specify a file of coordinates, limiting alerts to
                        within this area
  -tl TIMELIMIT, --timelimit TIMELIMIT
                        Minimum number of seconds remaining on a pokemon to
                        notify
  -tz TIMEZONE, --timezone TIMEZONE
                        Timezone used for notifications. Ex:
                        "America/Los_Angeles"
```

To facilitate use of PokeAlarm, all of the optional arguments above may be configured in `config.ini`, located in the `config` subfolder of your PokeAlarm installation.  Below is `config.ini.example`.  Copy this file, rename `config.ini`, and update as necessary for your instance.
```
# Copy this file to config.ini and modify to suit your needs
# Uncomment a line (remove the #) when you want to change its default value. Alternatively, all of these options can be set at the command line

# Server Settings
#host: 						# Address to listen on (default 127.0.0.1)
#port: 						# Port to listen on (default: 4000).  Do not include http://
#key: 						# Google Maps API Key to use
#config: 					# Alarms configuration file. default: alarms.json
#location: 					# Location, can be an address or coordinates
#locale: 					# Locale for Pokemon names
#geofence: 					# Specify a file of coordinates, limiting alerts to within this area
#units: 					# Specify either metric or imperial
#timelimit: 				# Minimum number of seconds remaining on a pokemon to notify
#timezone:					# Timezone used for notifications.  Ex: "America/Los_Angeles"
```

## Alarm Configuration file (alarms.json)
The `alarms.json` file is where you would customize your notifications.  It:

* Enables/disables alarm services
* Formats specific alarm notifications
* Enables pokemon, gym, or lured pokestop to be notified

Note that the default name of this alarm configuration file is `alarms.json`.  However, PokeAlarm allows you to select specific `*.json` configuration files with the `-c` or `--config` flag.

See the [Alarm Configuration](https://github.com/kvangent/PokeAlarm/wiki/Alarm-Configuration) wiki for setup and more details.