# Wiring Notes

**Target board:** NodeMCU ESP8266  
**Sensor:** BME280 I²C breakout  
**Status:** Proposed wiring; not physically tested as part of this repository.

| BME280 | NodeMCU |
|---|---|
| VIN / VCC | 3V3, if supported by your breakout |
| GND | GND |
| SDA | D2 / GPIO4 |
| SCL | D1 / GPIO5 |

## Important

- Check your specific BME280 breakout's voltage requirements before connecting power.
- Use 3.3 V logic with the ESP8266.
- BME280 modules commonly use I²C address `0x76` or `0x77`; the sketch checks both.
- This wiring measures temperature, humidity, and atmospheric pressure. It does not measure AQI.
