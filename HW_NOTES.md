# Hardware Notes — Arduino UNO R3 (5V)

## HC-SR04 wiring (UNO)
- VCC -> 5V
- GND -> GND
- TRIG -> D9
- ECHO -> D10 (direct to UNO; UNO is 5V tolerant)

## Buzzer wiring
If buzzer is low current and 5V:
- D8 -> Buzzer +, Buzzer - -> GND

If buzzer draws significant current or needs switching:
- Use NPN transistor (2N2222) low-side switch:
  - Buzzer + -> 5V
  - Buzzer - -> Collector
  - Emitter -> GND
  - D8 -> 1kΩ -> Base

## Power & ground
- Common ground required between UNO and any external supply for buzzer.
- USB supply usually sufficient for UNO + HC-SR04 + small buzzer.

## Safety
- Verify buzzer current before connecting directly to a digital pin.


