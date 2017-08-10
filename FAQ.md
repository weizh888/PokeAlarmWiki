## Overview
* [General Info](#general=info)
* [Troubleshooting](#troubleshooting)

## General Info

#### What scanners are supported?

* Currently RocketMap and Monocole are compatible with PA. Any others following our [Webhook Standards](webhook-standard) should work as well. The PA team does NOT help with troubleshooting scanners - they have their own resources you can use.

#### I have a great idea for a new feature!
* Open an Enhancement Request on our Github page. Use the correct template - Do NOT post requests in Discord!

#### Do you support new services?
* Please check in the [New/Upcoming Service MEGA-THREAD](https://github.com/kvangent/PokeAlarm/issues/147) to see if the service has already been requested. If it hasn't, feel free to leave a post requesting it.

##Troubleshooting

#### I am receiving an Error from RocketMap! What do I do?
* Check the [RocketMap Wiki](https://rocketmap.readthedocs.io) or the ask in the RocketMap Discord.  We will not troubleshoot your RocketMap installation.

#### PokeAlarm outputs an alarm about 'ValueError' when starting up?

1. Make sure you didn't open any files with Notepad or TextEdit - they can break the encoding on your files.
2. If you sure that isn't the problem, then you probably have an error with your JSON Formatting. Look up how JSON formatting works and use a [JSON Editor](http://www.jsoneditoronline.org/) to find your problem.

#### PokeAlarm repeatedly spams Error 10053 on Windows or Error 53 on Linux?

* This error is when your machine can't keep up with the current number of sockets open. This is particularly common on Windows. You can try the following:
1. Lower the number of webhook threads (wh-concurrent or similiar)
2. Decrease database threads (db-concurrency or similiar)
3. If on Windows, try Linux (even a VM will see improvements)
4. If all of the above fails, you are being bottlenecked by hardware. It could be CPU is maxed out, HD is too slow, etc. You can upgrade your hardware or add on additional machine(s) to split the load.

#### Why does <iv>, <cp>, or another DTS show up as '?'?
* This means that PA wasn't send that information by your scanner. Make sure your scanner is configured to scan for the data you want. 

#### My maps don't show up consistently... What can I do?
* Make sure you have added a [Google API Key](Google-Maps-API-Key) and have the Static Maps API enabled. If you already have it enabled, make sure that you haven't hit the limit for free users.

#### Why isn't <gym_name> working right?
* You must have gym-details enabled in your scanner and webhook options. 
* Most scanners don't send the gym-details with every gym related webhook - PA will cache the details and try to remember them, but this goes away upon restart. It takes time for the scanner to send all the details. 

#### I have some other problem and can't figure it out.
* If you have already checked the [Wiki](Home) thoroughly, you can try asking in our [Discord](https://discord.gg/S2BKC7p). Make sure to read the Rules before posting.
* **Note**: Only [PokeAlarm Patrons](https://www.patreon.com/pokealarm) are guaranteed responses from the PA team as thanks for their helping to keep PA alive and running. 