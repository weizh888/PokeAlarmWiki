## Overview
* [Prerequisites](#prerequisites)
* [Introduction](#introduction)
* [Base URL](#base-url)
* [Get Location](#get-location)
* [Update Location](#update-location)
* [Get Geofence Area](#get-geofence-area)

## Prerequisites
This guide assumes:

1. You have a working PokeAlarm installation.
2. You are familar with REST APIs


## Introduction
PokeAlarm exposes a REST API that grants programmatic access to:
* Collect current location, in *[lat,lon]* format
* Update location
* Get an image URL of the current geofence area

## Base URL
| Base URL                       |
|:-------------------------------|
| `http://127.0.0.1:4000`        |

The base URL will change if you override the default HOST and PORT in `config.ini` or by passing `-H HOST` and/or `-P PORT` in the command line.

## Get Location
Returns the current location, set by the `-l` parameter in PokeAlarm.

### Request

|Request   | Path         |
|:---------|:-------------|
| `GET`    | `/location/` |

### Response
200 status code with text of current location coordinates in lat,lon format.

#### Example response

`Current location is [40.764694, -73.973083]`



## Update Location
Changes location of PokeAlarm. 

### Request 

Pass `NEW_LOCATION` directly into the request URL with an empty body.

|Request     | Path                               |
|:-----------|:-----------------------------------|
| `POST`     | `/location/?location=NEW_LOCATION` |

### Response
200 status code with updated location coordinates in lat,lon format.
#### Example response

`Location changed to : [40.764694, -73.973083]`

#### Example console output
```
2016-09-22 16:22:34,927 [        runwebhook] [   INFO] POST request received from 127.0.0.1.
2016-09-22 16:22:35,098 [             utils] [   INFO] Location found: 40.764694, -73.973083
2016-09-22 16:22:35,098 [        runwebhook] [   INFO] Location updated via POST request!
```

## Get Geofence Area
Retrieves a URL from Google Maps that represents the geofence area.

### Request

|Request     | Path         |
|:-----------|:-------------|
| `GET`      | `/geofence/` |

### Response

200 status code with response of google maps image, similar to below.

#### Example Response
`<img src="https://maps.googleapis.com/maps/api/staticmap?size=600x600&maptype=roadmap&markers=fillcolor%3Ablue%7C...>`

A browser request will display an image of the geofenced area, for example:
![](images/geofence_coronado.png)

If geofence is not enabled, the response will be your current location, with the google image pin and no bounded shaded geofence area.

If no location or geofence is enabled, the response will be `no location or geofence set`.