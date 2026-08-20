# Arduino LCD Animation

> Typing animation, marquee scroll, and contrast pulse on a 16x2 LCD using **Arduino + LiquidCrystal**

![Arduino](https://img.shields.io/badge/Arduino-Uno-00979D?style=flat&logo=arduino&logoColor=white)
![C++](https://img.shields.io/badge/Language-C%2B%2B-00599C?style=flat&logo=cplusplus&logoColor=white)
![LCD](https://img.shields.io/badge/Display-16x2%20LCD-blue?style=flat)



ty

---

## What It Does

This sketch drives a 16x2 character LCD through three chained animations:

1. **Typing effect** — text appears character by character on the first row
2. **Marquee scroll** — both lines scroll across the display from right to left
3. **Contrast pulse** — the LCD contrast fades in and out using PWM on pin 6

Custom characters (a heart ♥ and a smiley ☺) are defined using 5x8 bitmaps and rendered at the end of each line during the animation.

---

## Hardware

| Component | Details |
|---|---|
| Microcontroller | Arduino Uno |
| Display | 16x2 Character LCD (HD44780 compatible) |
| Contrast control | PWM via pin 6 (potentiometer or direct PWM) |

---

## Wiring

```
LCD Pin   →  Arduino Pin
--------------------------
RS        →  12
Enable    →  11
D4        →  5
D5        →  4
D6        →  3
D7        →  2
V0 (contrast) → Pin 6 (PWM)
VSS       →  GND
VDD       →  5V
A (backlight+) → 5V
K (backlight-) → GND
```

---

## Custom Characters

Two 5x8 bitmap characters are defined in the sketch:

```cpp
// Heart ♥
byte heart[8] = {
  0b00000,
  0b01010,
  0b11111,
  0b11111,
  0b11111,
  0b01110,
  0b00100,
  0b00000
};

// Smiley ☺
byte smiley[8] = {
  0b00000,
  0b00000,
  0b01010,
  0b00000,
  0b00000,
  0b10001,
  0b01110,
  0b00000
};
```

---

## Animation Flow

```
1. Typing effect
   └─ Characters appear one by one on row 1
   └─ Row 2 shows static text with smiley at end

2. Marquee scroll
   └─ Both rows scroll right to left across the display
   └─ Heart character appended at end of row 2

3. Contrast pulse
   └─ PWM value sweeps 50 → 200 → 50 on pin 6
   └─ Creates a breathing/fade effect on the display

4. Loop repeats
```

---

## Setup

1. Wire the LCD according to the table above
2. Open `LCD_Animation.ino.ino` in Arduino IDE
3. Select **Board: Arduino Uno** and the correct COM port
4. Upload and watch the animation run

> No external libraries needed beyond the built-in `LiquidCrystal.h`

---

## Demo

![Hardware Demo](1000010748%20(1).jpg)

---

*A small but satisfying hardware project — exploring custom LCD characters, animation timing, and PWM contrast control on Arduino.*
