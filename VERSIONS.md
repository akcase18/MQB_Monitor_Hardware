# Versions
Just a place that I can keep track of what each version is at a high level.

## v1

### v1.0.0
First board design. Had MCU sandwiched between PCB and display. Touch didn't work

## v2

### v2.0.0
Effectively flipped board upside-down, so the MCU was located on the underside of the PCB. This allowed me to access the MicroMod Board without fully disassembling everything. Touch still didn't work, but modified the board to fix this issue (SPI lines were switched).

### v2.1.0
Never actually printed, but added the fix to the SPI lines so touch will work. Also added BOOT and RESET buttons.

## v3

### v3.0.0
Old display and PCB idea (standard headers, resistive touch) but with ESP32-C3 on-board, adding WiFi capability while retaining the same display for troubleshooting.

### v3.1.0
Small changes to fix some incorrect power supply assumptions for the Teensy.

## v4

### v4.0.0
Switch to a panel-only LCD instead of the LCD with a breakout board. Moved away from the standard 40-pin connector to a 50-pin ZIF-style connection. Much smaller board to minimize overall package size, designed to be affixed directly to the back of the LCD panel.

This board was ordered and is currently in-use as a development board and for internal tools.

### v4.1.0
During bring-up of v4.0, found an issue with the decoupling capacitors that prevented display funcion. This was fixed. Additionally, the backlight driver was incorrect for the use-case, but that was not fixed in v4.1.

This board was never ordered.

## v5

### v5.0.0
Switch from the Teensy MM + ESP32-C3 MCU strategy to ESP32-S3 only. Need to rework the backlight driver that was not fixed in v4.1 as well.

### v5.0.1
Reworked layout of board to move the car connector. I want to support the AMPS mounting standard, which could cover the previous connector location.

### v5.0.2
Updated component selection to improve board robustness. Switched 12v --> 5v switching regulator to be safe up to 45v. Added some additional capacitors near components, and updated other capacitors to work better.

This board was ordered and is in initial user testing stages.

### v5.0.3
Fixed minor component footprint issues.

### v5.1.0
Switched ESP pins used for parallel display interface to be able to support ESP32-S3 with OctalSPI PSRAM instead of only QuadSPI PSRAM. Added TE connection from ESP to display. Removed unnecessary RESET button.