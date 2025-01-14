# Gaming Gun 

This project aims to enhance the mobile gaming experience by simulating touch inputs on the screen using a gaming gun. It leverages the Android Debug Bridge (ADB) for touch simulation, where processing occurs on a Raspberry Pi that controls button inputs from the user. it enhances your Real time gaming experience.

## Features

- **Touch Simulation:** Simulates touch inputs on mobile devices using ADB commands.
- **Sensor Integration:** Utilizes MPU9250 for accelerometer and gyroscope data, and HMC5883L for magnetometer data.
- **Real-time Interaction:** Processes sensor data in real-time to provide smooth gaming controls.
- **User Input Control:** Uses GPIO buttons for user inputs.

## Requirements

- Raspberry Pi (preferably Raspberry Pi 3 or later)
- MPU9250 sensor
- HMC5883L sensor (GY-273)
- ADB installed on your Raspberry Pi
- Python 3.x
- Required Python libraries:
  - `smbus2`
  - `RPi.GPIO`
  - `statistics`
  
To install the required Python libraries, you can use pip:

```bash
pip install smbus2 RPi.GPIO
```
## Hardware Setup

- Connect the MPU9250 sensor to the Raspberry Pi using I2C interface.
- Connect the HMC5883L sensor to the Raspberry Pi using I2C interface.
- Connect GPIO buttons to the specified pins on the Raspberry Pi.

## Code Overview

The main code is written in Python and can be found in the `gaming_gun.py` file.

Below is a brief overview of the code structure:

**Initialization Functions:**

* `MPU_Init()`: Initializes the MPU9250 sensor.
* `HMC5883L_Init()`: Initializes the HMC5883L sensor.

**Data Reading Functions:**

* `read_raw_data(addr)`: Reads raw accelerometer and gyroscope data.
* `read_HMC5883L_data()`: Reads magnetometer data from the HMC5883L sensor.

**Calculating Orientation:**

* `calculate_pitch_roll_yaw(Ax, Ay, Az, Gy, Mx, My, Mz, prev_Y)`: Calculates pitch, roll, and yaw based on sensor data.

**ADB Interaction:**

* `adb_swipe(end_x, end_y)`: Sends swipe commands to the mobile device using ADB.

**Input Handling:**

* GPIO inputs are read to determine user interaction, triggering ADB commands based on sensor data analysis.

**Usage**

1. Ensure your mobile device is connected to the Raspberry Pi and ADB is properly configured.
2. Run the script on the Raspberry Pi:

```bash
python gaming_gun.py
```
3. Use the physical buttons connected to the Raspberry Pi to interact with the game. The code will read sensor data and simulate touch inputs based on your movements.

