# UAV-Serial-Bridge

This is a marriage of ESP32-Serial-Bridge by AlphaLima and WiFiManager by tzapu. It is functional, even if the code is perhaps a bit messy (still working on that). I suggest using COM1. Connect GPIO16 of the ESP32 to the TX pad on your flight controller and connect GPIO17 to the RX pad on your flight controller. Set the BAUD rate of the UART on your flight controller to 115200. 


Used Ports:                                                                                                          
192.168.4.1:8880  <-> COM0                                     
192.168.4.1:5760  <-> COM1                                     
192.168.4.1:8882  <-> COM2                                     

===============================================================

Used Libraries: (must be installed in the arduino IDE):

https://github.com/espressif/arduino-esp32
https://github.com/tzapu/WiFiManager


===============================================================

Use Arduino IDE to flash the .ino file onto your ESP32. Upon booting up, you will be able to connect to your ESP32 via WiFi via the SSID called "AutoConnectAP." This will automatically launch a browser window where you can select the WiFi network you want to connect your ESP32 to. Select the WiFi SSID and provide the password. Once your ESP32 is connected to WiFi, you will need to determine what it's IP address is (more instructions later, but you should be able to figure this out). Once your WiFi network is selected, you will be able to connect to the ESP32 with your chosen mission planner via TCP at port 5760 at the IP address of your ESP32.

The ESP32 will automatically attempt to connect to the Wifi network you selected at ever bootup. If it can't connect to it, you will be able to connect to the "AutoConnectAP" SSID again and select a different WLAN to connect to.

===============================================================

In some cases the memorylayout is to small for this scetch.
If you face this problem you can either disable Bluetooth by removing
#define BLUETOOTH
in config.h 
or change the partition size as described here:
https://desire.giesecke.tk/index.php/2018/04/20/change-partition-size-arduino-ide/

Arduino hardware configuration:

https://github.com/AlphaLima/ESP32-Serial-Bridge/blob/master/Settings.jpg

===============================================================

example usecases:

https://www.youtube.com/watch?v=K2Hia06IMtk

https://www.youtube.com/watch?v=GoSxlQvuAhg

# Hardware
here is the wiring diagram recomendation:
https://raw.githubusercontent.com/AlphaLima/ESP32-Serial-Bridge/master/ESP32-SerialBridge.jpg             
Pinning                                                                                     
COM0 Rx <-> GPIO21                                                                               
COM0 Tx <-> GPIO01                                                                                 
COM1 Rx <-> GPIO16                                                                               
COM1 Tx <-> GPIO17                                                                              
COM2 Rx <-> GPIO15                                                                               
COM2 Tx <-> GPIO04                                                                              

NOTE: The PIN assignment has changed and may not look straigt forward (other PINs are marke as Rx/Tx), but this assignment allows to flash via USB also with hooked MAX3232 serial drivers.

I recomend to start your project with a Node32s or compatible evaluation board. For a TTL to RS232 level conversion search google for "TTL RS3232 Converter"



https://tech.scargill.net/wp-content/uploads/2017/05/ESP326.jpg


