Update to 0.15.3  

# WLED Build For SP530E  
Prepare UART Converter  
Download custom_build.bin  
Download ESPtool [Here](https://github.com/espressif/esptool/releases)  
Download C3_bootloader.bin and C3_partitions_4M.bin [Here](https://github.com/Aircoookie/WLED/releases/tag/v0.15.0-b2)  
  
  
## Connect UART Cable to board reverse side  
## Use this Command below to backup the original firmware.  
esptool read_flash 0 0x400000 sp530e-encrypted.bin  

##  Use this Command below to flash the custom firmware.
###  Please replace `0.xx.x` in the command below with the actual version number you downloaded (e.g., `0.15.3`)    
esptool write_flash --encrypt 0x0 C3_bootloader.bin 0x8000 C3_partitions_4M.bin 0x10000 custom_build.bin  

## I/O Pins:  
On Board Button GPIO 8  
On Board Mic GPIO 3  
On Board Blue LED GPIO 0 (Inverted)  
On Board Green LED GPIO 1 (Inverted)  
LED DAT Output GPIO 19  
### Analog Pins:  
R: GPIO 10  
G: GPIO 7  
B: GPIO 6  
WW: GPIO 5  
CW: GPIO 4 
