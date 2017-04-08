Execution is handled through the command `python start_pokealarm.py`.

PokeAlarm defaults to `127.0.0.1:4000`. Ensure that your RocketMap instance is running with the `-wh http://127.0.0.1:4000` flag or `webhook:http://127.0.0.1:4000` in your RocketMap `config.ini` file.  Update HOST and PORT per your particular installation.

## Command Line Arguments

```
pokealarm@pokealarm:/PokeAlarm$ python start_pokealarm.py -h
usage: start_pokealarm.py [-h] [-cf CONFIG] [-d] [-H HOST] [-P PORT]
                          [-m MANAGER_COUNT] [-M MANAGER_NAME] [-k KEY]
                          [-f FILTERS] [-a ALARMS] [-gf GEOFENCES]
                          [-l LOCATION] [-L {de,en,es,fr,it,ko,zh_hk}]
                          [-u {metric,imperial}] [-tl TIMELIMIT]
                          [-ma MAX_ATTEMPTS] [-tz TIMEZONE]

Args that start with '--' (eg. -d) can also be set in a config file
(/PokeAlarm/config/config.ini or specified via -cf). The
recognized syntax for setting (key, value) pairs is based on the INI and YAML
formats (e.g. key=value or foo=TRUE). For full documentation of the
differences from the standards please refer to the ConfigArgParse
documentation. If an arg is specified in more than one place, then commandline
values override config file values which override defaults.

optional arguments:
  -h, --help            show this help message and exit
  -cf CONFIG, --config CONFIG
                        Configuration file
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
  -L {de,en,es,fr,it,ko,zh_hk}, --locale {de,en,es,fr,it,ko,zh_hk}
                        Locale for Pokemon and Move names: default en, check
                        locale folder for more options
  -u {metric,imperial}, --units {metric,imperial}
                        Specify either metric or imperial units to use for
                        distance measurements.
  -tl TIMELIMIT, --timelimit TIMELIMIT
                        Minimum number of seconds remaining on a pokemon to
                        send a notify
  -ma MAX_ATTEMPTS, --max_attempts MAX_ATTEMPTS
                        Maximum number of attempts an alarm makes to send a
                        notification.
  -tz TIMEZONE, --timezone TIMEZONE
                        Timezone used for notifications. Ex:
                        "America/Los_Angeles"
```



## `config.ini`
To facilitate use of PokeAlarm, all of the optional arguments above may be configured in `config.ini`, located in the `config` subfolder of your PokeAlarm installation.  Below is `config.ini.example`.  Copy this file, rename to `config.ini`, and update as necessary for your instance.
```
# Copy this file to config.ini and modify to suit your needs
# Uncomment a line (remove the #) when you want to change its default value.
# Multiple arguments can be listed as [arg1, arg2, ... ]
# Number of arguments must match manager_count or be a single arguement (single arguements will apply to all Managers)
# To exclude an argument for a specific manager, use 'None'

# Server Settings
#debug											# Enables debugging mode
#host:											# Address to listen on (default 127.0.0.1)
#port:											# Port to listen on (default: 4000)
#manager_count: 1								# Number of Managers to run. (default: 1)

# Manager-Specific Settings
#manager_name                                   # Name of the Manager in the logs. Default(manager_0).
#key:                                           # Google Maps API Key to use
#filters:										# File containing filter rules (default: filters.json)
#alarms: 										# File containing alarm rules (default: alarms.json)
#geofence:										# File containing geofence(s) used to filter (default: None)
#location:										# Location for the manager. 'Name' or 'lat lng' (default: None)
#locale:										# Language to be used to translate names (default: en)
#unit:											# Units used to measure distance. Either 'imperial' or 'metric' (default: imperial)
#timelimit:										# Minimum number of seconds remaining to send a notification (default: 0)
#max_attempts:									# Maximum number of attempts an alarm makes to send a notification. (default: 3)
#timezone:                                      # Timezone used for notifications Ex: 'America/Los_Angeles' or '[America/Los_Angeles, America/New_York]'
```
