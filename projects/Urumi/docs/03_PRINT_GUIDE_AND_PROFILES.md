# 🖨️ 3D Printing Guide & Master Slicer Profiles

This guide translates the original spreadsheet data (`Urumi.ods`) into actionable presets for **Bambu Studio**, **OrcaSlicer**, and **PrusaSlicer** running on a Bambu Lab P1S/X1C/A1 (or any 200×200×220mm+ 3D printer).

---

## 1. Master Print Profiles Overview

All parts are sliced at **0.20 mm Layer Height**. Create the following profiles in your slicer:

| Profile Name | Layer Height | Wall Loops | Top Shells | Bottom Shells | Base Infill | Infill Pattern | Target Material |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **Profile A** | 0.20 mm | 1 | 3 | 3 | 0% | Gyroid | PLA / PLA+ / ePLA-ST |
| **Profile B** | 0.20 mm | 2 | 4 | 4 | 0% | None | PLA / PLA+ / ePLA-ST |
| **Profile C** | 0.20 mm | 3 | 5 | 5 | 0% | None | PLA / PLA+ / ePLA-ST |
| **Profile D (Solid)** | 0.20 mm | 3 | 5 | 5 | 100% | Rectilinear / Aligned | PLA / PLA+ (Crucial for Motor Mounts) |
| **Profile LW (Canopy)**| 0.20 mm | 4 (or 2 in PLA) | 2 | 2 | 10% | Gyroid | Foaming PLA-LW / ASA-Aero (or PLA Basic) |

---

## 2. Complete Parts Slicing Table (from `Urumi.ods`)

Total Estimated Print Time: **~26 hours 30 minutes** | Total Plastic Weight: **~571 grams**

| Subfolder | Part File Name | Profile | Infill % | Print Time (P1P/P1S) | Weight | Special Modifiers & Slicer Rules |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| `01_Fuselage/` | `Fuselage 1.3mf` | **B** | 0% | ~00:47 | 18g | No infill, no supports. |
| `01_Fuselage/` | `Fuselage 2.3mf` | **A** | 4% | ~03:02 | 58g | **Set 8 top layers** for canopy latch rigidity. 4% Gyroid infill. |
| `01_Fuselage/` | `Fuselage 3.3mf` | **C** | 0% | ~01:01 | 35g | No infill, 3 walls, 5 top/bottom layers. |
| `01_Fuselage/` | `Fuselage 4.3mf` | **A** | 5% | ~02:55 | 53g | 5% Gyroid infill. |
| `02_Wings/` | `Wing 1-2.3mf` (Left 1) | **A** | 3% | ~03:10 | 58g | 1 wall loop, 3% Gyroid infill. Print 1 as-is. |
| `02_Wings/` | `Wing 1-2.3mf` (Right 2) | **A** | 3% | ~03:10 | 58g | **Mirror in slicer (X-axis)** to produce Wing 2. |
| `02_Wings/` | `Wing 3-4.3mf` (Left 3) | **A** | 3% | ~03:10 | 58g | 1 wall loop, 3% Gyroid infill. Print 1 as-is. |
| `02_Wings/` | `Wing 3-4.3mf` (Right 4) | **A** | 3% | ~03:10 | 58g | **Mirror in slicer (X-axis)** to produce Wing 4. |
| `03_Nacelles_and_Mounts/`| `Nacelle 1-2.3mf` | **B** | 0% | ~01:02 | 30g | **Enable Tree Supports on build plate**. |
| `03_Nacelles_and_Mounts/`| `Nacelle 3-4.3mf` | **B** | 0% | ~01:02 | 30g | **Enable Tree Supports on build plate**. |
| `03_Nacelles_and_Mounts/`| `Motor mount 1-2-3-4.3mf` | **D** | 100% | ~01:09 | 48g | **Print 4 copies. Must be 100% solid infill** for motor screw retention! |
| `03_Nacelles_and_Mounts/`| `Pad 1.3mf` | **C** | 0% | ~00:15 | 8g | Landing pad. 3 walls, 5 top/bottom. |
| `03_Nacelles_and_Mounts/`| `Pad 2.3mf` | **C** | 0% | ~00:15 | 7g | Landing pad. |
| `03_Nacelles_and_Mounts/`| `Pad 3.3mf` | **C** | 0% | ~00:15 | 7g | Landing pad. |
| `03_Nacelles_and_Mounts/`| `Pad 4.3mf` | **C** | 0% | ~00:15 | 7g | Landing pad. |
| `04_Internal_Plates/` | `Battery Plate.3mf` | **A** | 8% | ~00:19 | 11g | **Modifier**: Set 3 wall loops, 8% Gyroid infill. |
| `04_Internal_Plates/` | `FC Plate.3mf` | **A** | 8% | ~00:15 | 5g | **Modifier**: Set 3 wall loops, 8% Gyroid infill. |
| `04_Internal_Plates/` | `Servo Plate.3mf` | **A** | 8% | ~00:10 | 5g | **Modifier**: Set 3 wall loops, 8% Gyroid infill. |
| `04_Internal_Plates/` | `Camera mount.3mf` | **C** | 0% | ~00:36 | 8g | **Enable Supports** for camera pivot ears. |
| `05_Canopy/` | `Canopy 1.3mf` | **LW** | 10% | ~00:32 | 8g | 4 walls, 2 bottom, 2 top, 10% Gyroid (if PLA: 1 wall, 5% infill). |
| `05_Canopy/` | `Canopy 2.3mf` | **LW** | 10% | ~00:24 | 5g | 4 walls, 2 bottom, 2 top, 10% Gyroid (if PLA: 1 wall, 5% infill). |
| `05_Canopy/` | `Canopy locks.3mf` | **C** | 0% | ~00:14 | 4g | Print 2 sets. |

---

## 3. Wing Mirroring Instructions

The wings on Urumi are perfectly symmetrical left-to-right:
1. In Bambu Studio, import `3D_Print_Files/02_Wings/Wing 1-2.3mf`.
2. Slice and print your first copy (this is **Wing 1**).
3. Right-click the model on the virtual build plate -> select **Mirror** -> click **X Axis**.
4. Slice and print this mirrored part (this is **Wing 2**).
5. Repeat the exact same procedure for `Wing 3-4.3mf` to produce **Wing 3** (as-is) and **Wing 4** (mirrored).

---

## 4. Bed Placement & Orientation

Refer to the visual guides located in [`media/slicer_placement/`](../media/slicer_placement):
* `Fuselage 1.jpg`, `Fuselage 2.jpg`, `Fuselage 3.jpg`, `Fuselage 4.jpg` show the exact standing orientation on the build plate.
* Always orient tall fuselage parts standing vertically with the flat mating flange down on the plate.
* Use a brim (5mm–8mm) on `Fuselage 1` and `Fuselage 4` to prevent tall print wobbling on high-speed beds.

---

## 5. Bambu Lab P1S Recommended Print Settings

* **Nozzle**: 0.4 mm Stainless or Hardened Steel.
* **Plate**: Textured PEI Plate (clean with warm water and dish soap before large wing prints).
* **Printing Temperature (PLA Basic / PLA+)**: **230°C – 235°C** (The designer explicitly notes that high temperatures are required to ensure maximum layer bonding).
* **Bed Temperature**: 55°C – 60°C.
* **Chamber**: Door slightly ajar or top glass lifted for PLA to avoid heat creep during 3+ hour prints.
* **Cooling Fan**: 50%–70% for thin walls; reduce to 20% on the first 5 layers.
