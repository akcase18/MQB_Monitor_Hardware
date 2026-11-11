# Hardware Design for MQB Monitor

This is the PCB used for my software project, MQB Monitor, and enables the software features found in that repository.

This project was fully designed in KiCad, with the intention of using JLCPCB for both PCB manufacturing and assembly.

## Features

This project was designed to be a full plug-and-play compact display that could be used to show configurable information as reported by my car. I wanted installation to be easy and fully reversible, and require little-to-know technical knowledge in order to get it up and running.

To support this goal, this PCB is designed around a 480x320 3.5" LCD panel that supports capacitive touch, fast refresh rates, high-brightess, and is readily available. This allows the screen to be visible in a car in all but direct sunlight, react quickly to new information, and is glass-coated for better durablility and easier use. The PCB attaches directly to the back of the LCD panel (I use double-sided tape) for a secure and very compact package.

It utilizes a 4-wire connection to the car with a custom wiring harness that plugs directly into the OBD2 port. It pulls power, ground, and CAN (CAN high and low) directly from the port. Power is pulled from the ignition source, so the display turns on when the car turns on, turns off when the car turns off, and doesn't pull power while the car is off so there is no extra battey drain.

It also has a USB-C port on-board that can be used for updates and other communication with the MCU.

## Major Components

The full BOM can be found in the KiCad project, as well as in the `bom_production` folder, but the major components used for this are listed below. Please note, this information is only applicable to PCB v5.1.0.

- ESP32-S3-WROOM-1: This is the MCU for the project, and is what actually runs the display. For this board, it is recommended to use N16R8. See below for a more in-depth explanation.
  - There are multiple different flash configurations for this ESP module, indicated using N{X}R{Y}, where X is total flash storage and Y is the amount of PSRAM in the module. On v5.0.2 of this board, only N16R2 was supported because 1) N16 gives you maximum internal flash for logging purposes and 2) R2 uses quad SPI for PSRAM instead of octal SPI (which is used by other R configurations). THe pinout used for that PCB was not compatible with octal SPI PSRAM.
- PAM2804AAB010: LCD backlight driver. Used to control display brightness.
- PLMR54410DBVR: 12v -> 5v switching regulator, helps with overvoltage protection when connected to the car as well.
- AMS1117-3.3L: 5v -> 3.3v LDO, provides steady voltage source for display and MCU.
- SN65HVD230: Automotive CAN transceiver.
- ER-TFT035-6: LCD panel used. This connects to the PCB via 50-pin FPC connector, has a capacitive touch controller (via I2c), and is driven by the MCU using 8-bit parallel.

As mentioned, there are other supporting components used that are listed in the full BOM. There may be alternatives to some of the components on the board, but the components selected were chosen to minimize cost and maximize component availablilty, specifically for using JLCPCB for PCBA.