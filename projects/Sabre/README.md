# 🗡️ Sabre: High-Speed Twin-Tractor FPV Plank

[![Airframe Type](https://img.shields.io/badge/Airframe-Twin%20Tractor%20Plank-blue.svg)](#)
[![Print Weight](https://img.shields.io/badge/Plastic%20Weight-476g-green.svg)](#)
[![Print Time](https://img.shields.io/badge/Print%20Time-45h%2041m-orange.svg)](#)
[![Forum Source](https://img.shields.io/badge/RCGroups-Forum%20Thread-FF6600.svg)](https://www.rcgroups.com/forums/showthread.php?4223695-Rifter-Sabre-Scimitar-mini-sized-FPV-cruisers)

> **Sabre** is a fast, aggressive twin-tractor "plank" cruiser. With twin counter-rotating tractor motors mounted on wing nacelles and an un-swept plank wing layout, Sabre delivers blistering acceleration, locked-in pitch stability, and thrilling low-altitude carving.

---

## 📸 Aircraft Gallery

| Top View | Front View |
| :---: | :---: |
| ![Top](media/aircraft_photos/Sabre-top.jpg) | ![Front](media/aircraft_photos/Sabre-front.jpg) |
| **Side Profile** | **Disassembled Airframe & Parts** |
| ![Side](media/aircraft_photos/Sabre-side.jpg) | ![Parts](media/aircraft_photos/Sabre-parts.jpg) |

---

## ⚡ Specifications & Engineering Data

| Parameter | Specification | Notes |
| :--- | :--- | :--- |
| **Airframe Configuration** | Twin-motor tractor plank with twin stabilizers | Fast forward cruiser |
| **Total Printed Weight** | **476 g** | Standard PLA+ setup |
| **Total Print Time** | **45 hours 41 minutes** | Bambu Lab reference |
| **Carbon Spars Required** | **Front Spar:** 6.0 mm × 680 mm<br>**Rear Spar:** 6.0 mm × 320 mm | Dual hollow carbon spars |
| **Control Surfaces** | 2 Wing Elevons / Ailerons | Servo bays embedded in wings |
| **Recommended Propulsion** | 2x 1404 – 1806 brushless motors, 4"–5" counter-rotating props | Differential thrust capable |
| **Battery Compatibility** | 4S 1500–2200mAh LiPo or 4S 18650 Li-ion pack | Ample central battery tray |
| **FPV System Support** | GoPro / RunCam, DJI O3, Walksnail, Analog | Dedicated GoPro & SCM nose options |

---

## 🖨️ 3D Printing Bill of Materials (ODS Data)

| Part Name | Category Folder | Profile | Print Time | Weight (g) | Slicing Modifiers |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Fuselage 1** | `01_Fuselage/` | B | 01:03 | 12 | Standard nose |
| **Fuselage 2** | `01_Fuselage/` | D | 00:44 | 5 | Forward firewall |
| **Fuselage 3** | `01_Fuselage/` | A | 05:04 | 59 | Main payload cabin |
| **Fuselage 4** | `01_Fuselage/` | A | 05:36 | 62 | Aft fuselage |
| **Hatch** | `01_Fuselage/` | B | 01:49 | 14 | 20% infill |
| **Wing L/R 1** | `02_Wings/` | A | 02:26 each | 27 each | 1 wall, 3 top, 0 infill |
| **Wing L/R 2** | `02_Wings/` | A | 03:26 each | 43 each | Wing center section |
| **Wing L/R 3** | `02_Wings/` | B | 01:32 each | 18 each | Wing outer tip |
| **Wing Ailerons L & R** | `02_Wings/` | A | 01:35 each | 9 each | 10 bottom layers + raft |
| **Wing locks L & R** | `02_Wings/` | D | 00:44 each | 4 each | Wing retention latches |
| **Wing servos L & R** | `02_Wings/` | D | 01:15 | 9 | Servo covers / mounts |
| **Nacelles L & R** | `03_Nacelles_and_Mounts/` | B | 00:59 each | 12 each | Twin motor nacelles |
| **Motor mount LR** | `03_Nacelles_and_Mounts/` | D | 00:56 each | 6 each | Solid 100% infill |
| **Stabs LR** | `03_Nacelles_and_Mounts/` | B | 01:13 each | 19 each | Align flat to build plate |
| **Battery plate** | `04_Internal_Plates/` | D | 01:28 | 11 | Align flat to build plate |
| **FC plate** | `04_Internal_Plates/` | D | 00:50 | 5 | Flight controller tray |
| **Hinges (TPU)** | `04_Internal_Plates/` | D | 00:20 | 2 | Flexible 95A TPU |
| **Canopy** | `05_Canopy/` | A | 01:40 | 20 | Main top canopy |
| **Canopy lock** | `05_Canopy/` | D | 00:10 | 1 | Quick-release latch |
| **Total** | - | - | **45:41** | **476 g** | - |

---

## 📂 Project Directory Structure

```
Sabre/
├── README.md
├── Sabre.ods
├── 3D_Print_Files/
│   ├── 01_Fuselage/           # Fuselage 1-4, Hatch
│   ├── 02_Wings/              # Wings 1-3 (L/R), Ailerons, Locks, Servos
│   ├── 03_Nacelles_and_Mounts/# Nacelles (L/R), Motor mounts, Stabs
│   ├── 04_Internal_Plates/    # Battery plate, FC plate, TPU hinges
│   ├── 05_Canopy/             # Canopy, Canopy lock
│   └── Extras/                # GoPro RC predator nose, SCM nose
├── CAD_Source_Fusion/         # 18 native parametric Fusion 360 (.f3d) models
└── media/
    ├── aircraft_photos/       # High-res photos of assembled Sabre
    └── slicer_placement/      # 21 slicer bed orientation photos
```

---

## 🎬 Video Flight Logs
* 🎥 [Sabre Flight Demonstration](https://www.youtube.com/watch?v=Vm1uSv3ZKd4) by Olivier_C

[⬅️ Back to Unified Fleet Catalog](../../CATALOG.md)
