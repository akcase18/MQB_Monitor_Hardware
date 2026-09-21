# Versions
Just a place that I can keep track of what each version is at a high level.

### V1
First board design. Had MCU sandwiched between PCB and display. Touch didn't work

### V2
Effectively flipped board upside-down, so the MCU was located on the underside of the PCB. This allowed me to access the MicroMod Board without fully disassembling everything. Touch still didn't work, but modified the board to fix this issue (SPI lines were switched).

### V2.1
Never actually printed, but added the fix to the SPI lines so touch will work. Also added BOOT and RESET buttons.

### V3.0
Old display and PCB idea (standard headers, resistive touch) but with ESP32-C3 on-board, adding WiFi capability while retaining the same display for troubleshooting.

### V3.1
Small changes to fix some incorrect power supply assumptions for the Teensy.

### V4.0
Switch to a panel-only LCD instead of the LCD with a breakout board. Moved away from the standard 40-pin connector to a 50-pin ZIF-style connection. Much smaller board to minimize overall package size, designed to be affixed directly to the back of the LCD panel.

### V4.1
During bring-up of v4.0, found an issue with the decoupling capacitors that prevented display funcion. This was fixed. Additionally, the backlight driver was incorrect for the use-case, but that was not fixed in v4.1.