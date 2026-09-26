# 📖 Guide 05: References, Citations & Authoritative Sources

[![Guide](https://img.shields.io/badge/Guide-05-blue.svg)](#)
[![Type](https://img.shields.io/badge/Type-Citations%20%26%20Industry%20Benchmarks-purple.svg)](#)

The engineering rules, material recommendations, and electronics guidelines documented throughout the **AeroBlades Best Practices Suite** are grounded in empirical testing, manufacturer technical data sheets (TDS), independent laboratory benchmarks, and established aerospace/FPV community standards.

This document compiles the authoritative internet sources, test archives, and technical references underpinning this repository.

---

## 1. 3D Printing Materials & Mechanical Testing

### 🔬 CNC Kitchen (Stefan Hermann) — Empirical Mechanical Testing
* **"Testing Foaming Filaments: Mass Savings vs. Mechanical Strength"**  
  *Source:* [CNC Kitchen YouTube & Blog](https://www.cnckitchen.com/)  
  *Key Finding:* Demonstrates that active-foaming filaments (LW-PLA and LW-ASA) trade away up to 40%–50% of their inter-layer tensile strength and shear modulus in exchange for mass reduction. Concludes that high-stress functional components (motor mounts, latches, control horns) should always remain solid non-foaming materials (PLA+, PETG, or standard ASA), with carbon fiber spars used to provide primary bending and torsional rigidity.
* **"Layer Adhesion vs. Nozzle Temperature in FDM 3D Printing"**  
  *Source:* [CNC Kitchen Material Testing Database](https://www.cnckitchen.com/blog/layer-adhesion-temperature)  
  *Key Finding:* Higher print temperatures (e.g., 215°C–225°C for PLA+) significantly improve polymer chain entanglement across layers, yielding up to 30% higher Z-axis tensile strength—critical for thin-wall aircraft wings.

### 🏭 Manufacturer Technical Data Sheets (TDS) & Foaming Guides
* **colorFabb: LW-ASA (Lightweight ASA) Technical Guidelines**  
  *Source:* [colorFabb LW-ASA Documentation](https://learn.colorfabb.com/)  
  *Key Parameter:* Active foaming begins at ~230°C and reaches maximum expansion at 250°C–260°C, increasing volume up to 2.5× (density drops from 1.07 g/cm³ to ~0.55–0.65 g/cm³). Recommends lowering extrusion flow multiplier to 45%–60% and printing inside an enclosed chamber at 45°C+ to mitigate warping.
* **colorFabb: LW-PLA Printing & Slicing Manual**  
  *Source:* [colorFabb LW-PLA Technical Guide](https://learn.colorfabb.com/how-to-print-with-lw-pla/)  
  *Key Parameter:* Outlines the temperature-dependent density curve and highlights why active foaming materials are best suited for single-wall aerodynamic shells with zero retract or minimal retraction (1–2mm) to prevent hotend clogging.
* **Polymaker: PolyLite Light Weight PLA Data Sheet**  
  *Source:* [Polymaker Industrial & Consumer TDS](https://polymaker.com/)  
  *Key Parameter:* Explains pre-foamed (stabilized micro-balloon) PLA technology: achieves ~0.80 g/cm³ without temperature-activated foaming, offering superior print fidelity, zero stringing, and higher Young's modulus than active-foaming filaments.

---

## 2. Power Systems, Batteries & Electrical Safety

### 🔋 Battery Mooch (Independent Cell Benchmarking)
* **Molicel 21700 P42A & P45B Comprehensive Lab Tests**  
  *Source:* [Mooch's Battery Test Archive on E-Cigarette Forum](https://www.e-cigarette-forum.com/forum/blog-entry/list-of-battery-tests.7436/)  
  *Key Benchmark:*
  * **Molicel P42A**: 4000mAh min / 4200mAh typ, independently verified at **45A Continuous Discharge Rating (CDR)**. Proven baseline for high-current endurance packs.
  * **Molicel P45B**: 4500mAh typ, **45A CDR**, featuring ~33% lower internal resistance ($DC-IR$) than P42A, resulting in substantially lower voltage sag and cooler operation at high throttle.
* **Li-ion Voltage Sag Curve in Fixed-Wing Cruise**  
  *Source:* [Mooch: Voltage Cutoff and Cell Longevity Analysis](https://www.e-cigarette-forum.com/)  
  *Key Guidance:* High-density cylindrical cells can safely be discharged down to 2.80V–3.00V per cell under load, whereas standard pouch LiPos must never be drawn below 3.50V per cell.

### ⚡ Oscar Liang — FPV Electrical Engineering
* **"Why Capacitors Are Important for FPV ESCs"**  
  *Source:* [Oscar Liang: FPV Drone Capacitor Guide](https://oscarliang.com/capacitors-mini-quad/)  
  *Key Recommendation:* Fast motor braking and rapid PWM switching create violent inductive back-EMF voltage spikes that exceed component ratings. Mandates **low-ESR** capacitors (specifically **Panasonic FM/FR** or **Rubycon ZLH** series) soldered directly across the ESC power rails to protect sensitive 5V BECs and digital FPV transmitters.
* **"Choosing the Right Motor Size and KV for RC Planes"**  
  *Source:* [Oscar Liang FPV Knowledgebase](https://oscarliang.com/motors/)  
  *Key Recommendation:* Power-to-weight budgeting, thermal dissipation in enclosed fuselages, and why high-stator low-KV motors swinging larger propellers yield significantly higher thrust-per-watt efficiency in cruise.

---

## 3. Avionics, Antennas & RF Link Hygiene

### 📡 ExpressLRS (ELRS) Official Documentation
* **"Antenna Orientation, Polarization, and Placement Best Practices"**  
  *Source:* [ExpressLRS Official Hardware Wiki](https://www.expresslrs.org/)  
  *Key Principles:*
  * **Polarization Matching:** Linear dipole/T-antennas must maintain vertical alignment between transmitter and receiver to avoid a ~20dB cross-polarization signal penalty.
  * **Carbon Fiber Standoff:** Carbon is electrically conductive and attenuates RF. Active antenna elements must maintain at least **30mm clearance** from carbon tubes and large battery masses.
  * **Diversity Orthogonal Layout:** Dual-antenna receivers should orient elements at a 90° angle (L-shape) to eliminate antenna radiation null zones during banking turns.

### 🧭 INAV & ArduPilot Autopilot Frameworks
* **INAV Fixed Wing Official Guide & Documentation**  
  *Source:* [INAV GitHub Wiki & Docs](https://github.com/iNavFlight/inav/wiki)  
  *Key Guidance:* Comprehensive autolaunch configuration, PIFF controller tuning for flying wings and cruisers, fail-safe Return-to-Home (RTH) altitude parameters, and Li-ion fuel-gauge calibration.
* **ArduPilot: Compass Magnetic Interference (CompassMot) Documentation**  
  *Source:* [ArduPilot Compass Calibration Guide](https://ardupilot.org/copter/docs/common-compass-setup-advanced.html)  
  *Key Principle:* Explains how high-current DC traces generate magnetic fields according to Ampère’s law ($B \propto I / r$). Mandates physical separation of at least 60mm–100mm between compass sensors and battery/ESC power cables.

---

## 4. Primary Airframe Source & Designer Logs

### ✈️ RCGroups: Olivier_C FPV Cruiser Community
* **"Rifter, Sabre, Scimitar : mini-sized FPV cruisers" (Thread #4223695)**  
  *Source:* [RCGroups Forum Thread](https://www.rcgroups.com/forums/showthread.php?4223695-Rifter-Sabre-Scimitar-mini-sized-FPV-cruisers)  
  *Author:* **Olivier_C**  
  *Contribution:* Origin of the **AeroBlades** airframe geometries, thin-wall gyroid construction technique, carbon spar layout, and Bambu P1P flight-tested print profiles for Mini Rifter, Rifter 3, Sabre, Scimitar 3, Sica, and Urumi.
