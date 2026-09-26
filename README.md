# USB-C_powered_IMU_breakout_board
To power and interface the IMU on my Self Balancing Bot

# USB-C powered IMU breakout board
A small KiCad project: USB-C 5V input, regulated to 3.3V via an LDO, broken out to I2C for interfacing an MPU6050 IMU.

## Why
Built to power and interface the IMU on my Self-Balancing Robot project without relying on breadboard wiring.

## Design
- USB-C connector (power only, CC pulldowns (5.1k x2) for power negotiation)
- AMS1117-3.3 LDO regulator with input/output decoupling
- I2C breakout header (SDA, SCL, 3.3V, GND) with 4.7k pullups

## Process

To design a simple 2-layer PCB in KiCad that takes 5V USB-C input, regulates it down via an LDO, and breaks out I2C pins for a sensor (here, an IMU), the process from schematic to fabrication-ready files is as follows:

### Schematic

USB-C connector — chosen as the power input since it's the modern standard. It includes CC1/CC2 configuration channel pins, which signal to the power source (laptop, charger, etc.) that a valid device is present, enabling it to supply power. These pins are pulled down through 5.1k resistors so the source recognizes the connection.

LDO (Low Dropout Regulator) — a linear DC voltage regulator. Since the IMU's logic operates at 3.3V while USB-C supplies 5V, the LDO steps the voltage down. LDOs are well suited to small voltage drops like this, unlike larger step-downs which dissipate excess power as heat. Input and output capacitors (Cin, Cout) suppress voltage spikes and noise at the regulator's pins, ensuring a stable rail.

I2C (Inter-Integrated Circuit) — a communication protocol allowing multiple devices to share a single two-wire bus (SDA, SCL). I2C uses an open-drain design, meaning devices can only pull a line low, never drive it high — this prevents conflicts when multiple devices share the bus. Pull-up resistors (4.7k) are required to hold the lines high by default.

IMU module (MPU6050) — requires power, ground, and the two I2C lines. A solid ground connection is essential for reliable communication.

### PCB Design

Following the schematic, footprints were placed to keep routing paths short and direct. Using the ratsnest as a guide, appropriate trace widths were assigned — 10 mil for SDA/SCL signal lines, 20 mil for VCC/3V3/GND power lines. Routing was completed across two copper layers: B.Cu dedicated to GND (as a filled zone), and F.Cu for all other nets.

## Status
- [x] Schematic
- [x] PCB layout
- [x] Gerber files

## Tools
KiCad 8.x

## License
MIT (or your choice)
