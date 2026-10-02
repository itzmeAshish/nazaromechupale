# Nazarome Chupale OLED Animation — Arduino SSD1306

![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D?logo=arduino&logoColor=white)
![OLED](https://img.shields.io/badge/Display-SSD1306%20128x64-111827)
![Library](https://img.shields.io/badge/Library-Adafruit%20SSD1306-orange)
![License](https://img.shields.io/badge/code-free%20to%20use-brightgreen)

Play **Nazarome Chupale** as a looping animation on a **0.96" SSD1306 OLED** (128×64).  
This repo contains a ready-to-upload Arduino sketch with **150 PROGMEM bitmap frames**.

**Repo:** [https://github.com/itzmeAshish/nazaromechupale](https://github.com/itzmeAshish/nazaromechupale)  
**Full tutorial:** [Nazarome Chupale OLED Animation Guide](https://www.oledanimationmaker.com/blog/nazarome-chupale-oled-animation-arduino-ssd1306.html)  
**Made with:** [OLED Animation Maker](https://www.oledanimationmaker.com/)

---

## Keywords

`nazarome chupale oled` · `nazaron mein chhupale oled` · `arduino oled animation` · `ssd1306 frame animation` · `progmem bitmap` · `gif to oled` · `0.96 oled arduino` · `esp8266 oled song` · `adafruit ssd1306 animation`

---

## Features

- 150 frames × 128×64 mono bitmaps in `PROGMEM` (`frame0` … `frame149`)
- Frame delay **147 ms** (~6.8 fps) — easy to change
- Adafruit SSD1306 + Adafruit GFX
- I2C address **0x3C**
- Auto-loop in `loop()`
- Sketch file: `main.ino`

---

## Requirements

| Item | Notes |
|------|--------|
| Board | **ESP8266 / ESP32 recommended** (Mega may fit; classic Uno will not) |
| OLED | 0.96" SSD1306 I2C 128×64 |
| IDE | Arduino IDE 1.8+ or 2.x |
| Libraries | Adafruit SSD1306, Adafruit GFX |

> **Flash size:** 150 frames × 1024 bytes ≈ **150 KB** of bitmap data. Classic **Arduino Uno (32 KB)** cannot fit this sketch. Use ESP8266 or ESP32, or export fewer frames from [OLED Animation Maker](https://www.oledanimationmaker.com/).

---

## Connection / Wiring

The sketch header is written for Arduino Uno pins. For this frame count, wire an ESP8266 or ESP32 instead.

### ESP8266 NodeMCU / Wemos D1 Mini (recommended)

| OLED | Board | GPIO |
|------|--------|------|
| VCC | **3.3V** | — |
| GND | GND | — |
| SDA | **D2** | GPIO4 |
| SCL | **D1** | GPIO5 |

If the screen stays blank, add this before `display.begin()`:

```cpp
Wire.begin(4, 5);  // SDA, SCL on ESP8266
```

### ESP32

| OLED | Board |
|------|--------|
| VCC | 3.3V |
| GND | GND |
| SDA | GPIO21 |
| SCL | GPIO22 |

```cpp
Wire.begin(21, 22);
```

### Arduino Uno / Nano (smaller animations only)

| OLED | Board |
|------|--------|
| VCC | 5V (or 3.3V if the module requires it) |
| GND | GND |
| SDA | **A4** |
| SCL | **A5** |

---

## Install & upload

1. **Download** this repo  
   - ZIP: GitHub → **Code → Download ZIP**  
   - or `git clone https://github.com/itzmeAshish/nazaromechupale.git`
2. Arduino IDE needs the folder name to match the sketch. After unzipping, either:
   - rename the folder to `main`, then open `main/main.ino`, or
   - rename `main.ino` to `nazaromechupale.ino` and put it in a folder named `nazaromechupale`
3. Install libraries: **Adafruit SSD1306** + **Adafruit GFX Library**
4. Select board + COM port  
   - Example: *NodeMCU 1.0 (ESP-12E Module)* or *ESP32 Dev Module*
5. On ESP8266, set **Tools → Flash Size** to at least **1MB** (4MB is typical on NodeMCU)
6. Click **Upload**
7. The Nazarome Chupale animation loops on the OLED

Serial baud: **115200**. If you see `SSD1306 allocation failed`, check power, wiring, and try address `0x3D`.

---

## Speed control

In `loop()`, change the delay:

```cpp
if (millis() - lastMs >= 147) {  // lower = faster
```

| Value | Approx FPS |
|------:|-----------:|
| 147 | ~6.8 |
| 100 | ~10 |
| 66 | ~15 |

`numFrames` is **150**. Frames are `frame0` through `frame149`.

---

## How this was made

1. Open [oledanimationmaker.com](https://www.oledanimationmaker.com/)
2. **Import** a short clip of the Nazarome Chupale visual
3. Keep the export at or under **200 frames** so it fits ESP flash and the site database
4. **Get the Code** → Adafruit SSD1306 Arduino
5. Save as `main.ino` and push to this repo

Tutorial:  
https://www.oledanimationmaker.com/blog/nazarome-chupale-oled-animation-arduino-ssd1306.html

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Blank screen | 3.3V on ESP, check SDA/SCL, try `0x3D` |
| Sketch too big | Use ESP8266/ESP32 and a larger flash size; cut frames |
| “Sketch folder must match” | Folder name must be `main` if the file is `main.ino` |
| Laggy playback | Raise the frame delay; use a solid USB cable |
| Compile errors | Install both Adafruit libraries |

More help: [OLED blank screen guide](https://www.oledanimationmaker.com/blog/arduino-oled-blank-screen-fix-ssd1306.html)

---

## Links

- **Code:** https://github.com/itzmeAshish/nazaromechupale
- **Blog:** https://www.oledanimationmaker.com/blog/nazarome-chupale-oled-animation-arduino-ssd1306.html
- **Tool:** https://www.oledanimationmaker.com/
- **Author:** [Ashish (itzmeAshish)](https://github.com/itzmeAshish)
- **Instagram:** https://www.instagram.com/oled_animator
- **YouTube:** https://www.youtube.com/@oled_animator

---

## License

Free to use for learning, demos, and personal projects.  
Credit appreciated: link back to this repo and [oledanimationmaker.com](https://www.oledanimationmaker.com/).
