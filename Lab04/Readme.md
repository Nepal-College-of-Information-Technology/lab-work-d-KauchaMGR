# Lab 4: Different Types of IoT Sensors

## 1. Title : **Different Types of IoT Sensors**

## 2. Objectives
- Understand the concept and importance of IoT sensors.
- Identify and classify different types of IoT sensors.
- Study the basic functions of commonly used sensors in IoT systems.
- Learn how sensors are categorized based on physical parameters.
- Understand real-world applications of different IoT sensors.

## 3. Introduction
The **Internet of Things (IoT)** is a system of interconnected physical devices that communicate and exchange data over the internet. These devices rely heavily on **sensors** to interact with the physical environment.

Sensors act as the **"eyes and ears"** of IoT systems by detecting environmental changes and converting them into electrical signals. These signals are then processed to enable monitoring, automation, and intelligent decision-making.

## 4. Background Theory

### 4.1 Introduction to IoT Sensors
IoT sensors are electronic devices that detect changes in physical conditions such as temperature, humidity, light, motion, gas levels, and pressure. They convert these physical changes into measurable electrical signals.

<img width="1157" height="672" alt="image" src="https://github.com/user-attachments/assets/b84b20c2-9e69-4497-938d-c05e80752e90" />



### 4.2 Classification of IoT Sensors

#### A. Based on Physical Parameter Measured
- **Temperature Sensors** (LM35, DHT11)
- **Humidity Sensors**(DHT11)
- **Pressure Sensors** (BMP180)
- **Light Sensors** (LDR, Photodiode)
- **Motion Sensors** (PIR Sensor)
- **Gas Sensors** (MQ Series)

#### B. Based on Function
- Environmental Sensors (Temperature, Humidity, Air Quality)
- Motion Detection Sensors (PIR, Ultrasonic)
- Position Sensors (GPS, Accelerometer)
- Optical Sensors (Light, Infrared)

  ### 5.1 Temperature Sensors
Temperature sensors measure heat levels in an environment. They are widely used in weather monitoring, industrial systems, and smart homes.

**Examples:** LM35, DHT11

**Applications:**
- HVAC Systems
- Weather Stations
- Industrial Monitoring
  <img width="851" height="338" alt="image" src="https://github.com/user-attachments/assets/cac94e5f-3f77-400b-93c8-00f8b64258bc" />
                                                      Fig:DHT11

  ### 5.2 Humidity Sensors
Humidity sensors measure moisture content in the air. They are used in agriculture, weather forecasting, and environmental monitoring systems.

**Applications:**
- Smart Farming
- Greenhouses
- Weather Monitoring
  
  <img width="563" height="637" alt="image" src="https://github.com/user-attachments/assets/7c4fb50a-c963-4bb8-a5c6-51d7d12efdbd" />
  
  Fig:Humidity and Temperature sensor
  ### 5.3 Light Sensors
Light sensors detect the intensity of light in the surroundings. They are used in automatic street lights, smartphone brightness control, and energy-saving systems.

**Example:** LDR (Light Dependent Resistor)

<img width="433" height="341" alt="image" src="https://github.com/user-attachments/assets/5e0d9c15-fdba-4a02-b8c4-81b44a10ad01" />

Fig:LDR 


**Applications:**
- Automatic Lighting Systems
- Smartphone Brightness Control
- Energy Saving Systems

  ### 5.4 Motion Sensors
Motion sensors detect movement of objects or humans within a defined area. They are widely used in security systems and automatic doors.

**Example:** PIR Sensor

**Applications:**
- Smart Security Systems
- Motion Activated Lights
- Automatic Doors
- 
<img width="371" height="305" alt="image" src="https://github.com/user-attachments/assets/f24b824a-c192-44f6-8197-b671d3d2dfae" />

Fig:PIR motion sensor
### 5.5 Gas Sensors
Gas sensors detect harmful or specific gases in the environment. They play a major role in safety and industrial monitoring systems.

**Examples:** MQ-2, MQ-135

**Applications:**
- Air Quality Monitoring
- Gas Leakage Detection
- Industrial Safety Systems
  
  <img width="326" height="246" alt="image" src="https://github.com/user-attachments/assets/f8154e7e-9c14-4207-add9-18aa8fe04b07" />
  
Fig:MQ-2 gas sensor
### 5.6 Pressure Sensors
Pressure sensors measure force applied per unit area. They are used in industrial systems, automotive applications, and weather stations.

**Applications:**
- Tire Pressure Monitoring
- Weather Forecasting
- Industrial Automation
  
  <img width="445" height="303" alt="image" src="https://github.com/user-attachments/assets/3b537021-b3c1-4883-9e40-1770983feca4" />
  
Fig:Pressure Sensor


## 6. Working Principle of IoT Sensors
IoT sensors operate by detecting physical changes and converting them into electrical signals. These signals are processed by microcontrollers and transmitted to IoT platforms for monitoring and decision-making.


<img width="1035" height="677" alt="image" src="https://github.com/user-attachments/assets/9ec26c00-acaf-48fb-916d-7fbce6447597" />

Fig:IOT Architecture
## 7. Research Work: 10 IoT Projects

| # | Project Title | Brief Description | Reflection | Resource Link |
|---|---|---|---|---|
| 1 |Smart Energy & Power Monitoring|Use non-invasive current sensors (like the SCT013) to track your home's total power consumption. By tracking voltage, current, and power over time via a mobile interface, you can easily identify high-draw appliances.| A Smart Energy Meter with Home Automation system integrates real-time energy monitoring with automated control of household devices, enhancing energy efficiency and convenience. | [Smart Energy and power monintor](https://www.hackster.io/rajeshjiet/smart-energy-meter-with-home-automation-d7ea76) |
| 2 | Smart Home Automation with Voice Assistants | Uses a NodeMCU ESP8266 with relays to control home appliances, integrated with Google Assistant/Alexa via Sinric Pro, plus manual switches as a fallback. | Highlighted the importance of designing a fallback (manual switch) path for when the internet/cloud service is unavailable — a practical reliability lesson for our own attendance system's offline handling. | [Smart Home Automation with Voice Assistants](https://www.scribd.com/document/671447928/Home-automation-project) |
| 3 | Air and Noise Pollution Monitoring | Use MQ series gas sensors (for CO, CO₂, or dust) and a sound sensor to measure urban air and noise quality. Upload the environmental telemetry data to ThingSpeak or Firebase to create a city-wide pollution map |This IoT-based system uses a Raspberry Pi with MQ135, MQ7, and DHT11 sensors to monitor urban air, temperature, and humidity levels, utilizing MQTT for real-time data analysis| [IoT-Based Air_and_Noise_polution_monitoring](http://eprints.intimal.edu.my/1142/1/v1_2018_8.pdf) |
| 4 |  IoT based Weather Station | Combines a NodeMCU with a DHT11 sensor to monitor temperature and humidity, transmitting live data to the Blynk app. | A good example of a minimal, low-cost sensor node — useful as a template for our own idea of adding classroom environment monitoring alongside attendance in the future. | [Portable IoT Weather Station](https://www.researchgate.net/publication/399534225_METEORO_Low-Cost_IoT_Weather_Station) |
| 5 | Automatic Fire and Smoke Detection Alarm | Uses an Arduino with flame and MQ-2 gas/smoke sensors to detect a fire hazard and trigger a buzzer/LED alert. | Reinforced that safety-critical systems should react locally and instantly rather than depending on a network round-trip — an important design trade-off to keep in mind for any IoT deployment. | [Automatic Fire and Smoke Detection Alarm ](https://ijamtes.org/gallery/644.%20dec%20ijmte%20-%201414.pdf) |
| 6 | Touchless Smart Dustbin | An Arduino and ultrasonic sensor open a dustbin's lid automatically when a hand or object approaches, closing it after a short delay. | A simple but effective demonstration of proximity sensing driving a servo actuator — the exact sensor-to-actuator pipeline (input → decision → motion) that our attendance system uses conceptually (face detected → decision → log entry). | [Touchless Smart Dustbin](https://www.scribd.com/document/894958224/Smart-Dustbin-1) |
| 7 | Patient Health Monitoring System | Develop a wearable or bedside device to track vital signs like Heart Rate, SpO₂, or body temperature using sensors such as the MAX30100. The data can be sent to an IoT cloud, alerting doctors or family members if anomalies occur. | The device was synced with the app and the app was used by the medical professional in charge of the ward. Notifications are sent from the app when a critical value is recorded, and the healthcare professional will be alert.| [Patient_monitoring System ](https://www.hackster.io/projects-by-r/health-network-wearable-remote-patient-monitoring-system-24c5f6) |
| 8 | Smart Parking Management System | Install infrared or ultrasonic sensors at parking spots to detect if a space is occupied. Link this to a web or mobile application so users can check available parking spots in real time, reducing traffic congestion. | Showed a clean example of aggregating many simple binary sensor readings (occupied/empty) into a single useful dashboard view, similar to how individual attendance records will be aggregated into class-level reports. | [Smart Parking Management System](https://www.scribd.com/document/517502172/Smart-Parking) |
| 9 | Smart Waste Management | Equip trash bins with ultrasonic sensors to measure waste levels. When a bin reaches maximum capacity, it can trigger an alert or update a web dashboard to optimize collection routes, saving fuel and time. | Illustrated the "smart city" theme of using threshold-based alerts rather than continuous monitoring to reduce unnecessary notifications — a useful pattern for designing our own attendance/GPA alert thresholds. | [Smart Dustbin Fill-Level Indicator](https://www.scribd.com/document/970576922/TrashTracer-Smart-Dustbin-Fill-Level-Monitor) |
| 10 | Automated Plant Care System | Set up a closed-loop system for houseplants. It monitors soil moisture, automatically dispenses water, and uses a light-dependent resistor (LDR) to ensure the plant gets enough sunlight. |the plant will receive light at night and receive water automatically by using the light sensor with the m5stack light and the moisture sensor with servo motor which is connected to the water dispenser. It also inform the farmers if the plant temperature is above or below desired temperature to indicate whether the plant is suitable for growth and farmer no need to waste time and instead plant a new plant that is suitable at that temperature.|[Plant_care](https://www.hackster.io/group-4/automated-plant-caring-system-14e945#story)|

## 8. Importance of IoT Sensors
- Enable real-time monitoring of environments.
- Support automation in smart systems.
- Improve decision-making through data collection.
- Form the foundation of all IoT applications.

## 9. Applications of IoT Sensors

**Smart Homes**
- Smart Lighting
- Temperature Control
- Security Systems

**Healthcare**
- Patient Monitoring
- Wearable Devices



**Smart Agriculture**
- Soil Monitoring
- Weather Monitoring
- Automated Irrigation



**Industrial Automation**
- Predictive Maintenance
- Equipment Monitoring

**Smart Cities**
- Traffic Management
- Environmental Monitoring
- Smart Parking



## 9. Output
- Clear understanding of IoT sensor types.
- Knowledge of classification methods.
- Awareness of real-world applications.
- Ability to distinguish sensor functions.

## 10. Conclusion
In this lab, we studied different types of IoT sensors and their roles in real-world systems. Each sensor plays a critical role in collecting environmental data such as temperature, humidity, motion, light, gas levels, and pressure.

These sensors form the **backbone of IoT systems** by enabling real-time monitoring, automation, and intelligent decision-making in applications such as smart homes, healthcare, agriculture, and industrial systems.
