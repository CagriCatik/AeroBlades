# 🛸 Urumi: Experimental Hybrid VTOL / Quadplane

[![Airframe Type](https://img.shields.io/badge/Airframe-Tailsitter%20VTOL%20Hybrid-blue.svg)](#)
[![Firmware](https://img.shields.io/badge/Firmware-INAV%206.x%20%2F%207.x-green.svg)](#)
[![Print Material](https://img.shields.io/badge/Material-PLA%2B%20%2F%20Standard%20PLA-orange.svg)](#)
[![Print Weight](https://img.shields.io/badge/Plastic%20Weight-571g-green.svg)](#)
[![Print Time](https://img.shields.io/badge/Print%20Time-26h%2030m-orange.svg)](#)
[![Forum Source](https://img.shields.io/badge/RCGroups-Forum%20Thread-FF6600.svg)](https://www.rcgroups.com/forums/showthread.php?4223695-Rifter-Sabre-Scimitar-mini-sized-FPV-cruisers)

> **Urumi** is an experimental hybrid VTOL aircraft combining vertical helicopter hovering (quadcopter mode) with high-speed wing-borne forward flight (aeroplane mode). It features an X-wing layout with four 22° dihedral wings, four brushless motors, a tilting servo camera, and **no moving control surfaces**—steering is achieved entirely via differential motor thrust.

---

## 📸 Aircraft Gallery

| Top View | Front View |
| :---: | :---: |
| ![Urumi Top](media/aircraft_photos/Urumi-top.jpg) | ![Urumi Front](media/aircraft_photos/Urumi-front.jpg) |
| **Side Profile** | **Disassembled Airframe & Removable Wings** |
| ![Urumi Side](media/aircraft_photos/Urumi-side.jpg) | ![Urumi Parts](media/aircraft_photos/Urumi-parts.jpg) |

---

## ⚡ Specifications & Flight Characteristics

| Parameter | Specification | Notes |
| :--- | :--- | :--- |
| **Airframe Weight (Plastic)** | **565 g – 571 g** | Printed mostly in PLA+ / PLA Basic |
| **Dry Weight (with FPV Gear)**| **1035 g** | Without flight battery |
| **All-Up-Weight (AUW)** | **~1215 g** | Including 4S 1500mAh 100C LiPo (~180g) |
| **Wing Dimensions** | 4 wings @ 20 × 20 cm | Equivalent to an 80 × 20 cm single wing area |
| **Wing Dihedral Angle** | **22°** | Optimised for 7" prop clearance while maintaining vertical hover thrust |
| **Transition Airspeed** | **70 – 80 km/h** | Speed at which wings produce full flight lift |
| **Control Surfaces** | **None** | Differential thrust provides pitch, roll, and yaw control |
| **Camera Mechanism** | 9g Servo Tilting Mount | 90° (hover) → 45° (transition) → 0° (forward cruise) |
| **Carbon Spars Required** | **4x** 6.0 mm × 284 mm | Forms rigid central X-frame |

---

## 🖨️ 3D Printing Bill of Materials (ODS Data)

| Part Name | Category Folder | Profile | Infill % / Type | Print Time (P1P) | Weight (g) | Slicing Modifiers |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| **Fuselage 1** | `01_Fuselage/` | B | 0% | 00:47 | 18 | Tilting camera bay |
| **Fuselage 2** | `01_Fuselage/` | A | 4% Gyroid | 03:02 | 58 | 8 top layers |
| **Fuselage 3** | `01_Fuselage/` | C | 0% | 01:01 | 35 | Central carbon spar junction |
| **Fuselage 4** | `01_Fuselage/` | A | 5% Gyroid | 02:55 | 53 | Aft fuselage |
| **Wings 1, 2, 3, 4** | `02_Wings/` | A | 3% Gyroid | 03:10 each | 58 each | 1+2 identical, 3+4 identical |
| **Nacelles 1+2+3+4** | `03_Nacelles_and_Mounts/` | B | 0% | 02:04 | 60 | 1+2 identical, 3+4 identical (+support) |
| **Motor mounts 1-4** | `03_Nacelles_and_Mounts/` | C | 100% Solid | 01:09 | 48 | Solid screw retention |
| **Pads 1+2+3+4** | `03_Nacelles_and_Mounts/` | C | 0% | 00:58 | 29 | Landing pads (all 4 different) |
| **Battery plate** | `04_Internal_Plates/` | A | 8% Gyroid | 00:19 | 11 | 3 walls |
| **FC plate** | `04_Internal_Plates/` | A | 8% Gyroid | 00:15 | 5 | 3 walls |
| **Servo plate** | `04_Internal_Plates/` | A | 8% Gyroid | 00:10 | 5 | 3 walls |
| **Camera mount** | `04_Internal_Plates/` | C | 0% | 00:36 | 8 | Tilting 9g servo mount (+support) |
| **Canopy 1** | `05_Canopy/` | C LW | 10% Gyroid | 00:32 | 8 | Foaming LW-PLA (4 walls, 2 b/t) |
| **Canopy 2** | `05_Canopy/` | C LW | 10% Gyroid | 00:24 | 5 | Foaming LW-PLA (4 walls, 2 b/t) |
| **Canopy locks** | `05_Canopy/` | C | 0% | 00:14 | 4 | Canopy retention latches |
| **Total** | - | - | - | **26:30** | **571 g** | - |

---

## 📂 Project Directory Structure

```
Urumi/
├── README.md                                  # Aircraft documentation (this file)
├── Urumi.ods                                  # Original CAD spreadsheet archive
│
├── 📂 3D_Print_Files/                         # 3MF models organized by assembly stage
│   ├── 01_Fuselage/                           # Fuselage 1, 2, 3, 4
│   ├── 02_Wings/                              # Wing 1-2, Wing 3-4 (with mirroring)
│   ├── 03_Nacelles_and_Mounts/                # Nacelles 1-4, Motor mounts, Landing pads 1-4
│   ├── 04_Internal_Plates/                    # Battery plate, FC plate, Servo plate, Camera mount
│   ├── 05_Canopy/                             # Canopy 1, Canopy 2, Canopy locks
│   └── Extras/                                # Tighter motor mounts, Wing roots 1-4
│
├── 📂 CAD_Source_STEP/                        # 19 raw STEP files for CAD modifications
├── 📂 docs/                                   # Complete 6-document build & flight manual suite
│   ├── 01_HARDWARE_ELECTRONICS.md
│   ├── 02_HARDWARE_PARTS_AND_MECHANICAL.md
│   ├── 03_PRINT_GUIDE_AND_PROFILES.md
│   ├── 04_ASSEMBLY_AND_WIRING.md
│   ├── 05_INAV_FLIGHT_MANUAL.md
│   └── 06_DESIGNER_FLIGHT_LOGS_AND_VIDEO_TRANSCRIPTS.md
│
└── 📂 media/
    ├── aircraft_photos/                       # Assembled aircraft photography
    └── slicer_placement/                      # 11 bed orientation photos
```

---

## 📚 Complete In-Depth Documentation Suite

All detailed manuals, wiring schematics, and tuning guides are located in [`docs/`](docs/):

1. ⚡ **[Hardware Electronics & Configuration Software](docs/01_HARDWARE_ELECTRONICS.md)**
2. 🔩 **[Hardware Parts, Mechanical Structure & Materials](docs/02_HARDWARE_PARTS_AND_MECHANICAL.md)**
3. 🖨️ **[3D Printing Guide & Master Slicer Profiles](docs/03_PRINT_GUIDE_AND_PROFILES.md)**
4. 🛠️ **[Airframe Assembly & Wiring Guide](docs/04_ASSEMBLY_AND_WIRING.md)**
5. ✈️ **[INAV Hybrid VTOL Flight Manual](docs/05_INAV_FLIGHT_MANUAL.md)**
6. 🎬 **[Designer Flight Logs, Video Transcripts & History](docs/06_DESIGNER_FLIGHT_LOGS_AND_VIDEO_TRANSCRIPTS.md)**

---

## 🎬 Video Flight Logs
* 🎥 [Part 1 (Conception & Transition)](https://www.youtube.com/watch?v=R3-GTveqTRI) by Olivier_C
* 🎥 [Part 2 (Crash Investigation & Redesign)](https://www.youtube.com/watch?v=sHy94xdoC1A) by Olivier_C
* 🎥 [Part 3 (Final Flights & Wind Limits)](https://www.youtube.com/watch?v=J87EU8D0PFA) by Olivier_C

[⬅️ Back to Unified Fleet Catalog](../../CATALOG.md)
