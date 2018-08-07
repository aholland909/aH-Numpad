# aHolland's Numpad Programming Guide (or how to flash a Pro Micro with .Hex files)

## Parts list
* 1x 	  Pro Micro
* 1x	  Computer

## Step 1 - Arduino 

Download Arduino IDE. This will give you avrdude.exe and the config file. 

## Step 2 - Path Variables

Once installed find the folder directory for avrdude, mine is: C:\Program Files (x86)\Arduino\hardware\tools\avr\bin. Add this into the PATH under user variables in the environmental variables. This will allow you run the avrdude command in command prompt. Also make sure you know where the avrdude.conf file is, mine is in: C:\Program Files (x86)”\Arduino\hardware\tools\avr\etc\avrdude.conf. We will need to program the Pro Micro.

## Step 3 - Hex Files/Code

Download either the 17key or 20key hex file from the repository. You can also upload the .json files to https://kbfirmware.com/. 

## Step 4 - Bootloader mode

Before you program your Pro Micro you need to put it into bootloader mode. To get your Arduino in this mode, short the ground to the rest pin.  Make sure to have a look in device Manager or Devices and printers and note down the new port that it gets when it's in bootloader mode. Bootload more last for about 10 seconds. 

## Step 5 - Programming 

Next navigate to the folder where you have your hex file by using command prompt and the cd command.  Then run the following command in command prompt, when the Pro Micro is in bootloader mode. 
```
avrdude -C”C:\Program Files (x86)”\Arduino\hardware\tools\avr\etc\avrdude.conf -v -p atmega32u4 -c avr109 -P COMX -b 57600 -D -U flash:w:FILENAME.hex
```
Replace ‘X’ with the COM port, for the Arudino when it is in bootloader mode.  Replace the ‘FILENAME’ with the hex file you want to flash.
