# Arduino Solar Tracker using LDR Sensors and Servo Motor

## Overview

This project implements a simple **single-axis solar tracking system** using an Arduino, two LDR (Light Dependent Resistor) sensors, and a servo motor. The system continuously compares light intensity detected by the LDRs and adjusts the servo position to keep a solar panel facing the strongest light source.

## Components Required

- Arduino Uno/Nano
- 2 × LDR (Light Dependent Resistors)
- 2 × 10kΩ Resistors
- Servo Motor (SG90 or similar)
- Breadboard
- Jumper Wires
- Solar Panel (optional)

## Circuit Connections

| Component | Arduino Pin |
|------------|-------------|
| East LDR | A0 |
| West LDR | A1 |
| Servo Signal | D9 |
| Servo VCC | 5V |
| Servo GND | GND |

## Working Principle

1. The Arduino reads light intensity from two LDR sensors:
   - East LDR (A0)
   - West LDR (A1)

2. The difference between the sensor readings is calculated.

3. If the east sensor detects significantly more light than the west sensor, the servo rotates toward the east.

4. If the west sensor detects significantly more light than the east sensor, the servo rotates toward the west.

5. When both sensors detect low light levels (nighttime), the servo automatically returns to its starting position.

## Features

- Automatic solar tracking
- Single-axis movement
- Night reset functionality
- Adjustable sensitivity threshold
- Servo angle limits for safe operation

## Code Parameters

| Variable | Description | Default Value |
|-----------|------------|--------------|
| `calibration` | Sensor calibration offset | 600 |
| `servoposition` | Initial servo angle | 90° |
| `error` | Difference between LDR readings | Dynamic |
| Threshold | Tracking sensitivity | ±15 |

## Servo Movement Range

- Minimum Angle: 20°
- Maximum Angle: 150°
- Initial Position: 90°

## Algorithm

```text
Read East LDR
Read West LDR

If both readings are low:
    Return servo to home position

Calculate error = East - West

If error > 15:
    Move servo right

If error < -15:
    Move servo left

Repeat
```

## Installation

1. Open Arduino IDE.
2. Install the Servo library (included with Arduino IDE).
3. Copy and paste the code into a new sketch.
4. Connect the hardware according to the wiring table.
5. Select the correct board and COM port.
6. Upload the sketch to the Arduino.

## Applications

- Solar panel tracking systems
- Light-following robots
- Educational electronics projects
- Renewable energy demonstrations

## Future Improvements

- Dual-axis solar tracking
- LCD display for sensor values
- Real-time monitoring
- Battery charging integration
- Automatic calibration

## License

This project is open-source and may be modified and distributed for educational and personal use.
