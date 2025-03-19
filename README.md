# RFID reader test

code to test RFID-RC522 and/or PN532 NFC RFID (both 13,56 MHz)
Including communication with a simple python server through MQTT (optional).
Code for two leds included, will light up when a tag is read, can skip it.

Fill in (both c++ code and python code) WiFi and MQTT credentials:

const char* ssid = ""; <p align="middle">// wifi ssid  (has to be exact, otherwise, won't connect)</p> 
const char* password = "";     // wifi password
const char* mqtt_server = "";  // your wifi ip address

The code will first search for available WiFi nearby, and then connect to both WiFi and MQTT, then it's ready for reading. The code is adjusted for two readers. Remove or add more readers at will.

relevant datasheets:
RFID RC522
https://www.handsontec.com/dataspecs/RC522.pdf

PN532 NFC RFID
https://www.elechouse.com/elechouse/images/product/PN532_module_V3/PN532_%20Manual_V3.pdf

ESP32-WROOM-32
https://www.edu.xunta.gal/centros/ieslaxeiro/system/files/ESP-32%20Dev%20Kit%20C%20V2_EN.pdf

# RFID-RC522
Use the code for RC522 in src. 

circuit (shown for one reader):
![circuit_image](https://github.com/user-attachments/assets/5d2bf677-8822-41b8-a4c7-97af51176256)

RFID RC522 Pins    	ESP32 Pins
1 +3.3V	              +3.3V
2	RST	                 G0
3	GND	                 GND
4	MISO	               19
5	MOSI	               23
6	SCK	                 18
7	SS/SDA               5 (if using two readers, set the other one to 4)

(LED optional, but if used, should connect the anod in series with a 1k resistor)
8 LED                  16
9 LED                  17
