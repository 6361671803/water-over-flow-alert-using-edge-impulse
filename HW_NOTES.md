# Hardware Notes — Nano 33 BLE Rev2 (3.3V)

## 1) HC-SR04 & ECHO level-shift
If HC-SR04 is powered at 5V, use this voltage divider:

ECHO --- R1 (10kΩ) ---+--- Nano D10 (input)
                      |
                     R2 (4.7kΩ)
                      |
                     GND

This reduces ~5V to ~3.2V safe for Nano. TRIG can be driven directly by Nano at 3.3V.

## 2) Buzzer driver (active buzzer, 5V or >20mA)
If buzzer is 5V/high current:
- Buzzer + -> 5V
- Buzzer - -> Collector (NPN like 2N2222) or Drain (N-MOSFET)
- Emitter/Source -> GND
- Arduino pin (D8) -> 1kΩ -> Base/Gate
Share common ground between Nano and buzzer supply.

If buzzer works at 3.3V and low current, you may connect directly to D8 and GND (verify buzzer specs).

## 3) Power & ground
- Always tie grounds together (Nano, sensor, buzzer power source).
- If powering multiple devices, check USB/external supply current limits.
