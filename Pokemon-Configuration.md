To configure what Pokemon you would like to be notified of, you need to edit the alarms.json file. Under the pokemon field, you need to specify the name of the Pokemon, and then specify when you would like to be notified of it.

**Note:** In order for distances to work, you MUST have a location set with `-l LOCATION`

`"Bulbasaur":"True"` will notify you of the pokemon Bulbasaur, regardless of its distance away from your set location. T, True, Y, and Yes evaluate to true, regardless of casing.

`"Bulbasaur":"1000"` will notify you of the pokemon Bulbasaur, if its distance is not greater then 1000 meters away. 

`"Bulbasaur":"False"` will NEVER notify you of the pokemon Bulbasaur, if its distance is not greater then 1000 meters away. Anything will evaluate to false unless is an except True statement or a float number.

Pokemon names should be allow in any supported language, regardless of set locale. However, the alert will ONLY specify pokemon in the selected locale. Mispelled pokemon names will NOT be counted.

## Example Pokemon Config 
```json
"pokemon":{
		"Bulbasaur":"1000",
		"Ivysaur":"False",
		"Bisaflor":"50",
		"Charmander":"true",
		"Charmeleon":"T",
		"Charizard":"True",
		"Сквиртл":"False",
		"Wartortle":"False",
		"Blastoise":"WHAT",
}
```

This will notify you of Bulbasaur (within 1000m), Venusaur (within 50m), Charmander, Charmeleon, and Charizard. 
