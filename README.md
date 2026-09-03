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

## Process
To design a simple 2 layer PCB in KiCAD that takes 5V USB-C input, regulates it down (LDO) and breaks out I2C pins for a sensor (Here IMU) the process from designing the schematic to the KiCAD files is as below:

First the schematic: why the USB-C Connector? its the power input or power connector form the source and is the modern standard and it has 2 channel configuration pins CC1 and CC2 (These indicate to the power source be it laptop or chargers to recognizes the device and supply power). These pins are connected to 5.1k pull down resistors.

Next the LDO (Low Dropout Regulator) regulator its a linear DC voltage regulator and since the IMU logic runs at 3.3V but USB-C gives a 5V the regulator steps it down (close range step down). The Cin and Cout also help in suppressing voltage spikes and noise at the regulator pins.

Then comes the I2C (Inter-Integrated Circuit) which is the communication protocol which allows multiple devices to work using a single, shared bus. Since its an open drain bus ( as it uses only 2 wires for data communication - SDA and SCL to allow it not short circuit it relies on these open drain pins with pull up resistors) so the devices on it can pull the line low never drive it high hence the 4.7k resistors. 

Next the sensor used here the IMU module (MPU6050) which needs power, ground and the 2 I2C lines. Connection to ground is a necessity.

## Status
- [x] Schematic
- [x] PCB layout

## Tools
KiCad 8.x

## License
MIT (or your choice)
