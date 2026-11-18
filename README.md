# Arduino Smart Robotic Car

A team-built Arduino car with two driving modes. An ultrasonic sensor guides obstacle avoidance, and Bluetooth allows manual control.

[Watch the robotic car demo](Robotics_Car.mp4)

## Control modes

| Mode | Input | Response |
| --- | --- | --- |
| Autonomous | Distance from an HC-SR04 ultrasonic sensor | The Arduino uses distance readings to guide obstacle avoidance. |
| Manual | Commands from an HC-05 Bluetooth module | The Arduino sends motor commands through an H-bridge driver. |

## Hardware integration

The build combined sensor input, Bluetooth commands, PWM motor control, DC gear motors, and a chassis. The team assembled and soldered the hardware and iterated on motor driver wiring during testing.

The [build journal](https://github.com/vivekar217220-del/Embedded_Journey/blob/main/What_I_Done) documents L298N wiring and an L293D iteration. This repository contains the demo recording.
