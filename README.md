# USB-C_powered_IMU_breakout_board
To power and interface the IMU on my Self Balancing Bot

# USB-C powered IMU breakout board
A small KiCad project: USB-C 5V input, regulated to 3.3V via an LDO, broken out to I2C for interfacing an MPU6050 IMU.

## Why
Built to power and interface the IMU on my Self-Balancing Robot project without relying on breadboard wiring.

## Design
- USB-C connector (power only, CC pulldowns for power negotiation)
- AMS1117-3.3 LDO regulator with input/output decoupling
- I2C breakout header (SDA, SCL, 3.3V, GND) with 4.7k pullups

## Status
- [x] Schematic
- [x] PCB layout

## Tools
KiCad 8.x

## License
MIT (or your choice)
