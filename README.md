This is a detailed description of how to send data from NodeMCU or ESP8266 to Google Firebase

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

![image](https://user-images.githubusercontent.com/55460620/160307963-4683daa6-2a6b-40d3-a1d6-5773c27a48a7.png)

# Step 3:  
After all necessary hardware connections, what you want to do is to configure Google Firebase to receive data from your EXSP8266, to access Google Firebase, open your browser and head over to firebase.google.com, and click on Get Started. You will be directed to the console where you can add new project, click on Add Project to create a new project.

![image](https://user-images.githubusercontent.com/55460620/160308054-ae4ecdc2-6001-451a-9088-34e16b5df758.png)

![image](https://user-images.githubusercontent.com/55460620/160308068-0ef928b4-8a2d-4b7d-8b0f-5452f98b5a5a.png)

# Step 4: 
After clicking on Add project, you will be asked to give your project a name, type in a suitable name for your project and click on Continue. This is step 1, on step 2 page, leave everything as default and lastly on step 3, select an account for your project, this will usually be the google account you are using for firebase. Click on continue  and allow firebase to finish setting up your project.

![image](https://user-images.githubusercontent.com/55460620/160308085-e4fa7cff-f72c-4b18-ba28-e45febf355c7.png)

![image](https://user-images.githubusercontent.com/55460620/160308089-1ebb13b2-a689-489b-9e2a-9860a6757a44.png)

![image](https://user-images.githubusercontent.com/55460620/160308095-3394b66e-9f01-4e55-9159-6532cd3094ec.png)

# Step 5: 
After creating your project, you will be presented with the Firebase working console, here we will be configuring authentications and also setting up the Realtime database. Before creating our database, we need to define set rules on how to authenticate users sending data to our database, on the side bar, click on Authentication and click on Get Started.

![image](https://user-images.githubusercontent.com/55460620/160308126-6f353c18-2616-4c72-a157-9cda40c4ac6b.png)

![image](https://user-images.githubusercontent.com/55460620/160308133-ec3cd438-c60c-4d86-9f25-4307276ea70f.png)

Click on Email/Password as sign in option and enable both Email/Password and Email Link, click save when you are done.

![image](https://user-images.githubusercontent.com/55460620/160308145-719efcfa-d2e8-4128-9524-6dad2638d5de.png)

![image](https://user-images.githubusercontent.com/55460620/160308152-8e844bb1-0487-42a0-a579-278f5b001520.png)

![image](https://user-images.githubusercontent.com/55460620/160308160-e51df325-1a4a-44df-a429-2ded73275d35.png)

# Step 6: 
Go back to Users and Click on Add User, enter both the user email and password you want the user to use in accessing the database, note these details somewhere as we will be using it in the code. With this, we are done with authentications.

![image](https://user-images.githubusercontent.com/55460620/160308172-aec938b4-cfef-4557-b72b-b70afc5a3b16.png)

![image](https://user-images.githubusercontent.com/55460620/160308179-dd0cd5b7-70fd-4bb0-8b54-d225876d9fbb.png)

# Step 7: 
From the side bar again, click on Realtime Database and click on Create Database. Select a region for your project, you will then be asked on which mode your project should start between Locked Mode and Test Mode. In test locked mode, both read and write access is set to false by default, you can change this later to true while in test mode, read and write access is set to true for some time, in this project, I will start with test mode. With that, our database has been set up.

![image](https://user-images.githubusercontent.com/55460620/160308196-8cd74537-d92e-44b2-adce-87650ac42712.png)

![image](https://user-images.githubusercontent.com/55460620/160308202-d35e3681-9785-4354-a01b-d2f804755d74.png)

![image](https://user-images.githubusercontent.com/55460620/160308207-91d58862-613f-4792-98f1-93afd3232669.png)

![image](https://user-images.githubusercontent.com/55460620/160308215-06c530ff-8c7b-406b-8408-bdeb65e151a6.png)

# Step 8: 
Wow, that was quite a set up. Now is the coding time. The source code can be found at https://github.com/adesolasamuel/ESP8266-NodeMCU-to-Google-Firebase , due to lots of complications while trying to set up this tutorial, I will be stating the version of all tools I used in case you are finding it difficult, just stick to the version I am using and there should not be a problem. To start with, I was working on Arduino IDE 1.8.13. From board managers, download ESP8266 of which I am using version 3.0.2 for this tutorial, due to reasons I do not know, firebase library I downloaded from Library manager was not working so I had to download it from GitHub, https://github.com/adesolasamuel/Firebase-ESP8266 which was version 3.9.5 at the time of writing this guide. Download the library ZIP file and add it to Arduino IDE through the library manager. 

![image](https://user-images.githubusercontent.com/55460620/160308254-252c03db-e46b-4b73-b509-df1bb53f1273.png)

![image](https://user-images.githubusercontent.com/55460620/160308258-cfd07b21-56eb-485a-b6df-6dbddc58424a.png)

Also, since we are reading DHT11 data, download a Adafruit library for reading DHT Sensor data from Arduino IDE library manager. After installing all necessary dependencies, you can start editing the credentials to suite your board and network.

![image](https://user-images.githubusercontent.com/55460620/160308281-4f93148d-5be0-4d01-bfed-82de2f256b74.png)

# Step 9: 
Change the WIFI SSID and Password to your network’s own. To get your API key, go back to firebase, click on the gear icon to go to project setting, on the general tab, you will see the web API displayed, copy it and paste it in the Arduino code. 

![image](https://user-images.githubusercontent.com/55460620/160308295-dfcc92c2-ca5e-4097-bf92-3692ccca793e.png)

![image](https://user-images.githubusercontent.com/55460620/160308304-42d4e02c-24be-4b64-a428-02391f695601.png)

![image](https://user-images.githubusercontent.com/55460620/160308311-8fc9b7ec-4c39-49b2-9d5b-5801e7cbc672.png)

To get your database URL, go back to Realtime database and copy the URL displayed on top of the database without the https. 

![image](https://user-images.githubusercontent.com/55460620/160308327-a33f02bb-fd65-490a-a5ea-776e47e8ef8d.png)

For user email and password, input the email and password that was defined during authentication. 
# Step 10: 
Study the code and note the line responsible for sending DHT data to cloud, verify the code and upload it, open the serial monitor and you will see data being sent, also, check your Firebase to read the data Realtime.

![image](https://user-images.githubusercontent.com/55460620/160308350-cdcf61ee-c890-40ba-9095-fd16c6444292.png)

![image](https://user-images.githubusercontent.com/55460620/160308359-6dd4b60a-c897-42d5-9847-bee8c13b47fc.png)

FOR VIDEO GUIDE, GO TO: https://www.youtube.com/watch?v=7VXbVHssiQU 
