# Arduino Smart Robotic Car

A team-built Arduino vehicle that combines ultrasonic obstacle avoidance with Bluetooth manual control. The project covers how sensor input and wireless commands become motor actions, and how wiring and driver choices affect a moving prototype.

[Watch the hardware demonstration](Robotics_Car.mp4)

## System architecture

```text
HC-SR04 distance readings ──┐
                           ├── Arduino control logic ── H-bridge driver ── Left and right gear motors
HC-05 Bluetooth commands ──┘
```

| Component | Role in the build |
| --- | --- |
| Arduino | Reads inputs, selects actions for the active driving mode, and controls the motor-driver signals. |
| HC-SR04 ultrasonic sensor | Uses the elapsed time between a trigger and echo to estimate the distance to an object ahead. |
| HC-05 Bluetooth module | Receives the operator’s commands and passes them to the Arduino over a serial connection. |
| H-bridge motor driver | Converts logic signals into the drive needed by the motors. Direction inputs select rotation and PWM varies the drive level. |
| Gear motors and chassis | Turn the electrical signals into movement. The two motor channels let the car steer by varying each side’s drive. |

## Control modes

### Autonomous obstacle avoidance

The Arduino reads the front-facing distance sensor and uses that reading to decide how the car should move near an obstacle. The sensing path is **trigger pulse → echo duration → distance estimate → drive decision**. The repository does not include the sketch, so the exact distance threshold and turn sequence cannot be confirmed from the checked-in material.

### Bluetooth manual control

The HC-05 gives a remote operator a serial command path to the Arduino. In manual mode, received commands are translated into motor-driver outputs. The recording is the demonstration artifact. A command map and mode-selection procedure would need the original sketch or controller configuration.

## Wiring and hardware iterations

The [build journal](https://github.com/vivekar217220-del/Embedded_Journey/blob/main/What_I_Done) records an L298N wiring layout and describes an L293D iteration during assembly. The table below summarizes the documented layout for the sensing and command paths.

| Module | Signal | Arduino connection in the journal |
| --- | --- | --- |
| HC-SR04 | TRIG | D9 |
| HC-SR04 | ECHO | D10 |
| HC-05 | TXD → Arduino receive | D2 |
| HC-05 | RXD ← Arduino transmit | D3 |

The journal also records a common ground between the Arduino and motor driver. Treat the journal’s driver table as a reference for that documented iteration. Confirm the actual shield model, its pin assignments, and the Bluetooth breakout’s input-voltage requirements before adapting the wiring.

## What to verify on the bench

1. With the chassis supported, confirm that each motor turns in the intended direction when its channel is driven.
2. Place an object in front of the sensor and check that the reported distance changes as the object moves.
3. Exercise the Bluetooth control path and confirm that each supported command reaches the Arduino and moves the correct motor channels.
4. Exercise obstacle avoidance on a clear floor. Check the reaction when an object enters the path and when the path is clear.

## Repository contents

| Artifact | What it provides |
| --- | --- |
| [Robotics_Car.mp4](Robotics_Car.mp4) | Recording of the assembled robotic car. |
| [Build journal](https://github.com/vivekar217220-del/Embedded_Journey/blob/main/What_I_Done) | Team build notes, wiring references, and debugging lessons. |

The team assembled and soldered the prototype and iterated on the motor-driver integration. The journal acknowledges guidance from Dr. Ravi Kant and Dr. Ankur Changela.
