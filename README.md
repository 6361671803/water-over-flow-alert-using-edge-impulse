

# 🚨 Water Overflow Alert System using Arduino & Edge Impulse (AI-Based)

This project prevents **water overflow** by detecting whether a **glass / cup / syntax tank is full or not**.
Instead of using a basic level sensor, this project uses **AI (TinyML) and ultrasonic distance measurement** to classify water level in real time and activate a buzzer when the level reaches FULL.

---

## 🧠 Project Concept

The **ultrasonic sensor HC-SR04** is placed **above the water cup facing downward**.
As the water rises, the distance between the **sensor and water surface decreases**.

This pattern is sent to a **machine learning model trained on Edge Impulse**.

| Water Level         | Distance       | ML Prediction | Buzzer |
| ------------------- | -------------- | ------------- | ------ |
| 3–6 cm from sensor  | glass_full     | 🔔 ON         |        |
| 8–12 cm from sensor | glass_not_full | ❌ OFF         |        |

The system runs **offline** on Arduino (no internet required).

---

## 🎯 Goals of the Project

✔ Detect full vs not-full automatically
✔ Trigger buzzer to prevent overflow
✔ Run AI model on microcontroller locally
✔ Apply TinyML in a real-world problem

---

## 🔌 Hardware Components

| Component                 | Purpose                 |
| ------------------------- | ----------------------- |
| Arduino UNO R3            | Runs the ML model       |
| Ultrasonic Sensor HC-SR04 | Captures water distance |
| Active Buzzer             | Alerts when full        |
| Jumper Wires              | Circuit connection      |
| Breadboard (optional)     | For wiring arrangement  |

---

## 🔧 Wiring Connections

| HC-SR04 Pin | Arduino Pin |
| ----------- | ----------- |
| VCC         | 5V          |
| GND         | GND         |
| TRIG        | D9          |
| ECHO        | D10         |

| Buzzer Pin   | Arduino Pin |
| ------------ | ----------- |
| + (Positive) | D8          |
| – (Negative) | GND         |

---

## 💡 ML Model Summary

| Parameter      | Value                          |
| -------------- | ------------------------------ |
| Platform       | Edge Impulse                   |
| Sensor type    | Ultrasonic distance            |
| Classes        | `glass_full`, `glass_not_full` |
| Training input | Distance values (cm)           |
| DSP block      | Raw data                       |
| Learning block | Neural Network                 |
| Deployment     | Arduino C++ library            |

**Dataset collection conditions:**

* FULL samples → 3–6 cm distance
* NOT FULL samples → 8–12 cm distance

---

## 🔁 Workflow of the System

1. Sensor repeatedly measures distance
2. Distance is fed into the TinyML model
3. Model predicts:

   * `glass_full`
   * `glass_not_full`
4. Action is taken:

   * FULL → buzzer alerts
   * NOT FULL → buzzer stays silent

---

## 🧪 Training & Testing Results

* Clear separation between FULL and NOT FULL datasets
* High accuracy achieved after retraining
* Real-time prediction works reliably in deployment

---

## 📦 Repository Contents (Recommended)

```
/code                  → Arduino program (without model)
/model                 → Edge Impulse library files
/dataset               → CSV training + testing samples
/images                → Wiring + circuit diagrams + setup photos
/video                 → Demonstration video (optional)
/README.md             → Project description
```

---

## 🧾 Applications

* Household water tank alert
* Smart kitchen water filling
* Industrial liquid level detection
* Overflow prevention systems

---

## 📌 Conclusion

This project demonstrates how **TinyML + Arduino** can be used to solve real-life problems efficiently without internet or cloud.
By analyzing water level patterns using **machine learning**, the system becomes **more adaptable, smarter, and reliable** than traditional sensors.

---



