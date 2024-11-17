## EXPERIMENT-05-TRANSFERRING-DATA-TO-IOT-NETWORK-USING-API-KEY
#### NAME: HARISH RAGAV S
#### REGISTER NUMBER:212222110013
#### DEPARTMENT:CSE(IOT)
#### YEAR:3rd
## Aim:
To transfer sensor data to an IoT platform (ThingSpeak) using an API key.

## Apparatus Required:
ThingSpeak Channel ID and Write API Key: A valid ThingSpeak account and API key.
Microcontroller (e.g., ESP32/ESP8266, NodeMCU, etc.): For collecting sensor data and transmitting it to ThingSpeak.
Sensor Modules (e.g., Temperature, Humidity, etc.): For data collection.
Computer System: For writing and uploading the code to the microcontroller.
Internet Connection: To send the data to the ThingSpeak platform.
Theory:
IoT networks enable the exchange of data between devices through the internet. ThingSpeak is an IoT analytics platform that allows users to collect, store, and visualize sensor data using API keys. In this experiment, we use the ThingSpeak API to send sensor data periodically, allowing remote monitoring and analysis.

## Procedure:
Setup ThingSpeak Channel:

Create a ThingSpeak account and generate a channel with the required fields (e.g., temperature, humidity).
Obtain the Write API Key for your channel, which is used for sending data.
Setup the Microcontroller and Sensors:

Connect the required sensors (e.g., temperature sensor, humidity sensor) to the microcontroller.
Ensure the microcontroller is connected to the internet (using Wi-Fi or Ethernet).
Code for Sending Data:

Write a Python script (or Arduino code, depending on the platform) to read data from sensors.
Construct the URL to send data to ThingSpeak using the API key and channel ID.
Use the requests library to send HTTP POST requests containing sensor data to ThingSpeak.
Code Implementation: Here’s the Python code that reads sensor data and sends it to ThingSpeak:

## python
```
import requests
import time

channel_id = "2746386" 
write_api_key = "Y7Z3LY03ACK6SC0T"  
url = f"https://api.thingspeak.com/update?api_key={write_api_key}"

field_1 = 23.5  
field_2 = 65    

payload = {
    'field1': field_1,
    'field2': field_2
}

def send_to_thingspeak(payload):
    try:
        response = requests.post(url, params=payload)
        if response.status_code == 200:
            print(f"Data sent successfully: {payload}")
        else:
            print(f"Failed to send data. Status Code: {response.status_code}")
    except Exception as e:
        print(f"Error: {e}")

while True:
    send_to_thingspeak(payload)
    time.sleep(3)  
```
Execute the Program:

Run the Python script on your computer or upload the corresponding code to your microcontroller.
The data will be sent to ThingSpeak every 15 seconds, and you can visualize it on the ThingSpeak platform.
Monitor Data on ThingSpeak:

Visit your ThingSpeak channel’s dashboard to view the real-time data being sent from the sensors.
## Outputs:
![Screenshot (294)](https://github.com/user-attachments/assets/f16fa0f8-6780-4ff5-8441-290c4dbfcef0)

Sensor Data Visualization: The sensor data will be updated on the ThingSpeak dashboard in real-time.

![Screenshot (293)](https://github.com/user-attachments/assets/67894b90-52e7-4c27-9f73-bb9abccdff76)

Console Output: The console will print a success message for each data transfer, indicating the status (success or failure).

## Results:
The sensor data was successfully transferred to the ThingSpeak IoT platform using an API key. The experiment demonstrated how to send data from sensors to an IoT network and visualize it remotely using ThingSpeak. The periodic data updates were successfully logged and displayed on the ThingSpeak platform.
