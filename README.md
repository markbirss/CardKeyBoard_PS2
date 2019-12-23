# CardKeyBoard PS / 2 interface version

![利用例](./image/top.jpg)  

## Introduction
This software is a firmware that makes CardKeyBoard for M5stak compatible with PS / 2 interface.
It is intended for use on microcomputer boards that use a PS / 2 keyboard. The operation with
IchigoJam V1.3 and Toyoshiki Tiny BASIC for Arduino STM32 V0.87 has been confirmed.

The implementation uses Arduino environment.
This firmware is developed by modifying the source of the original version of CardKeyBoard firmware.

Source of original version of CardKeyBoard

Github m5stack / M5-ProductExampleCodes
https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/CARDKB

You can undo by writing the above original version.

Please use this software freely. 


## Note
No liability can be assumed for CardKB becoming unusable using the book or software.
In addition, the manufacturer's warranty may not be received.
Please use it after remodeling and understanding of self-responsibility.

## Interface specifications
The original I2C interface has been changed to the PS / 2 interface.

![コネクタ](./image/02.png)  

|Terminal / conductor|  signal  |
|:--:|:--:|
|Black   |GND  |
|Red   |5V or 3.3V  |
|Yellow   |CLK/D+(A4)  |
|White   |DATA/D-(A5) |

When using a USB connector (male), connect the above wires to the following terminals. 
![USBコネクタ](./image/04.png)  

## Keyboard specifications
In the original version, the LED (NeoPixcel) flashes at startup, but does not flash in this firmware.

Please specify a Japanese keyboard for the keyboard used by the host computer.

The specifications and functions of the keyboard are almost the same as the original, but the
following key assignments are newly added.  

|Key function|  Operation  |
|:--|:--|
|[F1]|[1]＋[Fn]
|[F2]|[2]＋[Fn]
|[F3]|[3]＋[Fn]
|[F4]|[4]＋[Fn]
|[F5]|[5]＋[Fn]
|[F6]|[6]＋[Fn]
|[F7]|[7]＋[Fn]
|[F8]|[8]＋[Fn]
|[F9]|[9]＋[Fn]
|[F10]|[0]＋[Fn]
|[Insert]|[BS]＋[Fn]
|[Home]	|[←]＋[Fn]
|[PageUp]|[↑]＋[Fn]
|[カナ]	|[k]＋[Fn]
|[PageDown]	|[↓]＋[Fn]
|[End]|[→]＋[Fn]

[F1] to [F10] are function keys.   


## Prepare libraries required for compiling sketches
Adafruit NeoPixel Library Search and install "Adafruit NeoPixel" in the library manager of Arduino IDE.  
![ISP](./image/09.png)  

- ps2dev (Emulating a PS2 device)
 [PS2 mouse interface for Arduino](http://playground.arduino.cc/ComponentLib/Ps2mouse)
 
- Click and download **Attach: ps2dev.zip** at the bottom from PS2 mouse interface for Arduino .
- Unzip and place it under libraries in your Arduino environment .
- **Open ps2dev.cpp** in an editor, modify it #include "WProgram.h"to #include "Arduino.h", and save it.
- **Open ps2dev.h** in an editor, #include "WConstants.h"comment out ( //#include "WConstants.h") and save.

## Write firmware
Compile the attached sketch with Arduino IDE or write the compiled image file CardKeyBoard.ino.hex in the
bin folder using a tool such as avrdude . Programmers should use what they are accustomed to.

(Caution) Do not change the fuse bit.
If you are using ProgIsp , please disable the default Program Fuse setting.

Writing with Arduino IDE
Open CardKeyBoard.ino attached to this project in Arduino IDE.
In the Arduino IDE environment, specify Arduino Pro (3.3V 8MHz) as the board selection and write.

(Write operation of boot loader ([Tool]-[Write boot loader]) is prohibited.)

Since the board does not have a bootloader, writing by a programmer (ArduinoISP, USBasp, USBtinyISP, etc.) from the ICSP terminal is required.
Programmers should use what they are accustomed to.

Specifications of ICSP terminal on board

![ICSP](./image/01.png)  

By inserting a jumper into the above terminal, writing can be done simply by connecting.
(Please use a device such as fixing with tape)

![ICSP](./image/06.jpg) 
![CISP](./image/08.jpg)  

Example using USBtinyISP as a programmer

![ICSP](./image/07.jpg)  

Writing of the IDE menu [Sketch] - [writing using the writing device] in,
compile the sketch, writes.

Example of mounting a simple cable to connect via USB connector
This is an example of mounting a simple cable using a USB terminal (male) and jumper wires (male-male). 

![ICSP](./image/10.jpg)

Usage example of Toyoshiki Tiny BASIC for Arduino STM32 V0.87 

![ICSP](./image/11.jpg)

Akizuki electrons " cable mounting USB connector (A type male) ," the use was Example
(reinforcing the root with heat shrinkable tube + Ties)

![ICSP](./image/14.jpg)  

![ICddSP](./image/15.jpg) 
