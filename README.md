# IR decoder

Decodes long IR codes, for example from air conditioner / heat pump devices.

Shows the timings, the symbols, and also the decoded signal for certain air conditioners.

Required hardware:
- Arduino (any compatible will do, but Arduino Uno or Nano is easiest for prototyping)
- Infrared receiver, for example VS1838 will do fine, see also https://arduino-info.wikispaces.com/IR-RemoteControl
- Breadboard, wiring
- IR remote control from the aircon/heatpump you plan to decode

## Build instructions
Defines for the different brands were introduced to limit the memory footage on a Arduino UNO.
Uncomment, in the beginning of the sketch, the define for your remote brand.
You will get a compiler error if you forget to uncomment!

* //#define MITSUBISHI_ELECTRIC
* //#define FUJITSU
* //#define MITSUBISHI_HEAVY
* //#define DAIKIN
* //#define SHARP_
* //#define CARRIER
* //#define PANASONIC_CKP
* //#define PANASONIC_CS
* //#define HYUNDAI
* //#define GREE
* //#define GREE_YAC
* //#define FUEGO
* //#define TOSHIBA
* //#define NIBE
* //#define AIRWELL
* //#define HITACHI
* //#define SAMSUNG
* //#define BALLU
* //#define AUX
* //#define ZHLT01_REMOTE
* //#define PHILCO

### Arduino IDE
* Open the sketch from subdirectory 'rawirdecode' in Arduino IDE and build

### PlatformIO
* platformio.ini contains build definitions for Arduino Mega, ESP32 (both tested on M5STACK ATOM LITE) and ESP8266 (tested on nodemcu)
* On Mega, connect the receiver data pin to GPIO 2
* On ESP32, connect the receiver data pin to GPIO 25
* On ESP8266, connect the receiver data pin to GPIO 5

## Instructions

* Connect an IR receiver into the Arduino
* Start the sketch, and enter 1, 2, 3, 4 or 5 into the 'Serial Monitor', to select which timings to use
   * Try out the alternatives until you get sensible output
   * The signal should always start with 'Hh', and within the signal there should only be a couple of 'Hh' pairs (if any)
   * 'H' and 'h' should be there only in pairs 'Hh'
   * 'H' stands for 'header mark' and 'h' for 'header space'
* Point your IR remote to the IR receiver and send the code
   * If the symbols are known, then the decoder shows its meaning on the serial monitor
   * If the symbols are unknown, then you can help by writing a decoder for the unknown remote

-> Mode '9' can be used to decode known signals, in that case you can send the symbols from the terminal, like entering this:

   Hh001101011010111100000111001001010100000000000111000000001111111011010100000001000111001011

![Schema](arduino_irreceiver.png)
