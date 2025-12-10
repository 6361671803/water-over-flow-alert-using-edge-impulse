
# 🧠 Edge Impulse — Build & Deploy (Arduino UNO / AVR)

1. Open your Edge Impulse project and make sure the impulse uses the same sampling interval and frame length you collected.  
2. Go to **Deployment → Arduino Library**.  
3. Under Target, choose **Arduino (AVR)** or **Arduino UNO** (if shown).  
4. Choose **Quantized (int8)** (recommended) and click **Build**.  
5. Download the generated ZIP and save it as:  
   `/model/edge_impulse_uno_library.zip` (do **not** unzip in the repo).  
6. In Arduino IDE: `Sketch → Include Library → Add .ZIP Library` → choose the downloaded ZIP.  
7. Open the ZIP locally and note the `.h` header filename (e.g. `water_overflow_alert_inferencing.h`). **Replace** the placeholder include line in your sketch with that exact filename.

---

# ▶ How to compile & upload

1. Install Arduino IDE and select **Arduino/Genuino Uno** under Tools → Board.  
2. `Sketch → Include Library → Add .ZIP Library` → select `/model/edge_impulse_uno_library.zip`.  
3. Open `code/water_overflow_alert_uno.ino` and replace the `#include <your_project_inferencing.h>` line with the header from the ZIP.  
4. Connect UNO via USB, select correct COM port.  
5. Click Upload.  
6. Open Serial Monitor at **115200** to observe samples and inference output.

---

# ✅ Default thresholds & behavior
- **FULL_THRESHOLD** = 0.80 (80% confidence) — you can tune this in the sketch.  
- Buzzer ON when `glass_full` > threshold.  
- Buzzer OFF otherwise.

---

# 📷 Images to include in repo
Place these files in `/images/`:
- `wiring_uno.png` — wiring diagram (D9 TRIG, D10 ECHO, D8 buzzer/transistor)  
- `hardware_setup.png` — photo of your breadboard + UNO + HC-SR04 + buzzer  
- `sensor_placement.png` — diagram showing sensor above glass and the distance markers (3–6 cm = full; 8–12 cm = not full)  
- `system_block_diagram.png` — logical flow (Sensor → MCU → ML → Buzzer)

---

# ⚠️ Limitations

- **Surface reflections & ripples:** foam, waves or tilt changes reading accuracy.  
- **Sensor mounting:** model assumes the sensor is placed at the same height and orientation used during training. If you move the sensor or change container geometry, retrain.  
- **Dirty/foamy liquids:** ultrasonic returns may be unreliable.  
- **Small dataset:** model robustness improves with more varied samples (different glasses, water temperatures, noises).  
- **Buzzer only:** no mobile/IoT notifications are included by default.

---

# 🌍 Real-World Applications

- Household overhead tank overflow detection — stop pumps and alert.  
- Beverage/production filling line overflow prevention.  
- Smart kitchen alerts (prevent boiling over).  
- Educational TinyML demo for embedded classification.  
- Small-scale industrial container level alerts (non-contact).

---

# 🧪 Testing & Verification Checklist

Before running:

- [ ] `/model/edge_impulse_uno_library.zip` is present in `/model/`.  
- [ ] `code/water_overflow_alert_uno.ino` `#include` matches `.h` inside ZIP.  
- [ ] UNO board selected in Arduino IDE and sketch compiles.  
- [ ] Wiring matches `images/wiring_uno.png`.  
- [ ] Serial Monitor open @ 115200 shows sample frames and classifier scores.  
- [ ] Buzzer toggles ON when water reaches ~3–6 cm.

---

# 🔁 GitHub upload order & recommended commit messages

1. Add `README.md` → `docs: add README for Arduino UNO R3`  
2. Add `.gitignore` → `chore: add .gitignore`  
3. Add `HW_NOTES.md` → `docs: add HW_NOTES`  
4. Add `code/water_overflow_alert_uno.ino` → `feat(code): add UNO sketch`  
5. Add `model/edge_impulse_uno_library.zip` → `chore(model): add EI library (UNO)`  
6. Add dataset files → `data: add dataset`  
7. Add images → `docs: add wiring + images`  
8. (Optional) Add LICENSE → `chore: add license`

---

# 🛠 Troubleshooting tips

- `run_classifier` fails: ensure EI library ZIP is imported in Arduino IDE and the header include matches exactly.  
- `pulseIn` returns 0: check TRIG/ECHO wiring and that sensor has line-of-sight to water.  
- Buzzer not responding: test buzzer with a small toggle sketch or verify transistor wiring if used.  
- Model performs poorly: collect more samples covering slight tilt, different glasses, and save separate test files.

---

# 📦 Want me to generate files?
If you want, I can now generate for you immediately:

- `wiring_uno.png` (clean labeled wiring diagram PNG)  
- `sensor_placement.png` (visual showing 3–6 cm vs 8–12 cm)  
- `system_block_diagram.png`  
- A ZIP of the text files for direct upload

Reply with any of: **“Make wiring_uno.png”**, **“Make all images”**, or **“Make repo ZIP”** and I’ll produce them now.

