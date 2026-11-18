# Obstacle-Avoiding Robotic Car

An Arduino robotic car with two control modes. It uses an ultrasonic sensor to detect nearby obstacles and Bluetooth for manual driving.

[▶ Watch the robotic car demo](Robotics_Car.mp4)

## How it works

| Mode | Input | Response |
| --- | --- | --- |
| Autonomous | Distance from the ultrasonic sensor | The Arduino uses distance to guide obstacle avoidance. |
| Manual | Commands from a Bluetooth controller | The Arduino drives the motors through the motor shield. |

## Hardware

- Arduino and motor driver shield
- Ultrasonic distance sensor and Bluetooth module
- DC gear motors and car chassis

For build notes and hardware iterations, see the [Embedded Systems Journey](https://github.com/vivekar217220-del/Embedded_Journey) [project journal](https://github.com/vivekar217220-del/Embedded_Journey/blob/main/What_I_Done). This repository contains the demo recording.
