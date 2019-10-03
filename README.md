# OPEnS-Power
Power Control Board for microcontroller projects, designed at OPEnS Lab OSU.

The OPEnS Power board is a simple, low-cost circuit board that can be attached to an Adafruit Feather M0 microcontroller and a DS3231 real-time clock breakout board to enable shutting off power to the microcontroller until a timed or sensed event wakes it up.
In the early time of development, the Feather needs to be shut down completely due to the inefficient  deep sleep firmware.
A circuit was designed to keep the state of the system, and a real-time clock can change the state and wake everything back up.
After Adafruit released new firmware for Feather M0 that allow microamp sleep current, complete shutdown of the Feather seem unnecessary.
However, during deep sleep, the 3v3 volt regulator is still providing power to other peripherals. 
MOSFET circuitry is introduced in 3.3-volt version V3 to cut down power to peripherals. Additional RTC and microSD for accurate timekeeping and data logging.


* `Hypnos` Power + RTC + microSD with FeatherWing footprint. Allow control on 3.3V and Vbus rail. Using MOSFET circuit, Feather deep sleep
* `eDNA.lbr` Eagle library that has the push button
* `powerboard.lbr` Eagle library that has FeatherWing pin layout
