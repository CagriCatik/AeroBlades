# 🖨️ Guide 02: 3D Printing & Slicer Setup

[![Guide](https://img.shields.io/badge/Guide-02-blue.svg)](#)
[![Topic](https://img.shields.io/badge/Topic-Slicing%20%7C%20Tolerances%20%7C%20Truss%20Infill-orange.svg)](#)

Unlike conventional 3D-printed aircraft that rely on complex spiral vase mode or fragile single-wall internal rib models, the **AeroBlades** fleet by Olivier_C uses a unique, robust construction methodology: **thin exterior walls reinforced by a continuous 3D Gyroid infill truss core**.

This guide details the precise slicer settings, orientation strategies, and dimensional compensation techniques required to print perfect, warp-free airframes.

---

## 1. The Olivier_C Thin-Wall Gyroid Philosophy

Most aircraft STL files in this repository are solid or hollow geometries designed to be sliced with specific perimeter and infill combinations:

```
[Exterior Airflow Surface: 1-2 Smooth Perimeters]
  └── [Internal Volume: 3% - 6% Gyroid Infill Core (Isotropic 3D Truss)]
        └── [Structural Spine: Continuous Carbon Fiber Tube Sockets]
```

### Why Gyroid Infill?
* **Isotropic Strength**: Unlike rectilinear or grid infill (which only support forces in X/Y planes), Gyroid is a 3D triply periodic minimal surface that provides uniform resistance against bending, torsional twisting, and shear loads in all 3 axes.
* **Continuous Airflow & Wire Pass-Through**: The curved channels of gyroid infill allow internal servo cables and antenna leads to be fished through wings without needing pre-cut wiring tunnels.
* **Lightweight Efficiency**: At only 3% to 6% density, gyroid adds massive torsional rigidity to thin wings while adding only a few grams of weight.

---

## 2. Master Slicing Profiles Cheat Sheet

All models in the fleet are tuned for **0.4mm nozzles** and **0.20mm layer heights** in **Bambu Studio**, **OrcaSlicer**, or **PrusaSlicer**:

| Profile Code | Profile Name | Perimeters (Walls) | Top / Bottom Layers | Infill % & Pattern | Typical Weight/Speed Balance | Typical Use Cases |
| :---: | :--- | :---: | :---: | :---: | :--- | :--- |
| **Profile A** | Thin / Aero | 1 | 3 / 3 | 3% – 6% Gyroid | Maximum lightness, high surface fidelity | Wing panels, elevons, ailerons, main fuselage cabins |
| **Profile B** | Medium | 2 | 4 / 4 | 0% – 10% Gyroid | Balanced strength & impact resistance | Nose bays, tail cones, winglets, vertical stabs |
| **Profile C** | Heavy Structural | 3 – 4 | 5 / 5 | 0% or 10% Gyroid | Maximum rigidity, solid hard points | Landing pads, wing locks, battery trays, camera brackets |
| **Profile D** | Solid Retention | 4 – 5 | 5 / 5 | 100% Rectilinear | Extreme shear & thread grip strength | Motor mounts, servo brackets, alignment pins |
| **Profile LW**| Active Foaming | 1 – 2 | 2 / 2 | 8% – 10% Gyroid | Ultra-lightweight (0.55–0.65 density) | Aerodynamic canopies, sun covers, non-structural fairings |
| **TPU** | Flexible Hinge | 2 – 3 | 4 / 4 | 100% Solid | Flexible elastic live hinge | Wing control surface hinges (95A TPU) |

---

## 3. Dimensional Tolerances & Carbon Spar Channels

All airframes in this fleet incorporate longitudinal hollow channels designed for **6.0 mm** and **8.0 mm** outer diameter (OD) pultruded carbon fiber tubes.

### The Problem: Hole Undersizing
Due to plastic thermal shrinkage and 3D printing inner-hole polygon faceting, printed holes are virtually always **0.1mm to 0.25mm smaller** than their nominal CAD dimensions. If not compensated, carbon spars will bind or crack the wing root during insertion.

### Recommended Slicer Settings:
1. **X-Y Hole Compensation (OrcaSlicer / Bambu Studio)**:
   * Set **X-Y Hole Compensation**: `+0.10 mm` to `+0.15 mm`.
   * Leave **X-Y Contour Compensation**: `0.0 mm` (maintains true outer aerodynamic airfoil profile).
2. **ASA / ABS Shrinkage Factor**:
   * If printing with ASA or ABS, apply an overall X/Y scale compensation of **100.8% to 101.2%**.
3. **Manual Workshop Reaming**:
   * Always have a standard 6.0mm or 8.0mm round file or metal drill bit on hand.
   * Slide the carbon spar into each segment dry *before* applying adhesive. The spar should slide through with light thumb pressure—never force a spar with a hammer.

---

## 4. Bed Adhesion & Orientation Best Practices

Many fuselage and wing segments stand **180mm to 240mm tall** on the build plate with a relatively narrow footprint. Preventing mid-print detachment or corner warping is paramount:

### 1. Build Plate Preparation
* **Textured PEI Plate**: Strongly recommended for PLA+, PETG, and ASA. Wash thoroughly with hot water and dish soap (Dawn / Fairy) to remove finger oils. Do not rely solely on Isopropyl Alcohol (IPA), which merely spreads grease.
* **Brim Configuration**:
  * For tall, slender wing panels: Enable an **Outer Brim of 5 mm – 10 mm** with a **0.1 mm Brim-Object Gap** for clean removal.
  * For flat-bottom fuselage parts: Brim can usually be disabled if bed leveling is properly calibrated.

### 2. Seam Placement Strategy
* Never use *Random* seam placement on aerodynamic surfaces—it creates hundreds of tiny drag-inducing pimples across the wing airfoil.
* Set **Seam Position**: **Aligned** or **Rear**.
* Position the seam along the **trailing edge** of the wing or inside the fuselage lock recess where airflow disturbance is minimized.

### 3. Cooling Fan Management
* **PLA+**: Set part cooling fan to **50%–70%**. Avoid blasting 100% fan on 1-perimeter wing shells, as rapid chilling reduces inter-layer fusion strength.
* **ASA / ABS**: Cooling fan **10%–20% maximum**, enclosed chamber at 45°C+.
* **PETG**: Cooling fan **20%–40%** to avoid brittle inter-layer bonding.

---

## 5. Post-Processing & Airframe Bonding

* **Cyanoacrylate (CA Glue) + Accelerator**:
  * Medium-viscosity CA glue (e.g., Gorilla Super Glue, BSI Insta-Cure+) is the gold standard for PLA+ and PETG aircraft assembly.
  * Lightly scuff bonding mating surfaces with 240-grit sandpaper before gluing.
  * Use aerosol activator sparingly to set alignment pins instantly.
* **Polyurethane / Epoxy for Spars**:
  * For permanently bonded carbon spars, use **5-minute or 15-minute 2-part epoxy**. Epoxy fills micro-voids between the round spar and printed internal ribs without melting the plastic.
