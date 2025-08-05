# Lab-Data-Monitoring-Station
A fully-featured, battery-powered data monitoring system capable of sensing key air quality parameters and environmental conditions. Envisioned to be used broadly in a chemical lab scenario to provide safety reading.Designed for portability and long-term data logging with a user-friendly display and alert system.

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Hardware Components](#hardware-components)
- [Sensor Coverage](#sensor-coverage)
- [Display & Interface](#display--interface)
- [Power System](#power-system)
- [Data Logging](#data-logging)
- [Communication](#communication)
- [Wiring Diagram](#wiring-diagram)
- [How to Use](#how-to-use)
- [CSV Format](#csv-format)
- [Future Enhancements](#future-enhancements)
- [License](#license)

---

## Overview

This project is a **Portable Environmental Monitoring Station** that measures a wide array of environmental parameters including CO₂, CO, NO₂, NH₃, alcohol vapors, ambient and focal temperatures, humidity, and pressure. The system displays real-time data on a 20x4 LCD screen, logs values to a microSD card in CSV format, alerts users via buzzer when thresholds are exceeded, and supports wireless communication through Bluetooth or Wi-Fi.

---

## Features

- **Battery-powered**: Runs on a rechargeable Li-ion battery
- **20x4 LCD**: Displays live sensor readings in real-time
- **Buzzer alerts**: Notifies user when toxic levels are detected
- **Data Logging**: CSV logs to SD card for long-term monitoring
- **Wireless Communication**: Bluetooth and optional Wi-Fi server (ESP32)
- **Wall-mounted charging dock**: Recharge when not in use
- **Expandable firmware**: Easily extend UI, thresholds, and logging

---

## Hardware Components

| Component               | Description                                       |
|------------------------|---------------------------------------------------|
| ESP32                  | Main MCU with Wi-Fi & Bluetooth                   |
| 20x4 I²C LCD           | Live display for sensor values                    |
| MH-Z19B                | CO₂ sensor (NDIR, UART)                          |
| MiCS-6814              | CO, NO₂, NH₃ sensor (3-channel)                   |
| MQ-3                   | Alcohol vapor sensor (analog)                     |
| BME280                 | Temperature, humidity, and pressure sensor        |
| MLX90614               | Focal IR temperature sensor (I²C)                 |
| SD Card Module         | Stores logs in CSV format                         |
| DS3231 (optional)      | RTC for timestamping CSV logs                     |
| Buzzer                 | Audio alert for high gas levels                   |
| TP4056 Module          | Battery charging (Li-ion)                         |
| MT3608 Boost Converter | Boosts battery to 5V                              |
| 18650 Battery          | Rechargeable power source                         |
| Enclosure / Dock       | Optional housing + wall charging dock             |

---

## Sensor Coverage

| Parameter               | Sensor      | Method        |
|------------------------|-------------|---------------|
| CO₂ (ppm)              | MH-Z19B     | NDIR, UART    |
| CO (trend %)           | MiCS-6814   | RED Channel   |
| NO₂ (trend %)          | MiCS-6814   | OX Channel    |
| NH₃ (trend %)          | MiCS-6814   | NH₃ Channel   |
| Alcohol Vapors (%)     | MQ-3        | Analog        |
| Ambient Temp (°C)      | BME280      | I²C           |
| Humidity (%)           | BME280      | I²C           |
| Pressure (hPa)         | BME280      | I²C           |
| Focal Temp (°C)        | MLX90614    | IR, I²C       |

---

## Display & Interface

- **Rotating or button-based UI**: View sensor data by group
- **Auto-refresh**: Values update every 2 seconds
- **Alert system**: When thresholds are exceeded, the buzzer sounds and affected values blink

---

## Power System

- Powered by **18650 3.7V Li-ion battery**
- Charged via **TP4056 module**
- Boosted to 5V using **MT3608**
- Safe and rechargeable; supports **wall-mounted dock charging**

---

## Data Logging

- Sensor data logged to **microSD** in CSV format
- Timestamped using `millis()` or optional **DS3231 RTC**
- Log file rollover based on time or file size

---

## Communication

- **Bluetooth Low Energy (BLE)**:
  - Supports connection via apps like **nRF Connect**
  - Sends grouped sensor data every few seconds
- **Wi-Fi Server (optional)**:
  - ESP32 serves a local webpage with live sensor data
  - Auto-refresh every few seconds

---

## Wiring Diagram

*Coming soon as Fritzing or schematic file.*

**Bus Assignments:**
- **I²C (SDA/SCL)**: BME280, MLX90614, MiCS-6814
- **UART**: MH-Z19B
- **SPI**: SD Card Module
- **Analog Pins**: MQ-3
- **Digital I/O**: Buzzer, LCD, Button

---

## How to Use

1. Power the system using a charged Li-ion battery or USB.
2. On boot, the LCD will show a welcome screen, then cycle through sensor readings.
3. Insert a microSD card to begin logging.
4. Optional:
   - Connect via BLE using **nRF Connect**
   - Access web dashboard (if Wi-Fi server is enabled)

---

## CSV Format

Each log entry contains a timestamp and all sensor readings:



---

## Future Enhancements

- OTA firmware updates
- Cloud logging (e.g., ThingSpeak, Google Sheets)
- Android/iOS app for real-time BLE view
- WebSocket-based live dashboard
- AI model for air quality classification

---

## License

MIT License. See `LICENSE` file for more details.

---

## Contributing

Pull requests welcome. For major changes, please open an issue first to discuss what you’d like to change or improve.

---

## Author

**Victor Granado**  
Computer Engineering Student  
[GitHub Profile](https://github.com/yourusername)

---
