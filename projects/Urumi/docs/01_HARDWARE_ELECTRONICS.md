# ⚡ Hardware Electronics & Configuration Software Guide

> **Urumi VTOL Hybrid** — Complete guide for electronic components, wiring specifications, and software tools for configuring ESCs, brushless motors, flight controller, tilt servo, FPV, and radio receiver.

---

## 1. Software Tools for ESC, Motor & Avionics Configuration

To configure, test, and tune the electronics, use the following specialized software tools:

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                               CONFIGURATION SOFTWARE SUITE                              │
├──────────────────────────┬─────────────────────────────┬────────────────────────────────┤
│ Subsystem                │ Primary Software Tool       │ Platform & Connection Type     │
├──────────────────────────┼─────────────────────────────┼────────────────────────────────┤
│ ESCs & Motor Rotation    │ ESC-Configurator / BLHeli32 │ Web (Chrome/Edge) or Win App   │
│ Flight Controller & VTOL │ INAV Configurator (v7.x)    │ Desktop App (Win/Mac/Linux)    │
│ Radio Receiver (ELRS)    │ ExpressLRS Configurator     │ Desktop App / Web (10.0.0.1)   │
│ FPV System (DJI O3/O4)   │ DJI Assistant 2 (Consumer)  │ Desktop App (USB-C to Air Unit)│
└──────────────────────────┴─────────────────────────────┴────────────────────────────────┘
```

---

### 1.1 ESC & Motor Configuration Software

You do **not** need to unsolder motor wires to reverse spin directions. The flight controller connects via **USB passthrough** directly to the 4-in-1 ESC.

#### Tool 1: [ESC-Configurator.com](https://esc-configurator.com) (Recommended for BLHeli_S / Bluejay / AM32)
* **How to run**: Open Google Chrome, Brave, or Microsoft Edge, navigate to `https://esc-configurator.com`, plug your flight controller via USB, and power the ESC with a flight battery.
* **Key capabilities**:
  * **Motor Direction**: Click to reverse spin direction for any motor without swapping solder pads.
  * **Firmware Flashing**: Flash **Bluejay** firmware onto BLHeli_S ESCs to enable bi-directional DShot and RPM filtering.
  * **PWM Frequency**: Set PWM frequency to **48 kHz** (greatly improves motor efficiency, reduces heat, and extends hover time compared to default 24 kHz).
  * **Motor Beeping**: Enable beacon beeps so motors sound an acoustic alarm if the aircraft is lost in tall grass.

#### Tool 2: BLHeliSuite32 / [BLHeli32 Web](https://open-txu.org/blheli32-configurator/) (For BLHeli_32 ESCs)
* **How to run**: Windows standalone executable (`BLHeliSuite32.exe`) or web-based configurator.
* **Key settings**:
  * **Motor Protocol**: Set to **DShot600** or **DShot300**.
  * **Motor Timing**: Set to `Auto` or `16°–20°` for large 2806.5 / 2807 stator motors.
  * **Rampup Power**: Set to 25%–35% for smooth, high-torque motor startup with 7-inch props.
  * **Brake on Stop**: Enabled.

---

### 1.2 Flight Controller Software: [INAV Configurator](https://github.com/iNavFlight/inav-configurator/releases)

The core brain of the hybrid aircraft is managed entirely via **INAV Configurator** (Version 6.x or 7.x):

* **Firmware Flasher**: Flash the target firmware (e.g. `SPEEDYBEEF405WING` or `MATEKF405TE`).
* **Ports Tab**:
  * Allocate **UART1** for DJI MSP DisplayPort OSD.
  * Allocate **UART2** for ExpressLRS Serial RX (CRSF protocol).
  * Allocate **UART3** for GPS Module (115200 baud).
  * Enable **I2C** for external compass.
* **Configuration Tab**:
  * Enable Barometer, Magnetometer (Compass), and Accelerometer.
  * Set physical board alignment (FC arrow points forward to the nose).
* **Motors Tab**:
  * Motor protocol: `DSHOT300` or `DSHOT600`.
  * Verify motor order (Quad-X layout: M1 Rear Right, M2 Front Right, M3 Rear Left, M4 Front Left).
  * Safe Motor Testing: Use the master slider (with **props off!**) to verify all 4 motors spin correctly.
* **Outputs Tab**:
  * Route servo output **S5** to the camera tilt mechanism.
* **Modes Tab**:
  * Map your 3-position transmitter switch (CH8) to `Mixer Profile 1` / `Mixer Profile 2`.

---

### 1.3 Radio Link: [ExpressLRS Configurator](https://www.expresslrs.org/)
* Flash the latest ELRS firmware to the receiver.
* Enter your unique **Binding Phrase** so your transmitter and receiver pair instantly without manual bind buttons.
* Alternatively, power the receiver without turning on the transmitter; after 30 seconds, it enters Wi-Fi mode. Connect to `ExpressLRS RX` Wi-Fi on your phone or PC and browse to `http://10.0.0.1`.

---

### 1.4 FPV Video: DJI Assistant 2 (Consumer Drones Series)
* If using the **DJI O3 or O4 Air Unit**, download *DJI Assistant 2 (Consumer Drones Series)* from the DJI website.
* Connect via USB-C to activate the unit and update to the latest firmware.
* In the DJI Goggles menu, enable **MSP Canvas mode** to display the INAV OSD (groundspeed, battery voltage, horizon bar, and active mixer profile).

---

## 2. Complete Electronics Component Breakdown

```
                       +-----------------------------+
                       |    Flight Battery (4S-6S)   |
                       +--------------+--------------+
                                      | (XT60)
                                      v
+-------------------------------------+-------------------------------------+
|                     45A - 60A 4-in-1 ESC (Central Stack)                   |
|  [Motor 1 Out]         [Motor 2 Out]         [Motor 3 Out]        [Motor 4 Out]
+-------+---------------------+---------------------+---------------------+--+
        |                     |                     |                     |
        v (3 wires)           v (3 wires)           v (3 wires)           v (3 wires)
   +----+-----+          +----+-----+          +----+-----+          +----+-----+
   | Motor 1  |          | Motor 2  |          | Motor 3  |          | Motor 4  |
   | (Top L)  |          | (Top R)  |          | (Bot L)  |          | (Bot R)  |
   +----------+          +----------+          +----------+          +----------+

                                      | (VBAT + Current + Telemetry)
                                      v
+-------------------------------------+-------------------------------------+
|                      INAV Flight Controller (F405 / F722)                 |
|                                                                           |
|  • PWM S1-S4: ESC Motor Signals 1-4                                       |
|  • PWM S5   : Camera Tilt Servo Signal (EMAX ES08MA II)                   |
|  • UART1    : DJI O3 / O4 Air Unit (MSP DisplayPort OSD)                  |
|  • UART2    : ExpressLRS 2.4GHz Receiver (CRSF Protocol)                  |
|  • UART3    : GPS Module (U-blox SAM-M10Q @ 115200 baud)                 |
|  • I2C1     : Compass (SCL / SDA for QMC5883L / IST8310)                  |
|  • 5V / 9V  : High-power BEC for Camera, VTX, Servo, and GPS              |
+---------------------------------------------------------------------------+
```

---

### 2.1 Brushless Propulsion Motors (4 Required)

Urumi relies completely on differential thrust across its 4 motor nacelles for steering in forward flight.

| Propulsion Setup | Recommended Stator Sizes | 4S Voltage KV | 6S Voltage KV | Recommended Propeller | Characteristics |
| :--- | :--- | :---: | :---: | :--- | :--- |
| **7-Inch Setup (Recommended)** | 2806.5, 2807, 2507, or 2306.5 | **1600 – 1950 KV** | **1250 – 1500 KV** | Gemfan 7040 bi-blade / HQProp 7x4x2 | Superior hovering efficiency, low noise, high forward cruising thrust. |
| **6-Inch Setup (Agile/Sport)** | 2207 or 2306 | **2400 – 2550 KV** | **1750 – 1950 KV** | HQProp 6x4 bi-blade / Gemfan 6042 | Higher acceleration, aggressive climb, smaller footprint. |

#### Top Recommended Motor Models:
* **7" Cruiser**: *BrotherHobby Avenger 2806.5*, *Emax ECO II 2807*, *T-Motor Velox V3 2306*.
* **6" Sport**: *T-Motor F60 Pro IV*, *iFlight XING2 2207*, *Emax ECO II 2306*.

---

### 2.2 Electronic Speed Controllers (ESCs)

* **Form Factor**: **4-in-1 ESC** (30.5×30.5mm or 20×20mm mounting).
* **Current Rating**: **45A to 60A continuous** (burst 65A+).
* **Firmware**: BLHeli_32, BLHeli_S (flashed to Bluejay), or AM32.
* **Recommended Models**:
  * *SpeedyBee 50A 4-in-1 ESC* (Budget, high performance, robust solder tabs).
  * *Holybro Tekko32 F4 50A 4-in-1* (Premium BLHeli_32, metal heatsink, excellent telemetry).
  * *Skystars KM55A 32Bit 4-in-1*.

---

### 2.3 Flight Controller (FC)

The FC must support INAV VTOL dual-mixer profiles and feature onboard barometer and dedicated servo power:

| Model | Mounting | Built-in BEC | Why It Fits Urumi |
| :--- | :---: | :---: | :--- |
| **SpeedyBee F405 WING APP** | Universal | 5V 5A & 9V 2A | Engineered specifically for VTOL / Fixed-wing; wireless Bluetooth setup via mobile phone app. |
| **Matek F405-VTOL / F405-WTE** | 30.5×30.5 | 5V 5A & 9V/12V 2A | Dedicated hybrid VTOL flight controller with dual BEC rails and native INAV profiles. |
| **SpeedyBee F405 V4 Multirotor Stack** | 30.5×30.5 | 5V 2A & 9V 2A | Compact multirotor stack; requires routing servo power to a separate 5V BEC. |

---

### 2.4 Tilt Mechanism Servo

* **Type**: Standard 9g micro metal-gear servo.
* **Model**: **EMAX ES08MA II** (Analog or Digital) or *Corona DS-929MG*.
* **Specifications**:
  * Operating Voltage: 4.8V – 6.0V
  * Torque: 1.8 kg/cm @ 4.8V (plenty of holding power against high-speed aerodynamic wind resistance).
  * Mounting Hole Pitch: **27.6 mm** (exact match for the pre-drilled holes in `Servo Plate`).

---

### 2.5 Navigation & Rescue (GPS + Compass)

Urumi requires an external GPS and digital compass module for automated Return-to-Home (RTH), position hold, and orientation recovery:

* **Recommended Models**:
  * **Matek M10Q-5883**: High-sensitivity u-blox SAM-M10Q GNSS receiver with onboard QMC5883L digital compass.
  * **Holybro Micro M10 GPS**: Includes IST8310 compass, fast satellite acquisition (GPS, Galileo, GLONASS, BeiDou).
* **Wiring**:
  * TX/RX wired to FC UART3 (GPS data).
  * SCL/SDA wired to FC I2C bus (Compass data).
  * 5V and GND.

---

### 2.6 FPV Camera & Video Transmitter (VTX)

* **Primary System (Direct Fit)**: **DJI O3 Air Unit** or **DJI O4 Air Unit**.
  * The camera cage in `Camera mount` has an internal width of **20.2 mm**, designed specifically for DJI O3/O4 camera modules.
* **Alternative Systems (19mm Micro Cameras)**:
  * **Walksnail Avatar HD Pro Micro** / **Caddx Vista Nebula Pro** / **RunCam Phoenix 2 (Analog)**.
  * Add a 0.5mm 3D-printed washer or nylon shim on each side to span the 20.2mm bracket.

---

### 2.7 Radio Receiver & Flight Batteries

* **Radio Receiver**:
  * **ExpressLRS (ELRS) 2.4GHz Diversity Receiver** (e.g. *RadioMaster RP3* or *BetaFPV SuperD*). Dual antennas ensure seamless signal reception whether the plane is sitting vertically in hover or banking horizontally.
* **Battery Configurations**:
  * **Acro & Sport Flying**: **4S 1500mAh – 2200mAh (100C)** LiPo (~180g – 240g). Gives ~5–7 minutes of spirited mixed flying.
  * **High-Efficiency Long Cruise**: **4S1P 21700 Li-Ion (4200mAh – 4500mAh)** built with *Molicel INR21700-P42A* or *P45B* cells (~290g). Once transitioned onto its wings, the low current draw enables 20–30+ minutes of cruising.
  * **6S Option**: 6S 1300mAh – 1800mAh 100C LiPo (when using 6S low-KV motors).
