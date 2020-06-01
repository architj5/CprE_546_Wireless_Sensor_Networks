# LED HAL Example
This example demonstrates and tests the functionality of the LED HAL, temperature sensor and light sensor.


* Understand the sensor activation, reading, and calibration.


# Supported devices
This example is expected to work off-the-shelf on the following boards:

* All CC13xx/CC26xx devices
* All CC2538 devices

# Make sure
* The makefile and the leds-example.c are in the same directory
* Within the makefile the path for the contiki-ng directory CONTIKI = ../path takes to the contiki-ng directory/../


* The LEDs blink according to the following order depending on the least significant bits of the counter.

* LED Green: LSB
* LED Red: bit next to LSB

When counter is  4x, 	(x = 0, 1, 2,...), both LEDs OFF 			(00)
When counter is (4x+1), (x = 0, 1, 2,...), Red  OFF, Green ON		(01)
When counter is (4x+2), (x = 0, 1, 2,...), Red ON, Green OFF		(10)
When counter is (4x+3), (x = 0, 1, 2,...), both LEDs ON				(11)

Each state is maintained till the next packet is received.

The node transmits a message each second with some added randomness between 0 to 0.99 second.
This random interval is achieved by calling 'random_rand()'.
	a. A random number is generated and its mod 100 is calculated. 
	b. This gives a number between 0 to 99
	c. This number is divided by 100 to get a value between 0 to 0.99
	d. This fraction is added to the default clock interval (which is 1 second)
	
	
