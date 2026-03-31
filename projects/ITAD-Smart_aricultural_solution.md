# 🌿 LusherGreens — Smart Agriculture IoT Solution

> An IoT-based smart agriculture system for indoor farms and greenhouses, built using AWS cloud services and real-time environmental monitoring.

---

## 📌 Project Overview

**LusherGreens** addresses the inefficiencies of traditional indoor farming by deploying a network of IoT sensors that continuously monitor critical environmental variables. The system provides farmers with real-time alerts, historical trend analysis, and actionable insights — enabling precise control over growing conditions and improving both yield and operational efficiency.

---

## 🚜 Problem Statement

Traditional indoor farming relies on manual checks, which are:
- Time-consuming and prone to human error
- Unable to catch environmental changes in real time
- Inefficient in resource (water, energy, nutrients) usage

LusherGreens solves this with 24/7 automated monitoring, cloud-based processing, and instant farmer alerts.

---

## 🏗️ System Architecture

### AWS Architecture
The system uses the following AWS services in a pipeline:

```
IoT Sensors → (MQTT) → AWS IoT Core → AWS Lambda → Amazon DynamoDB
                                                  → Amazon SNS (Alerts)
                                                  → Amazon QuickSight (Dashboards)
```

### Data Flow
1. **Sensors** collect environmental data and transmit via secure MQTT
2. **AWS IoT Core** receives and routes incoming data
3. **AWS Lambda** processes data and triggers alerts when thresholds are crossed
4. **Amazon DynamoDB** stores all data for historical tracking
5. **Amazon SNS** sends notifications to farmers
6. **Amazon QuickSight** visualizes trends and plant health metrics

---

## 📡 Sensors & Monitored Variables

| Parameter | Purpose |
|---|---|
| Temperature | Ensure optimal thermal range for plant growth |
| Humidity | Monitor moisture in the air |
| Soil Moisture | Trigger irrigation when levels drop |
| Light Intensity | Regulate artificial lighting cycles |
| pH Level | Maintain ideal soil acidity |
| CO₂ Level | Track carbon dioxide for photosynthesis |
| Nutrient Level (N/P/K) | Ensure adequate plant nutrition |
| Water Level & Quality | Monitor irrigation supply |

---

## 📦 Sample Sensor Payload

```json
{
  "thingId": "lushergreens_gateway_001",
  "temperature": "24.90",
  "humidity": 78,
  "soilMoisture": 59,
  "lightIntensity": 4078,
  "pHLevel": "5.92",
  "CO2": 581,
  "nutrientLevel": 23,
  "site": "1",
  "room": "002"
}
```

---

## ✅ Key Features

- **Real-time monitoring** across 8 environmental parameters
- **Automated alerts** via Amazon SNS when thresholds are exceeded
- **Historical data storage** in DynamoDB for trend analysis
- **Visual dashboards** via Amazon QuickSight
- **Secure data transmission** using MQTT protocol
- **Scalable cloud architecture** on AWS

---

## 📈 Benefits

### Tangible
- Increased crop yields through optimised growing conditions
- Reduced operational costs via efficient resource usage
- Early detection of crop disease or pest infestation
- Consistent produce quality from controlled environments

### Intangible
- Reduced farmer stress with 24/7 automated oversight
- Deeper agronomic insights from historical data
- Encourages data-driven innovation in farming practices

---

## ⚠️ Limitations & Mitigations

| Limitation | Mitigation |
|---|---|
| Sensor drift over time in humid conditions | Scheduled calibrations + ML-based drift correction |
| Power outages in remote farm locations | Hybrid solar + battery backup power system |
| Unstable internet connectivity in rural areas | Edge computing for local real-time processing when offline |

---

## 🛠️ Tech Stack

- **Communication Protocol:** MQTT (secure, low-power)
- **Cloud Platform:** AWS (IoT Core, Lambda, DynamoDB, SNS, QuickSight)
- **Data Format:** JSON
- **Architecture Pattern:** Event-driven serverless

---

## 🎓 Academic Context

- **Institution:** Temasek Polytechnic, School of Informatics & IT
- **Module:** IOT Application Development (CMC2C16)
- **Programme:** Diploma in Applied Artificial Intelligence / Diploma in Information Technology
- **Academic Year:** AY2023/2024 October Semester

---

## 📚 References

- O. Friha et al., "Internet of Things for the Future of Smart Agriculture: A Comprehensive Survey of Emerging Technologies," *IEEE/CAA Journal of Automatica Sinica*, vol. 8, no. 4, pp. 718–752, April 2021. [doi:10.1109/JAS.2021.1003925](https://ieeexplore.ieee.org/document/9374808)
- [IoT in Agriculture & Vertical Farming — Onio](https://www.onio.com/article/agriculture-vertical-farming-iot.html)
- [IoT Smart Indoor Farming — Indium Software](https://www.indiumsoftware.com/blog/iot-smart-indoor-farming/)
- [Vertical Farms & IoT Technologies — Connector Supplier](https://connectorsupplier.com/vertical-farms-control-the-weather-with-iot-technologies/)