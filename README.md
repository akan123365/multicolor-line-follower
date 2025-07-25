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

##  System Architecture
---

## Working Principle

1. The TCS3200 color sensor reads the color value beneath it.
2. Arduino compares the RGB values with predefined thresholds.
3. Based on the color detected (e.g., red = turn left, blue = turn right), the robot moves accordingly.
4. The robot follows the predefined color path intelligently.

---

## Circuit Diagram
---

## 💻 Code
