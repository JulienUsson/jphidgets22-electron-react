## Synopsis

**Un**official Phidget22 JavaScript library.

This library includes react and electron project support.

Note that the Phidget Network Server is required for JavaScript clients to
access Phidget devices.

## Code Example

Examples for each Phidget channel class are available at www.phidgets.com.

```
import jPhidget22 from 'jphidgets22-electron-react';

var url = 'ws://localhost:8989/phidgets';

console.log('connecting to:' + url);
var conn = new jPhidget22.Connection(url, { name: 'Server Connection', passwd: '' });
conn.connect()
  .then(runExample)
  .catch(function (err) {
	console.log('Error running example:' + err);
  });

function runExample() {

	var ch = new jPhidget22.TemperatureSensor();

	ch.onAttach = function(ch) {
		console.log(ch + ' attached');
		console.log('min temperature:' + ch.getMinTemperature());
		console.log('max temperature:' + ch.getMaxTemperature());
	};

	ch.onDetach = function(ch) {
		console.log(ch + ' detached');
	};

	ch.onTemperatureChange = function (temp) {
		console.log('temperature:' + temp + ' (' + this.getTemperature() + ')');
	};

	ch.open().then(function (ch) {
		console.log('channel open');
	}).catch(function (err) {
		console.log('failed to open the channel:' + err);
	});
}
```
## API Reference

Please see the online documentation at www.phidgets.com.
