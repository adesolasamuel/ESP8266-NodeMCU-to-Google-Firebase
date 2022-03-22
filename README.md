This is a detailed description of how to send data from NodeMCU or ESP8266 to Microsoft Azure IoT Central

How to send data to Microsoft Azure IoT central Using NodeMCU

Link to step by step Video: https://youtu.be/7VXbVHssiQU

IoT being an integral part of cloud computing, several cloud vendors make IoT part of the services they render. Also, with the emergence of IoT, there are different platform that makes IoT implementation available even to individuals. In this tutorial, I will be taking you through steps in sending data from NodeMCU, an IoT development platform to Google Firebase. To ensure all necessary things are in place, you will have to set up your computer to communicate with NodeMCU or ESP8266 before you can follow along this tutorial. In this tutorial, we will be using DHT 11 sensor to send Temperature and Humidity data to Azure IoT Central. Materials Needed

NodeMCU or ESP8266
DHT 11 sensor
10K resistor
Personal Computer
Arduino IDE software
Jumper Wires
Step 1: The very first step is to ensure that your PC has been configured to communicate with ESP 8266. If you haven’t did this already, now is the time. Once you have configured your PC, come right back to continue following this tutorial. Step 2: Hardware Setup: Connect the NodeMCU and the DHT 11 to the breadboard, depending on your model of DHT 11, it can be a 3-pin ready made model or a 4-pin model, in this tutorial, I am using a 3-pin model. If you are using a 3-pin model, connect the VCC to 3V of the NodeMCU, GND of the DHT 11 to GND on the NodeMCU and connect the data pin to Pin 4 of the NodeMCU. If it is 4-pin model you are using, connect Pin 1 of the DHT11 to 3V of the NodeMCU, connect the 10K resistor between pin 1 and pin 2 of the DHT 11, leave pin 3 of the DHT 11 sensor unconnected and connect pin 4 of the DHT 11 to GND on the NodeMCU. Connect the NodeMCU via a USB cable to your computer and you are good to go.
