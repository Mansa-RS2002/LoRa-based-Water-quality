# LoRa-based-water-quality
To monitor the physical parameters of water such pH, turbidity, TDS, conductivity, temperature with the help of LoRa module and to analyze it's accuracy with help of ML algorithms such as SVM, Logistic Regression and ADA Boost Classifier.

This Project has 2 parts Transmitter and Receiver.

LoRa

The Transmitter side has an Arduino Uno and LoRa SX1278 433MHz Transceiver module.The sensors are connected to the Arduino with respect to digital and analog pins respectively along with common VCC and GND pins.

The transmitter code(TX.c) is to define the pin numbers,initialize sensors,define threshold values,continously collect data from sensors,show alerts if sensor value exceeds the threshold value and send it to LoRa on the transmitter side.It also has defined pins of LoRa that are connected to Arduino Uno to receive sensor data. Arduino sends the data to LoRa via SPI(Serial Peripheral Interface) where Arduino is the Master and LoRa is the Slave(Master Out Slave In)

TX.c code that runs in Arduino IDE collect's the data from the sensors and compares it with the defined threshold values and displays the sensor data and alerts in the Arduino IDE Serial Monitor(External LED or LCD Display can also be used)

The Receiver side is similar to the trnsmitter but instead of Arduino Uno we used Arduino Nano 33 IoT board which has inbuilt Wi-Fi support. The received data from the transmitter side is received through the LoRa module on the receiver's side and sent to Arduino Nano but this time MISO(Master In Slave Out) line is used.

The Receiver code(RX.c) is to define the Blynk components,receive sensor data.The LoRa module has similar pin connection that was on the transmitter side. Arduino Nano sends the data via Wi-Fi network(whose SSID and Password is defined in the program) to Blynk IoT Platform for better visualization of data.
