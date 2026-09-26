# ⚡ Guide 03: Electronics, Propulsion & Power Systems

[![Guide](https://img.shields.io/badge/Guide-03-blue.svg)](#)
[![Topic](https://img.shields.io/badge/Topic-Motors%20%7C%20ESCs%20%7C%20LiPo%20vs%20Li--ion-orange.svg)](#)

Selecting and wiring the propulsion and power systems for 3D-printed aircraft requires a disciplined balance between weight, electrical efficiency, and heat dissipation. Because 3D-printed airframes have lower thermal conductivity than open carbon quadcopter frames, electronic components must be correctly sized to avoid thermal saturation inside plastic bays.

---

## 1. Fleet Motor & Propeller Sizing Guide

| Airframe | Propulsion Layout | Motor Stator Size | KV Range (3S / 4S) | Recommended Propeller | Thrust / AUW Ratio | Notes |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| **Mini Rifter** | Single Pusher | **1806 – 2204** | 2300–2600KV (3S)<br>1800–2000KV (4S) | 4" – 5" Bullnose / 2-blade | 1.8:1 | Ultra-quiet, low power draw (~8A cruise) |
| **Rifter 3** | Single Pusher | **2207 – 2806.5**| 1700–1950KV (4S) | 6" – 7" Long-range 2-blade | 2.0:1 | High efficiency, low-RPM cruising |
| **Sabre** | Twin Tractor | **1404 – 1806** (×2) | 2400–2800KV (4S) | 4" – 5" Counter-Rotating (CW+CCW) | 3.0+:1 | High-speed interceptor, torque-free launch |
| **Scimitar 3** | Single Pusher | **2207 – 2306** | 1950–2400KV (4S) | 5" – 6" Tri-blade / 2-blade | 2.2:1 | Fast throttle response, acrobatic agility |
| **Sica** | Heavy Twin Tractor | **2207 – 2806.5** (×2)| 1500–1800KV (4S/6S) | 6" – 7" Counter-Rotating (CW+CCW) | 2.5:1 | Heavy payload, gimbal & night flight cruiser |
| **Urumi** | Quad VTOL | **2207 – 2806.5** (×4)| 1800–1950KV (4S) | 7" Low-pitch 2-blade / Tri-blade | 2.5:1 (Hover) | Differential thrust steering, high hover burst current |

### Propeller Orientation Rules:
* **Counter-Rotating Twins (Sabre & Sica)**:
  Always configure twin tractor motors to rotate **Inward-Top** (left motor spins CW, right motor spins CCW when viewed from behind). This directs wash down over the wing root, reduces stall speed, and completely cancels motor gyroscopic torque during hand launches!
* **Pusher Motor Thrust Angle**:
  Ensure pusher motors are installed square to the fuselage thrust line. A 1°–2° upward thrust angle is built into the motor mounts to counter nose-down pitch when throttling up.

---

## 2. ESC Selection & Thermal Management

* **ESC Firmware**: Use **AM32** or **BLHeli_32** ESCs with bi-directional DShot. They offer smooth sine-wave motor startup and efficient low-throttle cruising.
* **Current Rating Headroom**:
  * Always size ESCs with at least **30% continuous amperage headroom** above static bench tests. For example, if a 2207 motor draws 25A at full throttle, use a 35A–45A ESC.
  * *Reason*: Inside enclosed 3D-printed fuselage bays, cooling airflow is lower than on open mini quads.
* **Low-ESR Filter Capacitors**:
  * **Mandatory**: Solder a 35V 470µF – 1000µF Low-ESR electrolytic capacitor (Rubycon ZLH or Panasonic FR) directly at the main battery input pads of the ESC/PDB.
  * High-current motor braking and throttle bursts cause inductive voltage spikes that can permanently destroy delicate 5V/9V BECs and digital FPV transmitters (DJI O3 / Walksnail).

---

## 3. Battery Chemistry: High-C LiPo vs. Li-ion Packs

| Attribute | Standard LiPo (e.g. Tattu R-Line 4S 1500mAh) | Li-ion 18650 Pack (e.g. 4S1P Sony VTC6 3000mAh) | Li-ion 21700 Pack (e.g. 4S1P Molicel P45B 4500mAh) |
| :--- | :---: | :---: | :---: |
| **Energy Density** | Medium (~140 Wh/kg) | **High (~220 Wh/kg)** | **Very High (~250 Wh/kg)** |
| **Discharge Capability (C-Rating)** | **Extreme (80C – 120C continuous)** | Low-Medium (10C – 15C / ~30A continuous) | Medium-High (10C – 15C / ~45A continuous) |
| **Voltage Sag Under Load** | Minimal (< 0.2V per cell) | Noticeable (~0.4V – 0.6V per cell) | Low-Medium (~0.3V per cell) |
| **Minimum Safe Cutoff Voltage**| 3.50 V / cell | **2.80 V / cell** | **2.80 V / cell** |
| **Best Airframe Matches** | **Urumi (VTOL)**, **Sabre (High Speed)** | **Mini Rifter**, **Scimitar 3** | **Rifter 3**, **Sica (Long Range)** |

### Battery Selection Strategy:
1. **Choose LiPo for Urumi & Sabre**:
   * **Urumi** draws 70A–90A total in hover and transition. Li-ion cells will sag below cutoff and trigger an immediate low-voltage shutdown. Use a 4S 1500–2200mAh 100C LiPo.
   * **Sabre** reaches 130+ km/h; its twin motors require instant throttle punch.
2. **Choose Li-ion for Rifter 3 & Sica**:
   * Fixed-wing cruising requires very little power (typically 3A–7A at 50–65 km/h).
   * A 4S1P 21700 pack (Molicel P42A or P45B) delivers **40 to 60+ minutes of continuous flight** in the same footprint as a 20-minute LiPo!
   * ⚠️ *Important*: Configure your OSD and INAV low-battery alarm for Li-ion packs to **3.0V/cell** (12.0V on 4S) instead of standard LiPo 3.5V/cell.

---

## 4. Power Distribution & Wire Sizing (AWG)

* **Main Battery Lead**:
  * 1806–2204 setups (Mini Rifter): **16 AWG** with **XT30** or **XT60**.
  * Twin / Heavy cruisers (Sabre, Sica, Urumi): **12 AWG or 14 AWG** with genuine **XT60**.
* **Motor Phase Wires**:
  * 1806–2207: **18 AWG – 20 AWG** multi-strand silicone wire.
* **BEC Power Routing**:
  * Never power multiple digital metal-gear servos (e.g., Emax ES08MDII) directly from the flight controller's internal 5V 1A BEC. 
  * Use a dedicated external **5V/6V 3A–5A switching BEC** for the servo rail to prevent flight controller brownouts in flight.

---

## 5. 📚 Authoritative References & Citations

1. **Battery Mooch**: *"Molicel P42A and P45B 21700 Benchmarks & Continuous Discharge Ratings"* — Independent laboratory testing verifying 45A CDR, internal resistance, and voltage sag characteristics. [[Mooch's Test Blog](https://www.e-cigarette-forum.com/forum/blog-entry/list-of-battery-tests.7436/)]
2. **Oscar Liang**: *"Why Capacitors Are Important For FPV Drones: Voltage Spikes and Filtering"* — Explains inductive back-EMF, low-ESR requirements, and Panasonic FM/FR and Rubycon ZLH capacitor sizing. [[Oscar Liang](https://oscarliang.com/capacitors-mini-quad/)]
3. **Oscar Liang**: *"Motor Size, Stator Dimensions, and KV Explained"* — Comprehensive tutorial on motor stator volume, torque vs RPM, and propeller matching. [[Oscar Liang](https://oscarliang.com/motors/)]
4. **AM32 / BLHeli_32 Architecture Documentation**: *"Sinusoidal Startup and Variable PWM Frequency for Fixed-Wing Efficiency"* — Multi-rotor and fixed-wing ESC commutation optimization. [[AM32 GitHub](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware)]
