# Nodejs/IOjs Library for ESC/POS Thermal Printer
[![Build Status](https://travis-ci.org/adzymaniac/thermalPrinter.svg)](https://travis-ci.org/adzymaniac/thermalPrinter) [![Test Coverage](https://codeclimate.com/github/adzymaniac/thermalPrinter/badges/coverage.svg)](https://codeclimate.com/github/adzymaniac/thermalPrinter)


Forked from [Adafruit/Sparkfun based Thermal Printer](https://github.com/xseignard/thermalPrinter)

## Usage
- install with `npm install thermalprinter --save` 
- check the demo sample:

```js
var SerialPort = require('serialport').SerialPort,
	serialPort = new SerialPort('/dev/ttyUSB0', {
		baudrate: 19200
	}),
	Printer = require('thermalprinter');

var path = __dirname + '/images/nodebot.png';

serialPort.on('open',function() {
	var printer = new Printer(serialPort);
	printer.on('ready', function() {
		printer
			.indent(10)
			.horizontalLine(16)
			.bold(true)
			.indent(10)
			.printLine('first line')
			.bold(false)
			.inverse(true)
			.big(true)
			.right()
			.printLine('second line')
			.printImage(path)
			.print(function() {
				console.log('done');
				process.exit();
			});
	});
});
```

## License

Original's repository does not include any license information. [This license](LICENSE) only for what changed from this repository.