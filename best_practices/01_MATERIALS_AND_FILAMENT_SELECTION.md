# 🧪 Guide 01: Material & Filament Selection

[![Guide](https://img.shields.io/badge/Guide-01-blue.svg)](#)
[![Topic](https://img.shields.io/badge/Topic-Filament%20Engineering%20%26%20Thermodynamics-orange.svg)](#)

Choosing the correct 3D printing material is the single most critical decision in manufacturing a 3D-printed aircraft. Unlike static ornamental prints, an aircraft airframe experiences continuous aerodynamic bending, torsional twisting, motor vibration, thermal exposure to direct sunlight, and high shock deceleration on landing.

This guide provides an engineering-grade evaluation of materials for the **AeroBlades** fleet, specifically dissecting the trade-offs between **Aero ASA (LW-ASA)**, **PLA+**, **LW-PLA**, **PETG**, and **TPU**.

---

## 1. The Core Dilemma: Stifness vs. Weight vs. Heat

A common misconception in 3D-printed aviation is that **lighter is always better**. In practical RC flight dynamics, this is only true if structural stiffness is preserved:

1. **Bending & Torsional Rigidity (Young's Modulus)**:
   When an aircraft dives at 80–120 km/h or pulls a 4G turn, the wings experience intense aerodynamic lift and torsional twisting (twist along the span). If the material has a low modulus of elasticity, the wing will twist dynamically, causing **aeroelastic flutter**—which strips servos or causes catastrophic structural failure.
2. **Inter-Layer Tensile & Shear Strength**:
   Active-foaming materials create a micro-cellular foam structure. While this cuts weight by up to 50%, it drastically weakens the bond between printed layers. Parts subjected to shear forces (wing locks, motor mounts, landing pads) snap easily.
3. **Glass Transition Temperature ($T_g$) & Thermal Creep**:
   Dark-colored PLA softens at approximately 55°C–60°C. In summer sun or inside a locked car (where interior cabin temperatures reach 65°C+), a thin PLA wing will permanently sag and distort under its own weight.

---

## 2. Comprehensive Material Comparison Matrix

| Filament Type | Density ($\text{g/cm}^3$) | Tensile Modulus (Stiffness) | Glass Transition ($T_g$) | Inter-layer Adhesion | UV / Weather Resistance | Slicer Ease of Print |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **PLA+ / Tough PLA** | 1.24 | **Very High (~3.5 GPa)** | ~55°C – 60°C | **Exceptional** | Moderate (degrades in direct wet weather) | ⭐⭐⭐⭐⭐ (Zero warp, no enclosure needed) |
| **Aero ASA / LW-ASA** (e.g. ColorFabb LW-ASA) | **~0.60 – 0.75** (foamed) | **Low (~1.0 – 1.3 GPa)** | **High (~98°C – 105°C)** | Moderate | **Exceptional** (UV immune, zero sun fade) | ⭐⭐⭐ (Enclosed chamber required, warping risk) |
| **Active Foaming LW-PLA** (e.g. ColorFabb LW-PLA) | **~0.55 – 0.65** (foamed) | **Low (~1.0 GPa)** | ~55°C | Low | Poor | ⭐⭐⭐ (High stringing, temperature sensitive) |
| **Pre-Foamed LW-PLA** (e.g. Polymaker PolyLite LW) | ~0.80 – 0.85 (fixed) | Medium (~2.2 GPa) | ~58°C | Medium-High | Moderate | ⭐⭐⭐⭐ (Prints like standard PLA, no stringing) |
| **PETG / PETG-CF** | 1.25 – 1.27 | High (~2.6 – 3.2 GPa) | ~75°C – 80°C | **Very High** | High | ⭐⭐⭐⭐ (Slight stringing, good bed grip) |
| **Standard Solid ASA/ABS** | 1.05 – 1.08 | High (~2.3 – 2.6 GPa) | **High (~95°C – 105°C)** | High | **Exceptional** | ⭐⭐⭐ (Requires 45°C+ heated chamber) |
| **TPU 95A** | 1.20 | Flexible (Elastomer) | - | **Virtually Indestructible** | High | ⭐⭐⭐⭐ (Slow print speed, direct drive) |

---

## 3. Deep Dive: Should You Use Aero ASA (LW-ASA)?

### ✅ When Aero ASA is the BEST Choice:
* **Canopies & Top Hatches (`05_Canopy/`)**:
  The canopy is situated on top of the airframe, receives 100% of solar radiation, and houses electronics that generate internal heat. Printing canopies in Aero ASA saves significant weight high above the center of gravity while remaining completely immune to sun warping.
* **Non-Structural Fairings, GPS Mounts & Nose Bay Hatches**:
  Where parts only act as aerodynamic wind covers and do not carry flight bending loads.
* **Warm Climate Flight Operations**:
  If you regularly fly in ambient temperatures above 32°C (90°F) or store your models in vehicles, Aero ASA eliminates thermal sagging on exterior fairings.

### ❌ When Aero ASA is the WRONG Choice:
* **High-Speed Wing Panels (`02_Wings/`)**:
  Airframes like **Sabre** (twin-tractor, 120+ km/h) or **Scimitar 3** experience immense aerodynamic pressure. Aero ASA's low torsional modulus can result in severe wing flex and flutter unless you thicken walls significantly (which defeats the weight savings).
* **Motor Mounts (`03_Tail_and_Stabs/`, `03_Nacelles/`)**:
  Brushless motors generate operational heat (50°C–70°C) and violent rotational vibration. Under screw clamping force, foamed Aero ASA will suffer from **material creep**—the motor mounting screws will lose tension in flight, leading to motor detachment.
* **Wing Snap Latches & Spar Sockets**:
  The shear strength of active-foamed layers is roughly 40%–50% that of solid PLA+ or PETG. Hard landings will snap the retention teeth immediately.

---

## 4. Component-by-Component Material Assignment Matrix

Use this authoritative assignment matrix when slicing parts across any **AeroBlades** aircraft:

| Subsystem Component | Primary Recommended Material | Alternative Option | Strict Rule / Avoidance |
| :--- | :--- | :--- | :--- |
| **Wing Panels & Ailerons** | **PLA+ / Tough PLA** | Pre-Foamed LW-PLA (PolyLite) or Standard ASA | ❌ Never use Active Foaming LW-PLA on high-speed wings without carbon spar trusses |
| **Fuselage Electronics Bays** | **PLA+** | Standard ABS / ASA | ⚠️ Ensure adequate airflow vents for ESC and VTX cooling |
| **Canopies & Sun Hatches** | **Aero ASA (LW-ASA)** | Active Foaming LW-PLA or Standard PLA+ | ✅ Ideal use case for lightweighting and sun protection |
| **Motor Mounts & Nacelles** | **PETG** or **Standard Solid ASA** | High-temp PLA+ (if motors run cool) | ❌ **NEVER** use foaming materials (Aero ASA / LW-PLA) |
| **Wing Locks & Joiner Latches** | **PLA+** or **PETG** | Solid ASA | ❌ Never use lightweight or foaming filament |
| **Battery & Flight Controller Plates** | **PLA+** | PETG / Carbon-filled PLA | ❌ Avoid brittle silk filaments |
| **Landing Skids & Nose Skids** | **PETG** or **TPU 95A** | Solid PLA+ | ⚠️ Needs impact and abrasion resistance on grass/gravel |
| **Control Surface Hinges** | **TPU 95A** (100% Solid) | Nylon fabric hinge tape | ❌ Never print live hinges in rigid PLA or ASA |

---

## 5. Printing Tips & Slicer Profiles for Key Filaments

### A. Tuning Aero ASA (LW-ASA)
* **Chamber Temperature**: Enclosed printer required. Chamber temperature should reach at least **45°C–50°C** before starting to avoid warping and delamination on long spans.
* **Nozzle Temperature & Foaming**: Foaming activates between **230°C and 255°C**.
  * 230°C: Low foaming, higher tensile strength, density ~0.80 g/cm³.
  * 250°C: Maximum foaming, density ~0.60 g/cm³, reduced layer strength.
* **Flow Rate (Extrusion Multiplier)**: Set to **55% – 65%** at 250°C.
* **Shrinkage Compensation**: Scale X and Y dimensions by **100.8% – 101.2%** to ensure carbon spars slide smoothly into printed channels.

### B. Tuning PLA+ for High Rigidity
* **Nozzle Temperature**: 210°C – 220°C (higher temperature promotes superior layer fusion).
* **Cooling Fan**: 60% – 80% (avoid 100% fan on thin-wall perimeters to maintain maximum interlayer weld strength).
* **Flow Rate**: 98% – 100%.

### C. Tuning TPU 95A for Control Surface Hinges
* **Orientation**: Lay hinges completely flat on the build plate.
* **Walls & Infill**: 2–3 perimeter walls, **100% solid infill**.
* **Speed**: 25 – 35 mm/s on direct drive extruders. Ensure retraction is low (0.8–1.2mm) to prevent extruder jamming.

---

## 6. Recommended Filament Brands

* **PLA+**: eSun PLA+, Bambu Lab PLA Tough / Basic, Sunlu PLA+, Polymaker PolyMax PLA.
* **Aero ASA / LW-ASA**: ColorFabb LW-ASA, eSun LW-ASA.
* **Pre-Foamed PLA**: Polymaker PolyLite Light Weight PLA (no active foaming, prints with standard PLA settings).
* **PETG**: Bambu Lab PETG-CF, eSun PETG, Prusament PETG.
* **TPU**: Overture TPU 95A, Polymaker PolyFlex TPU95-HF, Bambu TPU 95A.

---

## 7. 📚 Authoritative References & Citations

1. **CNC Kitchen (Stefan Hermann)**: *"Testing Foaming Filaments: Mass Savings vs. Mechanical Strength"* — Demonstrates tensile capacity and inter-layer bond reduction in active-foaming LW materials. [[CNC Kitchen](https://www.cnckitchen.com/)]
2. **colorFabb Technical Documentation**: *"colorFabb LW-ASA Printing Guidelines"* — Expansion ratios, foaming temperature thresholds (230°C–260°C), and flow rate reduction curves. [[colorFabb Learn](https://learn.colorfabb.com/)]
3. **colorFabb Technical Documentation**: *"colorFabb LW-PLA Technical Guide"* — Slicing single-wall aerodynamic shells with zero retraction. [[colorFabb LW-PLA](https://learn.colorfabb.com/how-to-print-with-lw-pla/)]
4. **Polymaker**: *"PolyLite Light Weight PLA Technical Data Sheet"* — Fixed micro-balloon pre-foaming vs active chemical foaming mechanical comparison. [[Polymaker TDS](https://polymaker.com/)]
5. **Olivier_C**: *"Rifter, Sabre, Scimitar: mini-sized FPV cruisers"* — Airframe structural test logs and Bambu P1P print profiles. [[RCGroups Thread #4223695](https://www.rcgroups.com/forums/showthread.php?4223695-Rifter-Sabre-Scimitar-mini-sized-FPV-cruisers)]
