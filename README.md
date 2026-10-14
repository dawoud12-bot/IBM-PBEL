# IoT-Based Weather Monitoring System

A learning project for monitoring temperature, relative humidity, and atmospheric pressure with a NodeMCU ESP8266 and a BME280 sensor. The sketch can publish readings to a ThingSpeak channel over Wi-Fi.

> **Project status:** Simulation / development stage. This repository contains starter code and wiring notes; it has not been verified on physical hardware. Do not describe it as a tested hardware prototype until you have tested it.

## Features planned

- Read temperature (°C), relative humidity (%) and pressure (hPa) from a BME280.
- Connect to Wi-Fi using credentials configured locally in the sketch.
- Send readings to ThingSpeak fields 1–3.
- Print sensor readings and upload status to the Serial Monitor.

## Components

- NodeMCU ESP8266 development board
- BME280 sensor module with I²C interface
- Jumper wires and breadboard (for a future hardware build)
- Wi-Fi connection and ThingSpeak account (for cloud upload)

The BME280 measures temperature, humidity and pressure. It does **not** measure air quality/AQI. Add a suitable air-quality sensor and implement its reading/calibration separately if you want that feature.

## Wiring (I²C)

| BME280 pin | NodeMCU ESP8266 |
|---|---|
| VIN / VCC | 3V3 (check your breakout board's requirements) |
| GND | GND |
| SDA | D2 (GPIO4) |
| SCL | D1 (GPIO5) |

Use a 3.3 V-compatible I²C connection. Sensor breakout boards differ, so check the labels and specifications of your exact module before wiring.

## Arduino IDE setup

1. Install the ESP8266 board package and select **NodeMCU 1.0 (ESP-12E Module)**.
2. In Library Manager, install:
   - **ThingSpeak** by MathWorks
   - **Adafruit BME280 Library**
   - **Adafruit Unified Sensor**
   - **Adafruit BusIO** (if requested as a dependency)
3. Open `src/WeatherMonitoring.ino`.
4. Replace the placeholder Wi-Fi name/password, ThingSpeak channel number, and Write API Key in the sketch. Never commit real passwords or API keys to a public repository.
5. In ThingSpeak, create a channel with:
   - Field 1: Temperature (°C)
   - Field 2: Humidity (%)
   - Field 3: Pressure (hPa)
6. Upload to the board and open Serial Monitor at 115200 baud.

## ThingSpeak notes

The sketch sends one update every 20 seconds. Check the current limits and requirements for your ThingSpeak account before changing the interval. A successful HTTP status from the library indicates that the update was accepted; it does not validate sensor accuracy.

## Simulation and testing

This repository is starter material, not proof of a completed simulation or working device. If your simulator does not support the BME280 or external network access, you may need to test the sensor and ThingSpeak parts separately or use a compatible simulator.

## Repository structure

```text
IoT-Based-Weather-Monitoring-System/
├── README.md
├── .gitignore
├── src/
│   └── WeatherMonitoring.ino
└── docs/
    └── WIRING.md
```

## Future improvements

- Add an air-quality sensor with safe voltage interfacing and calibration.
- Add a dashboard screenshot and a circuit diagram after testing.
- Add sensor fault handling and reconnect logic.
- Record real test results and limitations.

## Author

Mohammad Dawoud Eqbal  
B.Tech — Internet of Things, GNIOT
