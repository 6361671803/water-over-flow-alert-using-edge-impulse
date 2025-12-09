# Water Overflow Alert using Arduino + Edge Impulse (TinyML)

This project detects whether a water glass is **full** or **not full** using:
- Arduino Uno R3
- Ultrasonic sensor (HC-SR04)
- Buzzer
- TinyML model trained in Edge Impulse

## How it works

- The ultrasonic sensor is placed above the water glass, pointing down.
- When the glass is **full**, the distance from sensor to water surface is about **3–6 cm**.
- When the glass is **not full**, the distance is about **8–12 cm**.
- This distance data is sent to a TinyML model (Edge Impulse).
- The model predicts:
  - `glass_full`  → buzzer ON
  - `glass_not_full` → buzzer OFF

## Hardware connections

| Sensor / Part | Arduino Pin |
| ------------- | ----------- |
| HC-SR04 VCC   | 5V          |
| HC-SR04 GND   | GND         |
| HC-SR04 TRIG  | D9          |
| HC-SR04 ECHO  | D10         |
| Buzzer +      | D8          |
| Buzzer –      | GND         |

## Files in this repo

- `code/water_overflow_alert.ino` – main Arduino code
- `dataset/` – CSV files used to train the model
- `.gitignore` – tells Git which files to ignore
- `README.md` – this document
