# Day 14: Live Sensor + TinyML

This project reads light levels from an LDR sensor and uses an on-device TensorFlow Lite for Microcontrollers model to classify the environment as **Dark**, **Normal**, or **Bright**. The ESP32 displays the live reading and classification on an OLED.

## Components

- ESP32 DevKit board
- LDR light sensor (or photoresistor module)
- SSD1306 I2C OLED display

## Connections

### LDR module

- LDR VCC → ESP32 3V3
- LDR GND → ESP32 GND
- LDR AO → ESP32 GPIO 34

### OLED display

- OLED VCC → ESP32 3V3
- OLED GND → ESP32 GND
- OLED SDA → ESP32 GPIO 21
- OLED SCL → ESP32 GPIO 22

Check the pin labels in your Wokwi components and adjust the sketch if they differ.

## Wokwi Simulation

[Run the simulation](https://wokwi.com/projects/477652941860017153)

## How to use

1. Open the Wokwi simulation.
2. Start the simulation.
3. Adjust the LDR’s light level in Wokwi.
4. Watch the sensor reading and predicted class update on the OLED.

## How it works

The ESP32 reads the LDR’s analog output and prepares the reading as input for a TensorFlow Lite for Microcontrollers model. The model predicts one of three classes: **Dark**, **Normal**, or **Bright**. The OLED displays the reading and classification.

## Model

The model runs locally on the ESP32 using TensorFlow Lite for Microcontrollers. Include the converted model in the project (for example, as `model.h`) and make sure its input format and scaling match the values prepared by the sketch.

## Files

- `sketch.ino` — ESP32 sensor, inference, and OLED code
- `diagram.json` — Wokwi components and wiring
- `model.h` — model data included in the ESP32 sketch

## Note

The light-level thresholds or training labels depend on the dataset used to train the model. Calibrate the LDR and model for your setup for more reliable classifications.
