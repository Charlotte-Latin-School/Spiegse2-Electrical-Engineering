# Neopixel Board Documentation
The purpose of this project is to learn how to surface mount solder smaller and larger components, as well as combining phyiscal components with arduino and a microcontroller, learning how to program in C++, and using the neopixel library.

| Flat Components Soldered | Headers Soldered | Solder Joints (Backside) | All Components Soldered | Working Board |
| ---- | --- | --- | --- | --- |
| ![Flat Components Soldered](./Images/Screenshot%202026-11-09%20085402.png) | ![Headers Soldered](./Images/Screenshot%202026-11-09%20085407.png) | ![Solder Joints On Backside of Board](./Images/Screenshot%202026-11-09%20085413.png) | ![All Components Soldered](./Images/Screenshot%202026-11-09%20085425.png) | ![Working Board](./Images/Screenshot%202026-11-09%20085431.png) |

Code Embed: '// Code written by Ethan Spiegler 2026
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
}'


Video Embed:
[Click here to view the video of the working board](https://github.com/Charlotte-Latin-School/Spiegse2-Electrical-Engineering/issues/1#issue-6287285255)
