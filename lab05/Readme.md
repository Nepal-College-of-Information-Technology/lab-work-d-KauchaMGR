# Lab 5: Integrating ESP32 Sensor Data with Cloud-Based REST API and Dashboard Visualization

## 1. Objective

1)Interface the DHT11 or DHT22 temperature and humidity sensor with the ESP32 or ESP8266.

2)ead and display sensor data on the Serial Monitor.

3)Review the REST API developed and deployed on the AWS EC2 instance in Lab 2.

4)Transmit sensor data from the ESP32 to the cloud using the REST API over the EC2 instance's public IPv4 address.

5)Store the uploaded sensor data in the cloud database.

6)Retrieve the stored sensor data through the REST API.

7)Visualize real-time and historical sensor data using the dashboard developed in Lab 3.

8)Understand the complete data flow from an IoT device to cloud storage and visualization.


## 2. Background Theory

### 2.1 ESP32 Microcontroller

The ESP32 is a low-cost, low-power microcontroller developed by Espressif Systems. It features:

- Built-in Wi-Fi and Bluetooth
- Dual-core processor
- Multiple GPIO pins
- Support for HTTP, MQTT, I2C, SPI, UART, and ADC

Its integrated Wi-Fi capability makes it an ideal platform for Internet of Things (IoT) applications.

### 2.2 DHT22 Temperature and Humidity Sensor

The DHT22 (AM2302) is a digital temperature and humidity sensor that provides:

- High accuracy
- Wide measurement range
- Stable digital output

The sensor communicates with the ESP32 through a single-wire digital communication protocol.
### 2.3 Sensor Data Acquisition

Sensor data acquisition is the process of collecting data from physical sensors (such as temperature, humidity, motion, or cameras) and converting it into a digital format that a computer or microcontroller can process. It is the first step in any IoT system, enabling real-world information to be monitored and analyzed.

### 2.4 Serial Communication

Serial communication is a method of transmitting data one bit at a time between two devices over a communication channel. Common protocols include UART, SPI, and I²C. It is widely used for communication between microcontrollers, sensors, and computers due to its simplicity and reliability.

### 2.5 REST API Communication

A REST (Representational State Transfer) API is a web-based interface that allows different applications or devices to communicate over the internet using HTTP. In IoT systems, devices send sensor data to a server or request information from it through REST APIs, enabling seamless data exchange.

In this experiment:

- ESP32 acts as the client.
- AWS EC2 hosts the REST API.
- Sensor readings are uploaded using **HTTP POST** requests.
- Stored data is retrieved using **HTTP GET** requests.
 ### 2.6 HTTP POST and GET Methods

HTTP methods define how a client interacts with a server:

GET is used to retrieve data from the server without modifying it.
POST is used to send data to the server, such as uploading sensor readings or images.
These methods are the foundation of communication between IoT devices and web servers.
5. Cloud Data Storage on AWS EC2

AWS EC2 (Amazon Elastic Compute Cloud) is a cloud computing service that provides virtual servers for hosting applications and storing data. In IoT systems, sensor data can be transmitted to applications running on an EC2 instance, where it is processed, stored in a database, and made accessible for monitoring and analysis from anywhere.





### 2.8 IoT Data Flow

The complete IoT workflow is shown below.

```text
DHT22 Sensor
      │
      ▼
    ESP32
      │
      ▼
 Wi-Fi Network
      │
      ▼
 REST API (AWS EC2)
      │
      ▼
 Cloud Database
      │
      ▼
 Dashboard
```

## 3. Components Required

| Component | Quantity |
|-----------|---------:|
| ESP32 Development Board | 1 |
| DHT22 Sensor | 1 |
| Breadboard | 1 |
| Jumper Wires | As Required |
| Micro USB Cable | 1 |
| Arduino IDE | Installed |
| AWS EC2 REST API | Running |
| Dashboard | Developed in Lab 3 |

## 4. Circuit Connection

The DHT22 sensor is connected to the ESP32 using GPIO4.

| DHT22 Pin | ESP32 Pin |
|-----------|-----------|
| VCC | 3.3V |
| DATA | GPIO4 |
| GND | GND |

### Circuit Diagram:
<img width="956" height="670" alt="image" src="https://github.com/user-attachments/assets/f7905ab7-2173-4c83-a5a2-77f476c82699" />



## 5. Procedure

1. Connect the DHT22 sensor to the ESP32.
2. Install the required Arduino libraries.
3. Upload the ESP32 program.
4. Verify the sensor readings using the Serial Monitor.
5. Connect the ESP32 to the Wi-Fi network.
6. Configure the REST API endpoint.
7. Send the sensor readings to the AWS EC2 REST API.
8. Verify that the readings are stored in the cloud database.
9. Open the dashboard.
10. Observe the real-time and historical sensor data.

## 6. ESP32 Program

```cpp

#include <WiFi.h>
#include <HTTPClient.h>
#include <DHT.h>

#define DHTPIN 4
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

const char* ssid = "Suraj";
const char* password = "suraj@123312";

const char* serverUrl = "http://100.48.81.73/weather/sensor-data";

void setup() {

    Serial.begin(115200);

    dht.begin();

    WiFi.begin(ssid, password);

    while (WiFi.status() != WL_CONNECTED) {
        delay(500);
    }

    Serial.println("WiFi Connected");
}

void loop() {

    float temperature = dht.readTemperature();
    float humidity = dht.readHumidity();

    if (!isnan(temperature) && !isnan(humidity)) {

        if (WiFi.status() == WL_CONNECTED) {

            HTTPClient http;

            http.begin(serverUrl);

            http.addHeader("Content-Type", "application/json");

            String payload =
                "{\"temperature\":"
                + String(temperature)
                + ",\"humidity\":"
                + String(humidity)
                + "}";

            http.POST(payload);

            http.end();
        }

        Serial.print("Temperature: ");
        Serial.println(temperature);

        Serial.print("Humidity: ");
        Serial.println(humidity);
    }

    delay(10000);
}

```


## 7. Experimental Results



### 7.1  Dashboard

The dashboard displays the temperature and humidity values received from the REST API.

<p align="center">
  <img width="1372" height="655" alt="image" src="https://github.com/user-attachments/assets/73ac8fb0-e16c-48d8-a0e7-472c61706545" />

  <br>
  <em>Figure 3: Temperature Dashboard</em>
</p>

### 7.2 Humidity  and temperature Dashboard

The dashboard displays the humidity values stored in the cloud database.

<p align="center">
  <img width="1088" height="1600" alt="dashboard" src="https://github.com/user-attachments/assets/71939457-6b73-412c-9401-f11002393f91" />

  <br>
  <em>Figure 4: Humidity and Temperature Dashboard</em>
</p>

## 8. Results

The experiment successfully demonstrates:

- Successful interfacing of the DHT22 sensor with ESP32.
- Accurate acquisition of temperature and humidity readings.
- Wi-Fi communication using ESP32.
- Uploading sensor data to the AWS EC2 REST API.
- Storage of readings in the cloud database.
- Retrieval of stored readings through the REST API.
- Real-time dashboard visualization.
- Historical trend analysis of temperature and humidity.

## 9. Learning Outcomes

After completing this experiment, students are able to:

- Interface digital sensors with ESP32.
- Read environmental data from the DHT22 sensor.
- Use HTTP POST and GET requests.
- Send JSON data to a cloud REST API.
- Store IoT data in a cloud database.
- Visualize sensor data using a web dashboard.
- Understand the complete IoT data pipeline.

## 10. Conclusion

This experiment successfully demonstrates a complete Internet of Things (IoT) pipeline. The ESP32 collects temperature and humidity data from the DHT22 sensor, transmits it over Wi-Fi to a REST API hosted on an AWS EC2 instance, stores the readings in a cloud database, and visualizes both real-time and historical data through an interactive dashboard. The implementation validates reliable end-to-end communication between an embedded device and cloud services.

## 11. Workflow

```css
Read Sensor Data
        │
        ▼
ESP32 Processing
        │
        ▼
Wi-Fi Connection
        │
        ▼
HTTP POST Request
        │
        ▼
AWS EC2 REST API
        │
        ▼
Cloud Database
        │
        ▼
HTTP GET Request
        │
        ▼
Dashboard Visualization
```
