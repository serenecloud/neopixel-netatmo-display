# neopixel-netatmo-display

This is a project I did in my spare time for fun. It is shared so others wanting to do something similar can look at it for inspiration.

##What I used##

* A [netatmo weather station](https://www.netatmo.com/en-US/product/weather-station) and [the netatmo private API](https://dev.netatmo.com/)
* [netatmo-api-python](https://github.com/philippelt/netatmo-api-python/) by Philippe Larduinat
* An Arduino Nano
* An [Adafruit Neopixel](https://www.adafruit.com/products/1463) and [their library](https://github.com/adafruit/Adafruit_NeoPixel)
* An old laptop running Linux

##Disclaimer##

Adafruit Neopixels are not designed to be run without an external power source & resistor. I took the shortcut of setting the brightness very low, enough that I can light all the pixels with just the Nano. This is important, because if you don't, you can fry your Neopixel. Follow their guides if you're not willing to risk it.

##What I created##

An LED ring that shows the four main readings from the netatmo so everyone in the living room can see if everything is healthy.

![Image of indicator](http://f.dollyfish.net.nz/dbe0fc.jpg)

## How it works ##

* The neopixel has 16 LEDs, which I think of as 4 quarters with 4 pixels each
  * The code for the Arduino accepts Serial commands that tell it what colour to set each quarter a colour in the format `QUARTER_NUMBER:COLOUR;`. e.g. `0:green;`, `3:red;`

* The python script handles talking to the Netatmo API, getting the values and deciding which colour to use for which values
  * The colours are what I have set for a New Zealand climate - your values may be different
  * The instructions are sent over serial. For the above image you would send: `0:blue;` `1:green;` `2:green` `3:orange` as 4 different Serial instructions.

##Limitations##

This code is not particularly elegant, but it's working. If you want to pursue your own project I encourage you to take the code, improve it and share it. I'll happily see what others create based on this.

The netatmo takes regular readings, but it only sends them to the API every 10 minutes, so I only poll every 10 minutes.
