# STM32F4 Discovery SPI Programmer

It allows you to write different SPI flash memory by drag and drop the file in USB Mass Storage.
Created using Cube MX and Keil, also used source code <a href="https://github.com/flashrom/flashrom" rel="nofollow">Flashrom</a>

# Features

1 - Hardware full-duplex SPI with DMA, multiple clock speeds available (SPI2), selected by pressing the button(one blink - 1313KHz....five blinks - 21000KHz)  :

  - 1313 KHz
  - 2625 KHz
  - 5250 KHz
  - 10500 KHz
  - 21000 KHz

2 - Verified flash memory chips :
 
  - AT26DF041, SST25LF040A, EN25F80, W25Q80, W25Q64 (chips of the same series but of a different size will also work).
    Any other chips need to be added to files "flashchips.c" and "chip_drv.c".

Pins are used to connect the chip to the board:
 - SPI2_MISO Pin - PB14
 - SPI2_MOSI Pin - PB15
 - SPI2_SCK  Pin - PB13
 - SPI2_NSS  Pin - PB12
This can be changed in the file "RTE_Device.h".
If the LED 4 flashes after connecting the chip and powered, then the chip is identified and you can continue to work (press user button),
otherwise the LED 5 will be flash. After write the chip, the CRC will be checked. The erase-write-read process will be displayed using LED 3, 
if there were no errors, LED 4 will be flashed, otherwise LED 5 will be flash. You also need to pull-up the following  pins - WP, HOLD, DO.
You do not need to format the disk, just drag-n-drop the file there, will work only in the Windows system (tested WinXp, Win7).
  
# License

This software is provided under the  <a href="http://unlicense.org/" rel="nofollow">UNLICENSE</a>
