# ✈️ INAV Hybrid VTOL Flight Manual & Tuning Guide

> **Flight Characteristics Reference**: Derived from real prototype flight logs and crash incident analysis ([`06_DESIGNER_FLIGHT_LOGS_AND_VIDEO_TRANSCRIPTS.md`](06_DESIGNER_FLIGHT_LOGS_AND_VIDEO_TRANSCRIPTS.md)).

---

## 1. Principles of Operation

Urumi is an unconventional hybrid aircraft:
* **In Hover**: It functions as an agile Quad-X multirotor, taking off and landing vertically.
* **In Forward Flight**: It tilts 90° forward onto its four 22° dihedral wings. Once the aircraft reaches approximately **70–80 km/h**, the wings generate enough aerodynamic lift to support the entire vehicle.
* **No Control Surfaces**: Unlike conventional aeroplanes, Urumi has **no ailerons, no elevators, and no rudder**. Attitude, banking, pitching, and yawing in forward flight are produced entirely through **differential motor thrust**.

```
Hover Mode (Quad-X)               Transition Phase                Forward Wing Flight
   [Motors ↑ Thrust]            [Pitch Forward ~45°]              [Wings Generate Lift]
   Camera @ 90°                  Camera @ 45°                      Camera @ 0°
   Takeoff & Landing             Accelerate to 70-80 km/h          High Speed Cruise
```

---

## 2. INAV Dual-Mixer Configuration

INAV supports two independent mixer profiles, which allows switching between multirotor and forward-flight handling on a single switch.

### 2.1 Critical Installation Requirement
> ⚠️ **Important**: The flight controller must be installed flat in the **conventional aeroplane orientation**, with the FC arrow pointing toward the front nose of the aircraft.
> The multirotor mixer then applies a software orientation offset (90° pitch rotation). If the FC is physically installed in multirotor orientation, the forward-flight mixer and horizon level calculations will fail.

---

### 2.2 The Two Mixer Profiles

#### Mixer Profile 2: Vertical / Multirotor Mode (Hover)
* **Configuration**: Standard Quad-X multirotor mixer.
* **Camera Servo**: Commanded to approximately **90° down** relative to the fuselage (which points straight at the natural ground horizon during vertical hover).
* **Used for**:
  * Vertical take-off
  * Low-speed manoeuvring
  * Stationary hovering
  * Vertical spot landings

#### Mixer Profile 1: Forward-Flight Mode (Aeroplane)
* **Configuration**: Custom differential-thrust aeroplane mixer.
* **Axis Swapping**:
  * In forward flight, what was previously multirotor **Roll** becomes aerodynamic **Yaw** (differential thrust between left and right wing pairs).
  * What was previously multirotor **Yaw** becomes aerodynamic **Roll**.
* **Camera Servo**: Commanded to **0° (pointing straight out the nose)**.
* **Used for**: High-speed, efficient winged cruising.

---

## 3. 3-Position Flight-Mode Switch Setup

Assign a 3-position switch on your RC transmitter (e.g. Channel 8 / Aux 4):

| Switch Position | Active Mixer Profile | Camera Tilt Angle | Flight Phase & Pilot Instructions |
| :---: | :---: | :---: | :--- |
| **Position 1 (High)** | **Mixer Profile 2** (Multirotor) | **90°** (Hover View) | **Vertical Take-off & Hover**: Aircraft stands vertically. Take off like a normal quadcopter. |
| **Position 2 (Mid)** | **Mixer Profile 2** (Multirotor) | **45°** (Intermediate) | **Acceleration & Transition**: The aircraft remains under quadcopter control, but the camera tilts to 45°. Push the pitch stick forward to build airspeed to 70–80 km/h while maintaining clear horizon sight. |
| **Position 3 (Low)** | **Mixer Profile 1** (Wing Mode) | **0°** (Forward View) | **Forward Aeroplane Flight**: Switch active. Wings produce lift; fly using combined roll and yaw differential thrust. |

---

## 4. Piloting Dynamics & Handling Insights

### 4.1 Roll Authority & Coordinated Turns
Because Urumi has no physical ailerons, rolling with the roll stick alone produces a very wide, sluggish turning radius.
* **Always fly coordinated turns**: Combine roll and yaw stick inputs simultaneously. This commands differential thrust across the four motor nacelles to carve crisp, tight turns.

### 4.2 Flat Yaw Turns
One of Urumi’s most distinctive manoeuvres is a **flat yaw turn**:
* In forward flight, applying yaw alone causes the left or right motor pairs to change speed, rotating the aircraft around its vertical axis with virtually zero bank angle.
* This produces a stable, pan-camera effect similar to a gimbal-stabilized camera drone flying at high speed.

### 4.3 Passive Weathercock Stability
The large rear fuselage and vertical fin profile act like a weather vane in windy conditions. The aircraft naturally tends to align its nose into the wind, aiding heading stability during hover.

---

## 5. Landing Procedure & Crash Prevention (Lessons Learned)

In initial flight testing, an accidental crash occurred due to pilot disorientation:
> *"The pilot believed the camera was tilted to 45°, when it was actually at 0°. Misjudging the aircraft's attitude, the pilot entered a steep descent in Acro mode, expecting the plane to recover like a lightweight racing drone. The mass, drag, and wing aerodynamics delayed the pull-out, resulting in a nose-first impact."*

### Safe Recovery & Landing Protocol:
1. **Never attempt to land in forward-flight Acro mode.**
2. **Step 1 (Deceleration)**: Flip the 3-position switch from **Position 3** back to **Position 2** (Camera moves to 45°, quadcopter mixer engages). Pull back gently on pitch to bleed off forward speed.
3. **Step 2 (Establish Hover)**: Once forward airspeed drops below 30 km/h, flip the switch to **Position 1** (Camera moves to 90° hover view). The aircraft will settle into a stable vertical hover.
4. **Step 3 (Vertical Touchdown)**: Descend smoothly like a quadcopter onto its 4 landing pads.
5. **OSD Safety Indicators**: Ensure your FPV On-Screen Display (OSD) shows:
   * Current Mixer Profile (`PROF 1` / `PROF 2`)
   * Camera tilt angle indicator
   * Artificial horizon / attitude ladder
   * GPS Groundspeed and Altitude
