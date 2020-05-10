# OpenS-Hypnos
Power Control Board for microcontroller projects, designed at OPEnS Lab OSU.

Go to [Hypnos Wiki](https://github.com/OPEnSLab-OSU/OPEnS-Lab-Home/wiki/Hypnos) for more info and build guide.

<p align="center">
 <img  src="https://user-images.githubusercontent.com/48141945/67116762-fbe4ae80-f195-11e9-9a96-2610e023e2e0.jpg" width="230">   
 <img src="https://user-images.githubusercontent.com/48141945/67116763-fc7d4500-f195-11e9-8e4b-1b0d26c35872.jpg" width="230">
</p>

### Pinout
![Hypnos V3.1 Pinout](https://user-images.githubusercontent.com/48141945/80667189-4dc69500-8a53-11ea-8e3e-ec233a8205fb.png)

### Description
The OPEnS-Hypnos board is a simple, low-cost circuit board that can be attached to an Adafruit Feather M0 microcontroller and a DS3231 real-time clock breakout board to enable shutting off power to the microcontroller until a timed or sensed event wakes it up.
In the early time of development, the Feather needs to be shut down completely due to the inefficient  deep sleep firmware.
A circuit was designed to keep the state of the system, and a real-time clock can change the state and wake everything back up.
After Adafruit released new firmware for Feather M0 that allows microamp sleep current, complete shutdown of the Feather seem unnecessary.
However, during deep sleep, the 3v3 volt regulator is still providing power to other peripherals. 
MOSFET circuitry is introduced in HYPNOS to cut down power to peripherals. Additional RTC and microSD for accurate timekeeping and data logging.

* `Hypnos V2.x` Power + RTC + microSD with FeatherWing footprint. Allow control on 3.3V and VUSB rail. Using MOSFET circuit and Feather deep sleep
* `Hypnos V3.x` Upgraded from regular Hypnos. Can control one more rail of higher voltage (9-24V) at max 1.2 A continuous
* `eDNA.lbr` Eagle library that has the push button, MOSFET footprints
* `powerboard.lbr` Eagle library that has FeatherWing pin layout

### Specification
* Controlled 3v3 Rail (0.4 A continuous) and 5V Rail (0.5 A continuous from USB)
* [RTC DS3231](https://datasheets.maximintegrated.com/en/ds/DS3231.pdf) with TCXO
* Back up power CR1220 for RTC
* Micro SD slot

### Pinout for Feather M0
* RTC INTerrupt pin: GPIO 12
* 3.3V control pin: GPIO 5
* 5V control pin: GPIO 6
* SD chip select: GPIO 10

### Update from Version 1:
* 2 power indicator LEDs for 3V and 5V
* RTC is now powered from 3V3 instead of Vbat (using power from Vbat turns on Feather Battery Charger LED)
* Rounded PCB corner
* Move the reset button to the middle of the board
* Add solder jumper for RTC-INT, normally connected
* Use all logic MOSFET

### Note
* 5Vrail can go up to 1.2A if external 5V is connected directly to **Feather USB pin**
* The LEDs are low power (rated at 2mA instead of 20mA)
* I2C line pull up is attached to 3VRail