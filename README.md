# 🤖 IoT-Based Autonomous Fire Suppression Robot

**Smart Sensors & Actuators — IoT Seminar Paper**  
Frankfurt University of Applied Sciences (Fra-UAS)  
Department of Computer Science and Engineering  
Summer Semester 2026

---

## 📄 Overview

This repository contains the IEEE-format seminar paper submitted for the **HIS - Internet of Things (IoT)** course. The paper presents a fully autonomous fire suppression robot that integrates smart sensors and actuators with **Microsoft Azure IoT Hub** for real-time fire detection, suppression, and remote monitoring.

**Key result:** Response time reduced from 400–800 ms (traditional local-server systems) down to **~100 ms**, with **99.9% uptime** using Azure cloud infrastructure.

---

## 🧰 Tech Stack

| Layer | Technology |
|-------|-----------|
| Microcontroller | ESP32 (240 MHz, no OS — real-time sensor reading) |
| Edge Computing | Raspberry Pi 4 + Azure IoT Edge |
| Cloud Platform | Microsoft Azure IoT Hub |
| Messaging Protocol | MQTT over 5 GHz Wi-Fi |
| Real-time Updates | Azure SignalR Service (WebSocket, <50 ms latency) |
| Data Storage | Azure Blob Storage |
| Stream Processing | Azure Stream Analytics |
| Communication (ESP32 ↔ RPi) | Serial UART (TX, RX, GND) |

---

## 🔬 Sensors Used

| Sensor | Model | Role |
|--------|-------|------|
| Flame Sensor | YG1006 | Primary fire detection (0–100 cm) |
| Gas Sensor | MQ-2 | Early smoke/gas warning (300–10,000 ppm) |
| Temperature | MLX90614 | Heat localization (−70°C to +380°C) |
| Ultrasonic | HC-SR04 | Obstacle avoidance navigation |
| Camera | Pi Cam v2 | Live 1080p monitoring |

**Fire confirmation logic:** All three must trigger simultaneously — flame detected + temperature > 60°C + gas > 300 ppm. This eliminates false alarms.

---

## ⚙️ Actuators Used

| Actuator | Model | Role |
|----------|-------|------|
| DC Motors | 4× 12V | Robot movement |
| Motor Driver | L298N × 2 | PWM-based direction and speed control |
| Water Pump | 12V | Fire suppression |
| Relay Module | 5V | Safe high-current pump switching |

---

## 🏗️ System Architecture (5 Layers)

```
Layer 1 — Sensors (YG1006, MQ-2, MLX90614, HC-SR04, Pi Cam v2)
    ↓
Layer 2 — ESP32 Microcontroller (real-time, no OS, immediate local action)
    ↓ Serial UART
Layer 3 — Raspberry Pi 4 + Azure IoT Edge (local decision + cloud relay)
    ↓ MQTT over Wi-Fi
Layer 4 — Azure Cloud (IoT Hub → Stream Analytics + Blob Storage + SignalR)
    ↓ WebSocket <50ms
Layer 5 — Mobile Application (live monitoring + manual/autonomous control)
```

---

## 🚀 Key Results

- **Response time:** ~100 ms (vs. 400–800 ms in local-server approaches)
- **Uptime:** 99.9% (Azure IoT Hub SLA)
- **Multi-robot coordination:** Supported via cloud (impossible in older local systems)
- **False alarm prevention:** 3-sensor simultaneous confirmation required

---

## 📁 Repository Contents

```
├── README.md                              # This file
├── Smart_Sensors_Actuators_Fire_Robot.pdf # Final IEEE-format paper (4 pages)
└── main.tex                               # LaTeX source code
```

---

## 📚 Paper Abstract

Smart sensors and actuators are becoming critical in modern industrial IoT systems. This paper presents an IoT-based fire extinguisher robot using Microsoft Azure IoT Hub. The robot uses an ESP32 microcontroller for sensor reading and motor control, while a Raspberry Pi 4 runs Azure IoT Edge for local decision-making and cloud communication. The design addresses two core problems in existing fire-fighting robots: slow response time and poor network reliability due to local-server dependency.

---

## 👨‍💻 Author

**Mobeen Anwar**  
M.Sc. High Integrity Systems — Frankfurt University of Applied Sciences  
📧 mobeen.anwar@stud.fra-uas.de

---

## 📜 License

This work is submitted as a university seminar paper. All rights reserved by the author.
