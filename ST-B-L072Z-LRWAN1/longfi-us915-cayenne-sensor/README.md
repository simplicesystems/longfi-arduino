# ST B-L072Z-LRWAN1 - Cayenne Example

This example demonstrates sending motion and environmental sensor data in [CayenneLPP](https://developers.mydevices.com/cayenne/docs/lora/#lora-cayenne-low-power-payload) format, using a B-L072Z-LRWAN1 development board with a X-NUCLEO-IKS01A3 expansion shield, to the myDevices Cayenne dashboard. For more information on adding your device to the Helium network, visit our quickstart guide [here](https://developer.helium.com/console/quickstart). For more information on adding your device to myDevices Cayenne, visit our guide [here](https://developer.helium.com/console/integrations/mydevices-cayenne-integration).

## Required Arduino Libraries

From the Arduino IDE, open the Library Manager (Sketch->Include Library->Manage Libraries). In the search box, type the library name below and install the latest version.

[MCCI Arduino LoRaWAN Library](https://github.com/mcci-catena/arduino-lmic)  
[CayenneLPP](https://github.com/ElectronicCats/CayenneLPP)  
[X-NUCLEO-IKS01A3](https://github.com/stm32duino/X-NUCLEO-IKS01A3)  

## Required Arduino Board Support

### B-L072Z-LRWAN1 - ST STM32L0 Discovery kit  
Install board support package, find instructions [here](https://github.com/stm32duino/Arduino_Core_STM32#getting-started).  

Arduino IDE:  
1. Select Tools -> Board: -> Discovery 
2. Select Tools -> Board part number: -> Discovery L072Z-LRWAN1 

## Required Hardware

### B-L072Z-LRWAN1 - ST STM32L0 Discovery kit

[B-L072Z-LRWAN1 Product Page](https://www.st.com/en/evaluation-tools/b-l072z-lrwan1.html)  
[B-L072Z-LRWAN1 User Manual](https://www.st.com/content/ccc/resource/technical/document/user_manual/group0/ac/62/15/c7/60/ac/4e/9c/DM00329995/files/DM00329995.pdf/jcr:content/translations/en.DM00329995.pdf)  

### X-NUCLEO-IKS01A3 - ST Motion MEMS and Environmental Sensor Board

[X-NUCLEO-IKS01A3 Product Page](https://www.st.com/en/ecosystems/x-nucleo-iks01a3.html)  
[X-NUCLEO-IKS01A3 User Manual](https://www.st.com/resource/en/user_manual/dm00601501-getting-started-with-the-xnucleoiks01a3-motion-mems-and-environmental-sensor-expansion-board-for-stm32-nucleo-stmicroelectronics.pdf)  
## Programming (Uploading Method):

#### STM32CubeProgrammer(SWD)
Will use onboard ST-Link(Flasher/Debugger) to upload sketch.  
Download and Install required utility from ST [here](https://www.st.com/en/development-tools/stm32cubeprog.html).  

Arduino IDE:  
Select Tools -> Upload Method -> STM32CubeProgrammer(SWD)

### PlatformIO Support 

The PlatformIO Board file for this board is currently using the incorrect OpenOCD (Upload/Debug)
script for the microcontroller on this board. We are in the process of pushing a fix upstream. When 
uploading or debugging, hold the reset button down right until the upload or debug process initiates 
it's routine in communicating with the board, this seems to aleviate the issue for right now.

`platformio.ini`
```
[env:disco_l072cz_lrwan1]
platform = ststm32
board = disco_l072cz_lrwan1
framework = arduino

lib_deps =
     STM32duino LSM6DSO
     STM32duino LIS2DW12
     STM32duino STTS751
     STM32duino LIS2MDL
     STM32duino LPS22HH
     STM32duino HTS221
     MCCI LoRaWAN LMIC library
     CayenneLPP
``` 