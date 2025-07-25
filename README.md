# multicolor-line-follower
A color-based autonomous line follower robot using Arduino and GY-13 TCS3200 color sensor for intelligent path navigation in multi-color tracks.

An intelligent line-following robot designed to detect and follow colored paths using the TCS3200 color sensor and Arduino Uno. The bot can differentiate between multiple colors (e.g., red, green, blue, black) and follow them accordingly — suitable for educational automation tasks and smart navigation systems.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Objectives](#objectives)
- [Key Features](#key-features)
- [Hardware Used](#hardware-used)
- [System Architecture](#system-architecture)
- [Working Principle](#working-principle)
- [Circuit Diagram](#circuit-diagram)
- [Code](#code)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [Demo Video](#demo-video)
- [Project Report](#project-report)
- [License](#license)

---

## 📖 Overview

This project demonstrates a smart autonomous robot that can follow a line of a specific color. Unlike traditional black-line followers, this robot uses a GY-13 TCS3200 color sensor to distinguish between multiple colors on the track. It is controlled using an Arduino Uno and a motor driver module (L298N).

---

## 🎯 Objectives

- Detect and follow lines of different colors
- Provide accurate path detection using a color sensor
- Design an educational and practical model for robotics applications

---

## 🌟 Key Features

- Supports multiple colors (red, green, blue, black, white)
- Real-time color detection and tracking
- DC motor control via L298N driver
- Portable and cost-effective
- Easy to modify for different use cases

---

## 🔧 Hardware Used

| Component              | Quantity | Description                            |
|------------------------|----------|----------------------------------------|
| Arduino Uno            | 1        | Microcontroller board                  |
| TCS3200 Color Sensor   | 1        | GY-13 module for color detection       |
| L298N Motor Driver     | 1        | For driving DC motors                  |
| DC Motors              | 2        | To move the robot                      |
| Robot Chassis + Wheels| 1        | Base for motor and sensor mounting     |
| Power Supply (Battery) | 1        | 9V/12V rechargeable or dry cell        |
| Jumper Wires           | -        | Connections                            |

---

## Working Principle

1. The TCS3200 color sensor reads the color value beneath it.
2. Arduino compares the RGB values with predefined thresholds.
3. Based on the color detected (e.g., red = turn left, blue = turn right), the robot moves accordingly.
4. The robot follows the predefined color path intelligently.

---

## Circuit Diagram
<img width="2088" height="1244" alt="1000149705" src="https://github.com/user-attachments/assets/55f81cfb-733b-4d61-b800-9996e298e30b" />


## Code
#define IN1 9
#define IN2 10
#define IN3 11
#define IN4 12
#define S0 4
#define S1 5
#define S2 6
#define S3 7
#define sensorOut 8

int red = 0, green = 0, blue = 0;

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  pinMode(S0, OUTPUT);
  pinMode(S1, OUTPUT);
  pinMode(S2, OUTPUT);
  pinMode(S3, OUTPUT);
  pinMode(sensorOut, INPUT);

  digitalWrite(S0, HIGH);
  digitalWrite(S1, LOW);

  Serial.begin(9600);
}

void loop() {
  readColor();

  Serial.print("R: ");
  Serial.print(red);
  Serial.print(" G: ");
  Serial.print(green);
  Serial.print(" B: ");
  Serial.println(blue);

  if (isRed()) {
    turnLeft();
  } else if (isBlue()) {
    turnRight();
  } else if (isGreen()) {
    stopMotors();
  } else if (isYellow()) {
    uTurn();
  } else {
    moveForward();
  }

  delay(300);
}

void readColor() {
  digitalWrite(S2, LOW);
  digitalWrite(S3, LOW);
  red = pulseIn(sensorOut, LOW);

  digitalWrite(S2, HIGH);
  digitalWrite(S3, HIGH);
  green = pulseIn(sensorOut, LOW);

  digitalWrite(S2, LOW);
  digitalWrite(S3, HIGH);
  blue = pulseIn(sensorOut, LOW);
}

bool isRed() {
  return (red < 25 && green > 40 && blue > 40);
}

bool isGreen() {
  return (green < 30 && red > 35 && blue > 35);
}

bool isBlue() {
  return (blue < 25 && red > 40 && green > 40);
}

bool isYellow() {
  return (red < 35 && green < 35 && blue > 45);
}

void moveForward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void stopMotors() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}

void turnLeft() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void turnRight() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void uTurn() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  delay(700);
  stopMotors();
}

