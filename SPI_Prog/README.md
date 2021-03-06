# STM32F4 Discovery SPI Programmer

It allows you to write different SPI flash memory by drag and drop the file in USB Mass Storage.
Created using Cube MX and Keil, also used source code <a href="https://github.com/flashrom/flashrom" rel="nofollow">Flashrom</a>

# Features

Hardware full-duplex SPI with DMA, multiple clock speeds available (SPI2), selected by pressing the button(one blink - 1313KHz....five blinks - 21000KHz)  :

  - 1313 KHz
  - 2625 KHz
  - 5250 KHz
  - 10500 KHz
  - 21000 KHz

 Verified flash memory chips :
 

  - AT26DF041, SST25LF040A, EN25F80, W25Q80, W25Q64, W25X80, W25X40, SST25VF512A, AT25F512A, M25P10-A, Pm25LD010(C), Pm25LV512(A), W25Q16, AT25F1024(A), MX25L6406E, NX25B40,  cFeon Q32b-104Hip, W25Q128BV, MX25L25645G, LE25FU206, LE25FW406A, LE25FU406B, M25P40, MX25L4005AM, MX25L8006E (chips of the same series but of a different size will also work).

    Any other chips need to be added to files "flashchips.c", "chip_drv.c", "spi.c".


Pins are used to connect the chip to the board:
 - SPI2_MISO Pin - PB14
 - SPI2_MOSI Pin - PB15
 - SPI2_SCK  Pin - PB13
 - SPI2_NSS  Pin - PB12

This can be changed in the file "RTE_Device.h".
If the LED 4 flashes after connecting the chip and powered, then the chip is identified and you can continue to work (press user button),
otherwise the LED 5 will be flash. After write the chip, the CRC will be checked. The erase-write-read process will be displayed using LED 3, 
if there were no errors, LED 4 will be flashed, otherwise LED 5 will be flash. You also need to pull-up the following  pins - WP, HOLD, DO.
After the first button pressing  the backup mode will be enabled, if you press the button again, the device switches to the update mode.
You do not need to format the disk, just drag-n-drop the file there, will work only in the Windows system (tested WinXp, Win7).
To display debug information set in file "usbd_conf.h" :
 - USBD_DEBUG_LEVEL             1
 - SPI_DEBUG_LEVEL              1
 
 Problems with Windows 10 - windows 10 creates a folder on the disk - "System Volume Information". To fix this:
   
   Step 1:
     Using GPEDIT to modify Do not allow locations on removable drives to be added to libraries setting:
   In Windows 10 / 8.1 Pro & Enterprise Editions, press Windows Key + R combination, type put gpedit.msc in Run dialog box 
   and  hit Enter to open the Local Group Policy Editor.
   Navigate here: Computer Configuration -> Administrative Templates -> Windows Components -> Search
   In the right pane, look for the setting named Do not allow locations on removable drives to be added to libraries and 
   double  click it.
   Click on Enabled and then click Apply followed by OK. Close the Local Group Policy Editor.
   
   Step 2:
     For Windows 10 this additional step is necessary. Go back to Run, type services.msc, click OK. In the right pane scroll 
   down  to Windows Search, double click it and in Startup type: select Disabled. Click OK and then close. Just to be 
   safe  reboot.
   
   Step 3:
     In addition, disable or stop the service - StorSvc (Service storage or  Служба хранилища), and disable "Autoplay".


  
# License

This software is provided under the  <a href="http://unlicense.org/" rel="nofollow">UNLICENSE</a>

