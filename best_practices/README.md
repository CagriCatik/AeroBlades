# 🛠️ AeroBlades Fleet Best Practices & Engineering Guides

[![Documentation Type](https://img.shields.io/badge/Docs-Fleet%20Best%20Practices-blue.svg)](#)
[![Applicability](https://img.shields.io/badge/Applicability-All%20Airframes-green.svg)](#)
[![Focus](https://img.shields.io/badge/Focus-3D%20Printing%20%7C%20Avionics%20%7C%20Power-orange.svg)](#)

Welcome to the **AeroBlades Engineering Best Practices Suite**. While each aircraft project in [`projects/`](../projects/) contains its individual 3D models and CAD data, this directory serves as the **master knowledge base** for successfully manufacturing, outfitting, and flying 3D-printed FPV cruisers and hybrid VTOL platforms.

Whether you are printing your first **Mini Rifter**, assembling a high-speed twin **Sabre**, wiring a long-range **Sica**, or commissioning the quad-motor **Urumi**, these guides distill proven aerodynamic principles, mechanical material analysis, and electronics integration standards.

---

## 📚 Master Engineering Guides

| Guide | Core Topic | Key Questions Answered | Quick Link |
| :--- | :--- | :--- | :---: |
| **01. Material Selection & Filaments** | Material engineering, composites & thermodynamics | Should I use Aero ASA? Where is PLA+ mandatory? Why do active foaming filaments fail on high-speed wings? | [Read Guide](01_MATERIALS_AND_FILAMENT_SELECTION.md) |
| **02. 3D Printing & Slicing Setup** | Slicer optimization, tolerances & bed adhesion | How does the thin-wall gyroid truss system work? How do I account for carbon spar hole shrinkage? | [Read Guide](02_3D_PRINTING_AND_SLICER_SETUP.md) |
| **03. Electronics, Propulsion & Power** | Motors, ESCs, LiPo vs Li-ion batteries | What stator size and KV for pusher vs twin tractor? When should I use 21700 Li-ion cells vs high-C LiPos? | [Read Guide](03_ELECTRONICS_PROPULSION_AND_POWER.md) |
| **04. Avionics, FPV & RF Integration** | Flight controllers, INAV, GPS hygiene, FPV | How far must GPS be from DJI O3? How do I prevent compass magnetic interference from motor lines? | [Read Guide](04_AVIONICS_FPV_AND_RF_INTEGRATION.md) |
| **05. References & Authoritative Sources** | Industry benchmarks, citations & manufacturer TDS | What testing proves active-foaming strength reduction? What are Mooch's verified 21700 cell ratings? | [Read Guide](05_REFERENCES_AND_CITATIONS.md) |

---

## ⚡ The 5 Golden Rules of AeroBlades Aircraft

1. **Rigidity Outweighs Theoretical Lightness:**  
   A wing printed 20% lighter in weak foaming filament that flutters and twists in a dive will crash. A stiff wing printed in PLA+ or tough filament flies faster, cruises more efficiently, and withstands high G-forces.
2. **Never Print Motor Mounts or Locks in Foaming Material:**  
   Foaming filaments (LW-PLA, Aero ASA) suffer from low inter-layer tensile strength and creep under screw compression. Use solid **PETG**, **standard ABS/ASA**, or **solid PLA+** for high-stress retention.
3. **Separate High-Current Power from Sensitive RF Sensors:**  
   Keep motor and battery lines at least 50mm–80mm away from the GPS compass and radio receiver antennas. Digital FPV transmitters (DJI O3, Walksnail) must be ventilated and physically isolated from UHF/ELRS receivers.
4. **Always Test-Fit Carbon Spars Before Gluing:**  
   Slicer hole expansion, material shrinkage (1.0%–1.5% on ASA), and seam blobs inside spar channels can cause carbon tubes to jam. Ream channels gently with a 6.0mm or 8.0mm drill bit or round file before assembly.
5. **Center of Gravity (CG) is Non-Negotiable:**  
   A 3D-printed plane with a rearward CG is unrecoverable. Always balance your plane slightly nose-heavy on the marked molded CG dimples before every maiden flight.
