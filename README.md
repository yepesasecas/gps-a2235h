#GPS
Driver for the gps-a2235h Tessel GPS module (\<key chip\>)."

##Example
```js
var tessel = require('tessel');
var hardware = tessel.port('b');

var gps = require('./index.js').connect(hardware);

gps.on('connected', function() {
	console.log('GPS connected. Waiting for data...');
	gps.on('data', function() {
		console.log(gps.getSatellites()); //if numSat is 0, try going outside
		console.log(gps.getCoordinates()); //options: 'deg-min-sec', 'deg-dec', default 'deg-min-dec'
		console.log(gps.getAltitude()); //options: 'feet', defaults to meters
		console.log (gps.geofence({lat: [42.29, 'N'], lon: [71.27, 'W']}, {lat: [42.30, 'N'], lon: [71.26, 'W']}));
	});
});
```

##Installation
```sh
npm install gps-a2235h
```

##Import
```js
var gps = require('gps-a2235h').connect(hardware);
```

##Methods

*  **`gps`.getCoordinates(`format`)**

*  **`gps`.getAltitude(`format`)**

*  **`gps`.getSatellites()**

*  **`gps`.geofence(`minCoordinates`, `maxCoordinates`)**

*  **`gps`.powerOn()**

*  **`gps`.powerOff()**

## License

MIT
