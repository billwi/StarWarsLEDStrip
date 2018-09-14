---
layout: default
---

# Star Wars style LED firing with WS2812

For Christmas 2017, I was tasked to program a set of LED strips to make it look like an at-at was firing at the millennium falcon and vice versa. They were placed approximately 30 feet, or 10 meters apart. While factually both the at-at and the millennium falcon shoot red lasers, for some variety I decided to use green for the at-at and red for the falcon.

## The items

### Power supply

The power supply of choice was a 5 volt, 18 amp transformer from alitove. It worked well, providing screw terminals for the positive and negative. [Something like this, except 18 amps](https://www.amazon.com/ALITOVE-Adapter-Converter-Charger-5-5x2-1mm/dp/B01M0KLECZ/ref=cm_cr_arp_d_product_top?ie=UTF8)

### Logic board

An Arduino Uno was used due to the low power consumption, however any cheap programming board would have worked, namely any Arduino clone, any Arduino board, or a Teensy. An official [Arduino Uno](https://www.amazon.com/Arduino-Uno-R3-Microcontroller-A000066/dp/B008GRTSV6/ref=sr_1_4?ie=UTF8&qid=1512700508&sr=8-4) was used, but a [good clone](https://www.amazon.com/Elegoo-Board-ATmega328P-ATMEGA16U2-Arduino/dp/B01EWOE0UU/ref=sr_1_3?ie=UTF8&qid=1512700508&sr=8-3&keywords=arduino+uno) would have worked just as well.

### LEDs

2-5 meter strips of WS2812B strips were used. These were water proof, with a plastic sheath and glued down ends. This is useful since the lights will be placed outdoors. Two reels of [this](https://www.amazon.com/dp/B018X04ES2/ref=psdc_11974311_t1_B00ZHB9M6A) were used.

### 470 ohm resistor

This is optional and I did not have a resistor to use for this, but it would be useful, especially if a battery is used instead of a transformer. This would be connected between the green data wire of the LED and pin 6.

### 100 micro ferret capacitor

This is also an option part, which comes in handy if a battery is used instead of a transformer. It simply serves as a smoothing capacitor. This would be connected between GND and 5v on the Arduino.

## The Setup

Everything will be placed outdoors, so a single supply was a must. The power supply has 2 terminals, which both connect to the loose wires of the WS2812B strip. The LED strip then also gave a 3-pin header, with a ground, 5v, and a data line. The data line connects to the 6-pin on the Arduino, the 5v goes to the 5v line on the Uno, and the ground goes to ground.

On the other end, of the LEDs, there was a female connecter for the 3-pin as well as another 2 lose 5v and ground wires. The 3-pin connector directly connected to the 3-pin connector of the 2nd LED strip, requiring no other wires since it passed the power through flawlessly.

Since the at-at was on the floor and the falcon was on top of a roof, it made logical sense to have the at-at side (shooting green) be closer to the Uno where the power supply was located.

![Wiring Diagram](/wiringDiagram.png?raw=true)

## The code

The code can be found in the [starwars.ino](/starwars.ino) file. It uses the [FastLED library](http://fastled.io/) to interact directly with the WS2812B strip. The code can easily be uploaded to an Arduino using the [Arduino IDE](https://www.arduino.cc/en/Main/Software) or the [Arduino web editor](https://create.arduino.cc/editor). The FastLED library must be added. The zip provided is FastLED version 3.1.6, and is packaged as acceptable by the IDE. Simply add the library and hit the upload button with the Arduino connected to be on your way!

## Warnings

NEVER keep both the USB cable and the 5v line to the Arduino connected. The 5v line powers the Arduino, as does USB. Both together should NEVER be used!

## Notices

The WS2812B does not use RGB like most normal LEDs, but rather GRB. I was unaware of this during the programming, but noticed that the red and green shots were swapped. I set the pins to send Green when I really wanted red and vice versa, but setting the mode to GRB would have been the better way. 

## End result

The end result has a green bolt fire from the at-at to the falcon, at up to 4 consecutive bolts (chosen randomly). The falcon will then fire back, again randomly at 1-4 bolts, but green. A video will be attached later :)

## Sources

- [https://www.tweaking4all.com/hardware/arduino/arduino-ws2812-led/](https://www.tweaking4all.com/hardware/arduino/arduino-ws2812-led/)

-----------------------------------

[Link to repository](https://github.com/cool00geek/StarWarsLEDStrip)
