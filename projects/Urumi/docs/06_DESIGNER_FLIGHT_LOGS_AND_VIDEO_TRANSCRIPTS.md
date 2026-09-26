# 🎬 Designer Flight Logs, Video Transcripts & Development History

> **Project Source**: Designed by Olivier (*RCGroups: ["Rifter, Sabre, Scimitar mini-sized FPV cruisers"](https://www.rcgroups.com/forums/showthread.php?4223695-Rifter-Sabre-Scimitar-mini-sized-FPV-cruisers)*).  
> This document integrates the complete development history, technical insights, crash investigations, and video transcripts across the official 3-part YouTube video series.

---

## 📺 Official Video Series Reference

| Video Part | Title | Link | Key Milestones & Topics |
| :--- | :--- | :--- | :--- |
| **Part 1** | *Urumi, Quad/Interceptor/X-Wing 1* | [Watch on YouTube](https://www.youtube.com/watch?v=R3-GTveqTRI) | Prototype introduction, 22° wing dihedral design, removable wing mechanism, initial hover, first transition onto wings (70–80 km/h), first crash landing. |
| **Part 2** | *Urumi, Quad/Interceptor/X-Wing 2* | [Watch on YouTube](https://www.youtube.com/watch?v=sHy94xdoC1A&t=772s) | Second crash investigation (FC IMU thermal failure), redesigning to the final CAD release (wider landing pads, air intakes, VTX bay), F722 stack upgrade, INAV radar formation flight. |
| **Part 3** | *Urumi, Quad/Interceptor/X-Wing 3* | [Watch on YouTube](https://www.youtube.com/watch?v=J87EU8D0PFA) | Final flight tests with DakeFPV F722 stack, extreme wind sensitivity (5–6 km/h limit), honest pilot handling evaluation. |

---

## 1. Part 1: Conception, First Flights & Transition Test

### 1.1 Aerodynamic & Structural Architecture
* **Hybrid Concept**: The aircraft can be viewed as an aeroplane with unusually small wings and four propulsion motors, or as a quadcopter whose wings generate aerodynamic lift once forward airspeed is reached.
* **Wing Dihedral (22° Angle)**: The 22° dihedral was calculated precisely to allow clearance for 7-inch propellers while keeping the propeller thrust discs as horizontal as possible to preserve vertical hover efficiency.
* **Effective Wing Area**: Four wings measuring 20 × 20 cm each provide a total area equivalent to a single 80 × 20 cm wing.
* **Modular Glueless Wings**: In the very first prototype, the wings were glued to the fuselage. The designer subsequently redesigned the fuselage so the wings slide freely over the 6.0mm carbon spars and are locked by the motor mounts (`Wing lock`). This allows rapid replacement or testing of longer wing extensions.
* **Materials**: Airframe 3D-printed in PLA+ (ePLA-ST) assembled with cyanoacrylate (CA) and spray accelerator. Hollow 6mm carbon fiber tubes form the central X-frame.
* **Tilting FPV Camera**: Servo-actuated mount compatible with the DJI O3 and DJI O4 video systems.

### 1.2 Initial Flight & Hover Test
* Tested in breezy conditions. Despite small 6-inch test propellers and older 2206 motors, the aircraft hovered stably.
* **Passive Weathercock Stability**: The large rear fuselage acts as a weather vane, automatically turning the nose into the wind.

### 1.3 The First Transition & Wing-Borne Flight
* Operating on a standard quadcopter mixer, forward pitch was applied. To the team's delight, the aircraft accelerated and transitioned onto its wings at approximately **70–80 km/h** without requiring an excessive angle of attack.
* **Flight Controls**:
  * Turning with roll alone is inefficient due to lack of ailerons; the aircraft makes very wide turns.
  * **Coordinated yaw + roll** produces effective, tighter turns.
  * **Flat yaw turns**: Using yaw alone creates differential thrust across the left and right motors, rotating the aircraft around its vertical axis with zero bank angle (like a high-speed camera drone).

### 1.4 The Landing Crash (Disorientation Incident)
* **What Happened**: At the end of the second flight, the pilot believed the camera was tilted to 45°, when it was actually pointing straight forward at 0°. Misjudging the aircraft's true attitude, the pilot entered a steep dive in Acro mode, expecting to pull out near the ground.
* **Root Cause**: The hybrid aircraft's mass and wing drag do not respond with the instantaneous snap-recovery of a lightweight racing quad. The aircraft struck the rocky ground nose-first.
* **Damage**: Minor structural damage; the wings survived because they were removable.

---

## 2. Part 2: Crash Investigation, Evolution to Final CAD Release & Radar Cruise

### 2.1 The Second Crash: Flight Controller IMU Failure
During subsequent testing, a second crash occurred:
> *"Second plane broken because of this faulty flight controller. Maybe IMU issue, overheats or whatever and dies. Works at take off, then fails after a few minutes."*

### 2.2 Transition to F722 Stack & 4-in-1 ESC
In the initial prototype, the designer used 4 separate ESCs and an intermediate Power Distribution Board (PDB), which created a tangled nest of cables inside the fuselage.  
* **Upgrade**: The designer switched to an **F722 flight controller stack with a 4-in-1 ESC**, greatly simplifying internal wiring, reducing weight, and eliminating the cable clutter.

### 2.3 Airframe Modifications in the Final CAD Release
The designer incorporated several critical design improvements into the final files published on RCGroups (which match the files in this repository):
1. **Wider Landing Pads (`Pad 1, 2, 3, 4`)**: All 4 pads are now asymmetrical, widening the stance so the aircraft does not tip over when settling vertically onto uneven grass or gravel.
2. **Integrated Cooling Air Intakes**: Openings added to the fuselage nose to channel airflow directly over the ESC, FC, and VTX.
3. **Internal Plate Optimization**: Repositioned `FC Plate` and `Battery Plate` to create a dedicated compartment for the DJI O3 / O4 video transmitter.

### 2.4 Formation Flying with INAV Radar & Cruise Efficiency
* In Video 2, the designer performs dusk formation flights with a wingmate using the **INAV Radar** feature on their OSD.
* **Cruise Consumption**: In level forward flight, the aircraft draws only **~8 Amps** at cruising speed.
* **Efficiency**: Approximately **60 mAh per kilometer** on a 4S/5S LiPo battery, allowing ~15 minutes of forward flight on a 2200mAh pack.

---

## 3. Part 3: Final Flight Tests with DakeFPV F722 & Handling Limits

### 3.1 Flight Controller Replacement
* The designer installed a budget **DakeFPV F722** stack from AliExpress. In flight testing, the new board performed reliably with zero sensor lockups or overheating issues.

### 3.2 Environmental Limits: Extreme Wind Sensitivity
> ⚠️ *"If there is one thing this aircraft hates, it is wind. 5 to 6 km/h of wind is already too much—it completely disturbs it."*
* **Why**: The high surface area of the fuselage, four angled wings, and large vertical fin make hovering in wind turbulent. Ground turbulence near trees causes erratic drift. Always maiden and fly Urumi in calm or light-breeze conditions.

### 3.3 Honest Handling Summary from the Designer
Olivier provided an entertaining yet candid evaluation of the aircraft's dual nature:
> *"It's the worst quad in my fleet, and it's also the worst airplane! It's the combination of the two: a bad quad with a bad plane. It can do both. Landing it is not fun at all; however, launching and taking off is super fun! The rest is tricky, but I haven't finished the tuning yet..."*

---

## 4. Key Takeaways & Actionable Lessons for Builders

1. **Electronics Stack**: Use a modern **F722 or F405 flight controller with a 4-in-1 ESC** (rather than individual ESCs) to keep the fuselage clean and avoid IMU overheating.
2. **Attitude Awareness**: Set up your FPV OSD to clearly display:
   * Current Mixer Profile (`PROF 1` / `PROF 2`)
   * Camera tilt angle
   * Artificial horizon line
3. **Landing Discipline**: Never attempt a forward Acro descent. Always switch to **Position 2** (45° camera) to bleed off speed, then switch to **Position 1** (90° camera, Quad-X mode) and land vertically like a multirotor.
4. **Weather Condition**: Only fly in calm weather (<6 km/h wind).
5. **Turns**: Always coordinate your sticks (**Roll + Yaw together**) in forward flight.
