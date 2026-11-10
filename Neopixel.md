# Neopixel Board Documentation

## Purpose and Process

The purpose of this project is to learn how to surface mount solder smaller and larger components, as well as combining phyiscal components with arduino and a microcontroller, learning how to program in C++, and using the neopixel library. This board started as a basic PCB, without any components. The first three components soldered are the capacitors and resistor, all three at the same time using reflow soldering. The next two components, the SMS Neopixels, are soldered with reflow as well. The fiinal two components are the seven pin socket headers, which are soldered using a regular soldering iron and solder wire. After soldering, the code is written using multiple for() functions as loops, slowly fading in and fading out three different colors four times per one cycle in the main loop. After soldering and programming the EPS32C6, the ESP32C6 is plugged into the board and the project is complete.

## BOM

| Component | Specification | Quantity |
| :---: | :---: | :---: |
| SMS Neopixels | WS2812B | 2 |
| SMS Resistors | 330 Ω | 1 |
| SMS Capacitors | 0.1 µF | 2 |
| Socket Headers | 1x7 Pin | 2 |

## Process Images

| Flat Components Soldered | Socket Headers Soldered | Solder Joints (Backside) | All Components Soldered | Working Board |
| ---- | --- | --- | --- | --- |
| ![Flat Components Soldered](./Images/Screenshot%202026-11-09%20085402.png) | ![Headers Soldered](./Images/Screenshot%202026-11-09%20085407.png) | ![Solder Joints On Backside of Board](./Images/Screenshot%202026-11-09%20085413.png) | ![All Components Soldered](./Images/Screenshot%202026-11-09%20085425.png) | ![Working Board](./Images/Screenshot%202026-11-09%20085431.png) |

## Code

```C++

// Code written by Ethan Spiegler 2026
#include <Adafruit_NeoPixel.h>

#define LED_PIN      D3
#define LED_COUNT    2

Adafruit_NeoPixel strip(LED_COUNT, LED_PIN, NEO_GRB + NEO_KHZ800);

void setup() {
  strip.begin();
  strip.show();
  strip.setBrightness(75);
}

void loop() {
  //fade in
  for (int a=0; a < 256; a++) {
    for (int i = 0; i < LED_COUNT; i++) {
      strip.setPixelColor(i, strip.Color(a, a - a/2, a - a/3));
      strip.show();
      delay(5);
    }
  }
  //fade out
  for (int a=255; a > 0; a--) {
    for (int i = 0; i < LED_COUNT; i++) {
      strip.setPixelColor(i, strip.Color(a, a - a/2, a - a/3));
      strip.show();
      delay(5);
    }
  }
  //fade in
  for (int b=0; b < 256; b++) {
    for (int i = 0; i < LED_COUNT; i++) {
      strip.setPixelColor(i, strip.Color(b/3, b - b/2, b));
      strip.show();
      delay(5);   
    }
  }
  //fade out
  for (int b=255; b > 0; b--) {
    for (int i = 0; i < LED_COUNT; i++) {
      strip.setPixelColor(i, strip.Color(b/3, b - b/2, b));
      strip.show();
      delay(5);   
    }
  }
  //fade in
  for (int c=0; c < 256; c++) {
    for (int i = 0; i < LED_COUNT; i++) {
      strip.setPixelColor(i, strip.Color(c/3, c, c/2));
      strip.show();
      delay(5);
    }
  }
  // fade out
  for (int c=255; c > 0; c--) {
    for (int i = 0; i < LED_COUNT; i++) {
      strip.setPixelColor(i, strip.Color(c/3, c, c/2));
      strip.show();
      delay(5);
    }
  }
  delay(500);
  strip.clear();
  strip.show();
  delay(500);
  
  //multi fade

  for (int a=0; a < 256; a++) {
    strip.setPixelColor(0, strip.Color(a, a - a/2, a - a/3));
    strip.show();
    strip.setPixelColor(1, strip.Color(a/3, a, a/2));
    strip.show();
    delay(10);
  }
  for (int a=255; a > 0; a--) {
    strip.setPixelColor(0, strip.Color(a, a - a/2, a - a/3));
    strip.show();
    strip.setPixelColor(1, strip.Color(a/3, a, a/2));
    strip.show();
    delay(10);
  }
  delay(500);
  strip.clear();
  strip.show();
  delay(500);
}

```

## Video Embed
[Click here to view the video of the working board](https://github.com/Charlotte-Latin-School/Spiegse2-Electrical-Engineering/issues/1#issue-6287285255)

## Reflection

Several skills were reinforced with this project; a refresher on how to program in C++, more practice with surface mount soldering, and more practice with through hole soldeirng. I think soldering the Neopixels with reflow definitely helped me better understand how important it is to position the component as close to the perfect position as possible, as the pads for the Neopixels were not the largest and the Neopixels were a pretty large component. The programming aspect of this project was a really nice refresher, but it wasn't too challenging as I have worked with Neopixels in C++ a good amount in the past.
