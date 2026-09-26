# 🛩️ Rifter 3: Full-Size High-Endurance FPV Cruiser

[![Airframe Type](https://img.shields.io/badge/Airframe-Single%20Pusher%20Cruiser%20Gen%203-blue.svg)](#)
[![Print Weight](https://img.shields.io/badge/Plastic%20Weight-430g-green.svg)](#)
[![Print Time](https://img.shields.io/badge/Print%20Time-31h%2040m-orange.svg)](#)
[![Forum Source](https://img.shields.io/badge/RCGroups-Forum%20Thread-FF6600.svg)](https://www.rcgroups.com/forums/showthread.php?4223695-Rifter-Sabre-Scimitar-mini-sized-FPV-cruisers)

> **Rifter 3** is the mature, third-generation evolution of the Rifter single-motor pusher cruiser. Boasting a large high-aspect-ratio wing, dedicated fuselage bays, and modular carbon reinforcement, it delivers exceptional glide ratios and long-range cruising.

---

## 📸 Aircraft Gallery

| Top View | Front View |
| :---: | :---: |
| ![Top](media/aircraft_photos/Rifter3-top.jpg) | ![Front](media/aircraft_photos/Rifter3-front.jpg) |
| **Side Profile** | **Disassembled Airframe & Parts** |
| ![Side](media/aircraft_photos/Rifter3-side.jpg) | ![Parts](media/aircraft_photos/Rifter3-parts.jpg) |

---

## ⚡ Specifications & Engineering Data

| Parameter | Specification | Notes |
| :--- | :--- | :--- |
| **Airframe Configuration** | Single-motor pusher cruiser with V-tail | High efficiency glider/cruiser |
| **Total Printed Weight** | **430 g** | Standard PLA+ / LW-PLA setup |
| **Total Print Time** | **31 hours 40 minutes** | Bambu Lab P1P / P1S reference |
| **Carbon Spars Required** | **Front Spar:** 8.0 mm × 800 mm<br>**Rear Spar:** 6.0 mm × 400 mm<br>**Fuselage Spars (optional):** 2x 6.0 mm × 135 mm | High rigidity carbon spars |
| **Control Surfaces** | 2 Wing Ailerons + V-Tail Stabs | Precision flight stability |
| **Recommended Propulsion** | 2207 – 2806.5 brushless motor, 6"–7" folding or fixed prop | Rear-mounted quiet pusher |
| **Battery Compatibility** | 4S 18650 / 21700 Li-ion packs (up to 4000–5000mAh) or 4S LiPo | Long range endurance |
| **FPV System Support** | Analog, Walksnail, DJI O3, GPS mast mount | SCM nose & dedicated GPS plate |

---

## 🖨️ 3D Printing Bill of Materials (ODS Data)

| Part Name | Category Folder | Profile | Infill % / Type | Print Time (P1P) | Weight (g) | Slicing Modifiers |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| **Fuselage 1** | `01_Fuselage/` | B | 0% | 00:38 | 17 | Nose camera bay |
| **Fuselage 2** | `01_Fuselage/` | B | 100% Solid | 00:10 | 4 | Forward bulkhead |
| **Fuselage 3** | `01_Fuselage/` | A | 4% Gyroid | 02:41 | 37 | Main electronics cabin |
| **Fuselage 4** | `01_Fuselage/` | A | 4% Gyroid | 02:50 | 42 | Rear fuselage section |
| **Fuselage 5** | `01_Fuselage/` | B | 0% | 00:25 | 6.5 | Tail boom cone |
| **Hatch** | `01_Fuselage/` | B | 10% Gyroid | 00:20 | 10 | 2 bottom, 2 top layers |
| **Wing L/R 1** | `02_Wings/` | A | 6% Gyroid | 00:34 each | 11 each | 1 wall, 3 top/bottom |
| **Wing L/R 2** | `02_Wings/` | A (PMLW) | 4% Gyroid | 02:33 each | 36 each | Pre-foamed LW / PLA+ |
| **Wing L/R 3** | `02_Wings/` | A (PMLW) | 4% Gyroid | 03:19 each | 47 each | Extended wing section |
| **Wing L/R 4** | `02_Wings/` | B (LW) | 6% Gyroid | 01:26 each | 20 each | Wingtip section |
| **Wing Ailerons L & R** | `02_Wings/` | A | 6% Gyroid | 01:48 each | 12 each | 12 bottom layers |
| **Wing locks L & R** | `02_Wings/` | B / D | 100% Solid | 00:18 | 8.5 | Glueless wing locking |
| **Stabs LR (V-tail)** | `03_Tail_and_Stabs/` | A (LW) | 7% Gyroid | 01:04 each | 14 each | Foaming PLA-LW |
| **Motor mount** | `03_Tail_and_Stabs/` | B / D | 100% Solid | 00:12 | 3.5 | Solid screw retention |
| **Battery plate** | `04_Internal_Plates/` | B | 10% Gyroid | 00:16 | 9 | - |
| **Canopy** | `05_Canopy/` | A | 4% Gyroid | 02:03 | 20 | Main top hatch |
| **Canopy lock** | `05_Canopy/` | D | 100% Solid | 00:10 | 4 | - |
| **Total** | - | - | - | **31:40** | **430 g** | - |

---

## 📂 Project Directory Structure

```
Rifter_3/
├── README.md
├── Rifter3.ods
├── 3D_Print_Files/
│   ├── 01_Fuselage/           # Fuselage 1-5, Hatch
│   ├── 02_Wings/              # Wings 1-4 (L/R), Ailerons (L/R), Wing locks
│   ├── 03_Tail_and_Stabs/     # V-tail Stabs, Motor mount
│   ├── 04_Internal_Plates/    # Battery plate
│   ├── 05_Canopy/             # Canopy, Canopy lock
│   └── Extras/                # SCM camera nose, GPS plate
├── CAD_Source_STEP/           # 14 complete CAD STEP models
└── media/
    ├── aircraft_photos/       # High-res photos of assembled Rifter 3
    └── slicer_placement/      # 13 slicer bed orientation photos
```

---

## 🎬 Video Flight Logs
* 🎥 [Rifter 3 Flight Test](https://www.youtube.com/watch?v=L3LojPVs68U) by Olivier_C
* 🎥 [Rifter 2 Historic Video](https://www.youtube.com/watch?v=LL8X9GLXXWU) by Olivier_C

[⬅️ Back to Unified Fleet Catalog](../../CATALOG.md)
