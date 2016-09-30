## ***Pokemon***
Pokemon standard now includes moveset and IVs as of commit [oc1b4](https://github.com/kvangent/PokeAlarm/commit/0c1b4cce80e0ceb3cc6dbb2d802204af4dd3ce60).
#### Example:
```json
{
	"type": "pokemon",
	"message": {
		"move_1": 221,
		"move_2": 118,
		"disappear_time": 1375014270,
		"pokemon_id": 1,
		"individual_stamina": 15,
		"spawnpoint_id": "0",
		"individual_defense": 2,
		"longitude": -45.10312534490142,
		"time_until_hidden_ms": 884287,
		"latitude": 40.677737099053275,
		"last_modified_time": 1475033386661,
		"individual_attack": 5,
		"encounter_id": "0"
	}
}
```


## Pokestops
#### Example:
```json
{ 
    "type": "pokestop",
    "message": {
        "pokestop_id": 0,
        "enabled": "True",
        "latitude": 62.790967,
        "longitude":  76.927920,
        "last_modified_time": 1572241600,
        "lure_expiration": 1572241600,
        "active_fort_modifier": 0
    }
}
```

## Gyms
#### Example:
```json
{ 
    "type": "gyms",
    "message": {
		"gym_id": 0,
		"team_id": 0,
		"guard_pokemon_id": 0,
		"gym_points": 100,
		"enabled": "True",
		"latitude": 62.790967,
		"longitude":  76.927920,
		"last_modified": 1572241600
    }
}
```

#### Gym-details Example:
```json
{
	"type": "gym_details",
    "message": {
        "id": "4b432a31c3c247e5b0f7656d09e2c050.11",
        "url": "http://lh3.ggpht.com/yBqXtFfq3nOlZmLc7DbgSIcXcyfvsWfY3VQs_gBziPwjUx7xOfgvucz6uxP_Ri-ianoWFt5mgJ7_zpsa7VNK",
        "name": "Graduate School of Public Health Sculpture",
        "description": "Sculpture on the exterior of the Graduate School of Public Health building.",
        "team": 1,
        "latitude": 40.442506,
        "longitude": -79.957962,
        "pokemon": [{
            "num_upgrades": 0,
            "move_1": 234,
            "move_2": 99,
            "additional_cp_multiplier": 0,
            "iv_defense": 11,
            "weight": 14.138585090637207,
            "pokemon_id": 63,
            "stamina_max": 46,
            "cp_multiplier": 0.39956727623939514,
            "height": 0.7160492539405823,
            "stamina": 46,
            "pokemon_uid": 9278614152997308833,
            "iv_attack": 12,
            "trainer_name": "SportyGator",
            "trainer_level": 18,
            "cp": 138,
            "iv_stamina": 8
        }, {
            "num_upgrades": 0,
            "move_1": 234,
            "move_2": 87,
            "additional_cp_multiplier": 0,
            "iv_defense": 12,
            "weight": 3.51259708404541,
            "pokemon_id": 36,
            "stamina_max": 250,
            "cp_multiplier": 0.6121572852134705,
            "height": 1.4966495037078857,
            "stamina": 250,
            "pokemon_uid": 6103380929145641793,
            "iv_attack": 5,
            "trainer_name": "Meckelangelo",
            "trainer_level": 22,
            "cp": 1353,
            "iv_stamina": 15
        }, {
            "num_upgrades": 9,
            "move_1": 224,
            "move_2": 32,
            "additional_cp_multiplier": 0.06381925195455551,
            "iv_defense": 13,
            "weight": 60.0,
            "pokemon_id": 31,
            "stamina_max": 252,
            "cp_multiplier": 0.5974000096321106,
            "height": 1.0611374378204346,
            "stamina": 252,
            "pokemon_uid": 3580711458547635980,
            "iv_attack": 10,
            "trainer_name": "Plaidflamingo",
            "trainer_level": 23,
            "cp": 1670,
            "iv_stamina": 11
        }]
    }
}
```
