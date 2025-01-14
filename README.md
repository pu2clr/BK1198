# BK1198 Arduino Library

The BK1198 is a highly integrated digital signal processor (DSP) designed for AM/FM radio reception. Manufactured by Beken Corporation, it is a cost-effective solution commonly used in low-cost consumer radios, offering excellent performance with minimal external components. The BK1198 provides a simplified design for manufacturers while delivering high-quality audio reception across various radio bands.
One of the standout features of the BK1198 is its digital interface, which allows seamless communication with microcontrollers via the I2C protocol. This enables developers to control the radio’s settings programmatically, offering flexibility for custom applications.

## Integration with Arduino or Other Microcontrollers:

The BK1198 operates as an I2C slave device, making it simple to interface with microcontrollers like Arduino, ESP32, or Raspberry Pi.
Through I2C, the microcontroller can adjust frequencies, switch bands (AM/FM), control audio output, and manage other radio parameters.
Customization and Automation: This digital control capability makes the BK1198 suitable for DIY radio projects, automated scanning, or integration into larger systems requiring radio functionality.

This project is about an Arduino library for the BK1168 and is still under development, therefore not yet functional. At the moment, the author of this project has not obtained the necessary documentation to program the BK1198. The attempts to advance the project have been based on the author's experience with the BK1088.


## Main Features According to the Datasheet

1. **Supports FM frequency range from 60 to 112 MHz** - Allows tuning to FM radio stations within this range.  
2. **Supports AM frequency range from 504 to 1750 kHz** - Can tune to AM radio stations within this range.  
3. **Supports shortwave frequency range from 2.2 to 23 MHz** -  Enables listening to shortwave radio broadcasts.  
4. **Flexible configuration of operating modes** -  The device can be customized for different operating modes.  
5. **Automatic FM stereo/mono switching** -  Automatically switches between stereo and mono depending on signal quality.  
6. **Automatic noise suppression** -  Reduces noise automatically to improve audio quality.  
7. **Supports tuning with potentiometer or encoder** - Allows frequency tuning using a potentiometer or rotary encoder.  
8. **Channel adjustment by buttons (SSOP24 model)** - Enables station changes using buttons.  
9. **Digital frequency display function** - Displays the tuned frequency on a digital screen.  
10. **Line-in audio input (SSOP24 model)** - Includes an auxiliary input to connect other audio sources.  
11. **Operating voltage from 1.8 to 3.6 V** - Works with a low power supply between 1.8 and 3.6 volts.  
12. **Operating voltage from 1.8 to 3.6 V** - (Repeated for consistency).  
13. **LED indication for radio and stereo (SSOP24 model)** - The device can light LEDs to indicate stereo mode or radio signal reception.  
14. **Available in 24-pin SSOP and 16-pin SOP packages** - The chip is available in two different sizes depending on the application.  


UNDER CONSTRUCTION...



![BK1198 PINOUT](./extras/Images/Modification/RX_01/BK1198VM_PINOUT_05.jpg)


![Block Diagram](./extras/Images/Modification/RX_01/Block_Diag.jpg)


![Schematic](./extras/Images/Modification/RX_01/BASIC_CIRCUIT_WITH_VOLTAGE_DIVIDER.jpg)



# [PU2CLR BK1198 Arduino Library](https://pu2clr.github.io/BK1198/)

The BK1198 is a single-chip solution for receiving AM, FM, and shortwave radio. 
Using inexpensive components (Arduino Pro Mini, some push buttons buttons, and a standard OLED or TFT display), the  hobbyists can build serviceable little receiver based on BK1198 with a impressive performance.  

This project involves a cross-platform Arduino Library designed to control the BK1198 device. The BK108X Aerduino Library library is based on the documentation titled "BK1198 BROADCAST AM/FM/SW/LW RADIO RECEIVER; Rev.1.4" provided by BEKEN Corporation. Its purpose is to enable seamless control and integration of the BK1198 device within Arduino projects.

This library can be freely distributed using the MIT Free Software model. 

[Copyright (c) 2020 Ricardo Lima Caratti](https://pu2clr.github.io/BK1198/#mit-license). 

Contact: __pu2clr@gmail.com__.