#nrf8001-ble-uart-spark-io

Bluetooth low energy as UART for Spark Core (uses the nRF8001 from [Nordic Semiconductor](https://www.nordicsemi.com/ "Go to Nordic Semiconductor's homepage")). 

##Contents
The firmware folder contains the library, with the entire user interface defined in nrf8001-ble-uart-spark-io.h.
An example of usage can be found in /firmware/examples, structured as a simple Arduino sketch.

##Background
This library is a port from Nordic Semiconductor's [Bluetooth Low Energy for Arduino SDK](https://github.com/NordicSemiconductor/ble-sdk-arduino "Go to BLE for Arduino GitHub repository").
Tested with the RedBearLab Bluetooth Low Energy Shield v2.0.

##Connecting the nRF8001 to the Spark Core
The nRF8001 communicates with the Spark Core via SPI, acting like a slave.
Connect the Spark Core to the RedBearLab Bluetooth Low Energy Shield using this pin configuration:

| BLE Shield		| Spark Core	|	Explanation |
| --------- | ----------- | ----------- |
| MOSI 			| A5					| SPI Master Out, Slave In |
| MISO			| A4					| SPI Master In, Slave Out |
| CLK				| A3 					| SPI Bus clock |
| REQN			| D4					| SPI Master request line |
| RDYN			| D3					| SPI Slave ready line |
| RESET			| D2					| nRF8001 reset signal (triggered in the library setup) |
| VIN				| 3V3					| Main voltage supply for the nRF8001 |
| GND				| GND					| Voltage supply for the nRF8001 radio |

##Running the example
The library contains an example Sketch called "nrf8001-ble-uart.ino". This example displays the most basic use case for the library, and lets you communicate with a terminal application on your computer through the Spark Core over BLE.

###Terminal 
You will need a two way terminal application on your computer in order to communicate with the Spark Core (You can use [Termite](http://www.compuphase.com/software_termite.htm "Go to the Termite project home page") from Compu Phase, it is free)

You have to open the COM-port to the Spark Core before you either flash or reset your device.

Set up your terminal application with the following parameters:

| Field | Value |
|-------|-------|
| Port: | The COM-port your Spark Core is on. If you have the Spark CLI, this can be found with the command line command "spark serial list" |
| Baud rate: | 115200 |
| Data bits: | 8 |
| Stop bits: | 1 |
| Parity:    | None |
| Flow control: | None |

You should also append LF ('\n') to your messages (available as an option in most terminal applications).

###Flashing your Code

In the Spark.io Build IDE, Press "Libraries" in the bottom left corner, find the nrf8001-ble-uart-spark-io library, and press "INCLUDE IN APP".
Copy the code in "nrf8001-ble-uart.ino" over to your project sketch, and flash it onto your Spark Core with the lightning button on the left.

Your Spark Core should start flashing purple for a while, and start breathing cyan. This means it's active, and if you've done everything right, it should be on air!



The example can be used with the "nRF UART 2.0" app for iOS/Android, available in the Apple App Store and Google Play Store. Note that this app requires a BLE-compliant device.

###Using the example with the App

Open the nRF UART 2.0 app, and press the "Connect" button near the top of the screen. You'll see a list of available BLE devices in your area. Press the "Spark Core". The app should show the message "Spark Core says hello!". This means you have a connection, and you can start communicating with your Spark Core.

##The next steps
You can use the interface functions in the nrf8001-ble-uart-spark-io.h file to communicate with the nrf8001.

##Forum
[Nordic Developer Zone](http://devzone.nordicsemi.com/ "Go to Nordic developer zone")

##Resources
[Spark.io](http://spark.io "Go to Spark.io homepage")  

[nRF8001](https://www.nordicsemi.com/eng/Products/Bluetooth-R-low-energy/nRF8001 "Go to product") (Data sheet for the nRF8001) 

[RedBearLab BLE Shield from MakerShed](http://www.makershed.com/Bluetooth_Low_Energy_BLE_Shield_for_Arduino_p/mkrbl1.htm "Go to product")  

[RedBearLab BLE Shield from SeeedStudio](http://www.seeedstudio.com/depot/bluetooth-40-low-energy-ble-shield-v20-p-1631.html "Go to product")  
