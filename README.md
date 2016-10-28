# max31856
MicroPython Library for new MAX31856 (Precision Thermocouple to Digital Converter with Linearization) with 19-Bit Thermocouple Temperature Resolution. This chip provides a SPI digital interface for Thermocouple Types B, E, J, K, N, R, S or T. 

A "ripoff" of the original work of Stephen P. Smith. Original code is here: https://github.com/steve71/MAX31856

Tested with:
 - MicroPython 1.8.5
 - Adafruit Feather HUZZAH with ESP8266 WiFi: https://www.adafruit.com/product/2821
 - Thermocouple Type-K Glass Braid Insulated: https://www.adafruit.com/product/270
 - Adafruit Universal Thermocouple Amplifier MAX31856 Breakout: https://www.adafruit.com/product/3263
 
 Connections:
 
 Feather HUZZAH ESP8266  GND to MAX31856 GND
 Feather HUZZAH ESP8266  3.3V output to MAX31856 Vin (voltage input)
 Feather HUZZAH ESP8266  SCK (serial clock, GPIO14) to MAX31856 SCK (serial clock)
 Feather HUZZAH ESP8266  MISO (master input, GPIO12) to MAX31856 SDO (serial data output)
 Feather HUZZAH ESP8266  MOSI (master output, GPIO13) to MAX31856 SDI (serial data input) 
 Feather HUZZAH ESP8266  GPIO15 to MAX31856 CS (chip select)
 
 
To upload the module on ESP8266 use (on MacOS) "ampy --port /dev/tty.SLAB_USBtoUART put max31856.py" or WebREPL: https://docs.micropython.org/en/latest/esp8266/esp8266/quickref.html#webrepl-web-browser-interactive-prompt

Example code to test the MAX31586 on ESP8266:

import time
csPin = 15
max = max31856.max31856(csPin)
while True:
 thermoTempC = max.readThermocoupleTemp()
 print ("Thermocouple Temp: %f degC" % thermoTempC)
 juncTempC = max.readJunctionTemp()
 print ("Cold Junction Temp: %f degC" % juncTempC)
 time.sleep(1)





