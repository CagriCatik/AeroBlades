# 🛠️ Step-by-Step Airframe Assembly & Wiring Guide

> **Urumi VTOL Hybrid** combines a central fuselage with a rigid 4-point carbon-fiber X-frame, four angled wings (22°), four motor nacelles, and a servo-actuated tilting FPV camera.

---

## 1. Required Hardware, Consumables & Tools

### Structural & Fasteners
* **4x Carbon Fiber Tubes**: **6.0 mm Outer Diameter × 284 mm Length** (hollow pultruded tube, 4mm ID).
* **Medium Cyanoacrylate (CA Glue)** (e.g. *Bob Smith Insta-Cure+* or *Gorilla Super Glue*).
* **CA Accelerator / Activator Spray** (essential for rapid, strong bonding).
* **16x M3 × 6mm or 8mm socket screws**: For motor mounting.
* **4x M3 × 20mm screws & nylon standoffs/nuts**: For the FC / ESC central stack.
* **2x M2 × 8mm self-tapping screws**: For mounting the 9g tilt servo.
* **4x M2 × 4mm or 6mm screws**: For mounting the FPV camera (DJI O3/O4 or micro camera).
* **1x Non-slip Battery Strap**: 20mm × 200mm or 250mm.
* **Threadlocker (Blue Loctite 242)**: For all motor screws.

### Tools
* 1.5mm, 2.0mm, and 2.5mm hex screwdrivers.
* 6.0mm round file or drill bit (for cleaning out carbon tube channels if needed).
* Fine-grit sandpaper (240–400 grit) for smoothing mating bulkheads.
* Soldering iron (60W+) with 60/40 or lead-free solder and flux.

---

## 2. Airframe Assembly Sequence

```
Assembly Flow:
[Fuselage 1-4 + Carbon Spars] ──> [Internal Plates & Tilt Servo] ──> [Modular Wings] ──> [Nacelles & Motors]
```

### Step 1: Fuselage Alignment & Carbon Spar Insertion
1. Gather the four printed fuselage sections: `Fuselage 1` (nose), `Fuselage 2`, `Fuselage 3`, and `Fuselage 4` (tail).
2. **Dry Fit the Carbon Tubes**:
   * Slide the four 6.0mm × 284mm carbon tubes through the X-frame channels in `Fuselage 2` and `Fuselage 3`.
   * Ensure each tube slides smoothly without forcing. If tight, gently run a 6.0mm drill bit or round file through the printed channels.
3. **Bonding the Fuselage**:
   * Apply medium CA glue to the mating flanges of `Fuselage 2` and `Fuselage 3`.
   * Press firmly together, ensuring the internal carbon tube alignment holes match perfectly.
   * Mist the seam with CA accelerator.
   * Join `Fuselage 1` (nose) and `Fuselage 4` (tail) in the same manner.

---

### Step 2: Internal Mounting Plates & Tilt Mechanism
1. **Flight Controller Plate (`FC Plate`)**:
   * Slide `FC Plate` into its dedicated internal fuselage slots.
   * Secure your 4-in-1 ESC and Flight Controller onto the vibration-damping silicone bobbins using M3 hardware. (Supports both 30.5×30.5mm and 20×20mm hole patterns).
2. **Battery Plate (`Battery Plate`)**:
   * Thread your 20mm battery strap through the bottom slots of `Battery Plate` before gluing or snapping it into the fuselage bay.
   * Add a strip of adhesive silicone or foam padding to prevent LiPo pack slippage.
3. **Tilt Servo Installation (`Servo Plate`)**:
   * Mount the 9g metal-gear servo (e.g., *EMAX ES08MA II*) into `Servo Plate` using 2x M2 screws.
   * Center the servo electrically using a servo tester or FC output (1500µs midpoint) before attaching the servo horn.
4. **Camera Tilt Mount (`Camera mount`)**:
   * Mount your FPV camera (DJI O3, DJI O4, or 19mm micro camera) into `Camera mount` using M2 screws.
   * Snap or pin the camera mount into the pivot brackets in `Fuselage 1`.
   * Connect a short pushrod or direct-drive link from the 9g servo horn to the camera mount arm.

---

### Step 3: Modular Removable Wing System
Urumi features a glueless, removable wing locking design:
1. Slide **Wing 1** (top left) and **Wing 2** (top right) onto the top carbon spars.
2. Slide **Wing 3** (bottom left) and **Wing 4** (bottom right) onto the bottom carbon spars.
3. Push each wing firmly until the root aerofoil locks into the fuselage recess.
4. The motor mounts and nacelles act as the outer wing retaining locks—preventing the wings from sliding off during flight.

---

### Step 4: Motor Mounts, Nacelles & Landing Pads
1. Slide `Motor mount 1-2-3-4` onto the outer tip of each carbon fiber spar.
   * *Note*: If the spar fit feels slightly loose, use `3D_Print_Files/Extras/Motor mount 1-2-3-4.tighter by 05mm.3mf`.
2. Secure the brushless motors to the mounts using 4x M3 screws per motor with blue Loctite.
3. Slide `Nacelle 1-2` and `Nacelle 3-4` into place over the wingtips and mounts.
4. Snap on `Pad 1`, `Pad 2`, `Pad 3`, and `Pad 4` onto the bottom of each nacelle to form the landing feet.

---

## 3. Full Electronics Wiring Diagram

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

### Motor Direction & Numbering (INAV Multirotor Quad-X Convention)
* **Motor 1**: Rear Right (CCW)
* **Motor 2**: Front Right (CW)
* **Motor 3**: Rear Left (CW)
* **Motor 4**: Front Left (CCW)

---

## 4. Pre-Flight Physical Checks
1. **Spar Rigidity**: Hold the fuselage firmly and check each wing for torsional play. There should be zero wobble along the 6mm carbon spars.
2. **Propeller Clearance**: Rotate the propellers by hand to confirm at least 15mm clearance from the fuselage and landing pads.
3. **Center of Gravity (CG)**:
   * Balance the aircraft with battery and FPV gear installed.
   * Adjust the battery position on `Battery Plate` until the aircraft balances neutrally without pitching forward or backward.
