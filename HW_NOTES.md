# Hardware Notes — Nano 33 BLE Rev2 (3.3V)


## 1) ECHO level shifting (HC-SR04)
If HC-SR04 is powered at 5V, use a voltage divider on ECHO:


ECHO --- R1 (10kΩ) ---+--- Nano D10 (input)
|
R2 (4.7kΩ)
|
GND


This reduces ~5V pulses to ~3.2V safe for the Nano.
TRIG can be connected directly to Nano (3.3V output). If you power HC-SR04 at 3.3V, tests show it can work but may be less reliable.


## 2) Buzzer driver (active buzzer, 5V or >20mA)
If the buzzer needs 5V or draws more than the MCU pin can supply:


- Buzzer + -> 5V
- Buzzer - -> Collector of NPN transistor (e.g., 2N2222) or Drain of N-MOSFET
- Emitter/Source -> GND
- Arduino pin (D8) -> 1kΩ -> transistor base (or gate resistor for MOSFET)
- Add a common ground between Nano and buzzer supply.


If your buzzer is low-current and works at 3.3V, you can connect Buzzer + -> D8 and Buzzer - -> GND directly (check datasheet).


## 3) Power & Ground
- Always share a common GND between Nano, sensor and buzzer supply.
- If powering sensor or buzzer from USB, ensure total current draw is within the port limits (usually ~500mA for USB2.0). Use external supply if needed.
