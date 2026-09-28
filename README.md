# Emergency Drone Rescue System (DRS) Concept

## Mechanical Design, Analytical Sizing & Systems Integration.
---
**Institution:** Ghana-India Kofi Annan Centre for Excellence in ICT, Sunyani.

**Target Platform:** F450 ArduPilot Quadcopter.

**Target MTOW:** $2.0\text{ kg}$

**Tools:** CAD Modeling (Fusion 360) | ArduPilot | Analytical Fluid Dynamics | Embedded System Concepts |

**Date:** 2025

---

## 1. Project Overview.
During operational flight testing of a F450 quadcopter drone for agricultural applications, repeated crash events caused by mid-air instability, complex in-flight manoeuvres, rapid takeoffs and harsh landings, and motor/ESC failures resulted in expensive component repairs and project delays. While off-the shelf commercial recovery systems (e.g. DRS-M210, DRS-300, DRS-15, UAVOS Emergency Rescue System, PARASAFE, etc.) existed, it proved cost-prohibitive for the test vehicle's budget, and spatial integration challenge for our custom F450 frame.

To mitigate hardware loss, the team explored the conceptual design for a **low-cost, lightweight, custom-integrated mechanical deployment emergency Drone Rescue System (DRS)** capable of deploying a recovery parachute at low altitude following an emergency event.


## 2. Design Objectives
* Reduce the likelihood of extensive damage following an inflight emergency.
* Provide rapid deployment of a recovery parachute.
* Operate within the limited space available on an F450 platform.
* Minimise additional mass carried by the UAV.
* Avoid pyrotechnic deployment methods.
* Provide both autonomous and manual activation possibilities.
* Use components and mechanisms that could be fabricated or sourced at low cost.
* Deploy the parachute clear of the propeller wash where practical.


## 3. Design Requirements & Analytical Sizing
### a. Performance Parameters
* **Max Takeoff Weight (MTOW):** $2.0\text{ kg}$ (with provision for future payload scaling);
* **Max Operating Altitude:** $200\text{ m AGL}$
* **Target Terminal Descent Velocity:** $3.0\text{ m/s}$ to $5.0\text{ m/s}$ (Ensuring structural survival upon ground impact).
* **Deployment Response Time:** $0.3\text{ s} - 0.5\text{ s}$

### b. Aerodynamic Canoy Sizing
Using standard fluid dynamic drag principles, the required projected surface area ($A$) for a hemispherical canopy design with ($C_d\approx 1.5$) under sea-level atmospheric conditions ($\rho = 1.225\text{ kg/m}^3$) targeting a safe landing velocity of $3\text{ m/s}$ for a $2.0\text{ kg}$ vehicle:

$$A =\frac{2 m g}{\rho \cdot C_d \cdot v^2} = \frac{2 (2.0)(9.81)}{(1.225)(1.5)(3.0)^2} = 2.37\text{ m}^2$$

From the $$A = \pi \cdot r^2$$

$$r = \sqrt\frac{A}{\pi} = \sqrt\frac{2.37}{\pi} = 0.8686\text{ m}$$

$$\implies D = 1.737\text{ m}$$

### c. Mechanical Ejection Concept
To achieve clean deployment into undisturbed air within the strict $0.3\text{ s} - 0.5\text{ s}$ ejections window without relying on pyrotechnic charges, a mechanical spring-piston canister mechanism was designed:

* **Ejection Mechanism:** A $150\text{ mm}$ cylindrical canister containing a compression spring ($\sim 12\text{ N}$ force) driving a sliding piston placed plate to eject the canopy at a target velocity of $\sim 2\text{ m/s}$ into clean air outside the propeller wash.
* **Release Latch:** A low-latency MG90S micro-servo controlling a dual-pin rotary restraint arm holding the piston in pre-loaded compression until an emergency trigger signal is received. On receiving trigger signal, the servo rotates the arm to instantly release the piston.
* **Control Architecture:** Concept designed for hybrid activation - primarily autonomous free-fall/altitude threshold via ArduPilot IMU telemetry, with manual transmitter override.

---

## Project Outcome
The project established a preliminary engineering design for a lightweight, mechanically deployed UAV recovery system.

The work progressed from identifying the operational problem through preliminary requirement definition, aerodynamic sizing, mechanism selection, spring-powered ejection concept development, release-latch design, component selection, CAD development, and control-integration considerations.

While the initial CAD modeling and aerodynamic sizing were completed, full physical prototyping was deprioritized due to project timeline constraints and resource re-allocation toward the primary agricultural payload development.

However, the preliminary engineering phase successfully provided an analytical basis for a low-cost UAV recovery, suggesting a $2.37\text{ m}^2$ canopy deployed via a simple mechanical spring-servo latch can safely recover a $2.0\text{ kg}$ platform within tight altitude margins.

## Team & Credits
* [Mark Asare](https://www.linkedin.com/in/mark-asare-td/) - *Project Lead & Flight Co-Pilot*
* [Amos Ablorh](https://github.com/Snamosr) [LinkedIn](https://www.linkedin.com/in/amos-ablorh/) - *Co-Lead for DRS Development (Research, Aerodynamic Sizing, CAD Modeling, System Concept)*
* [Rene Novor](https://github.com/raynayx) [LinkedIn](https://www.linkedin.com/in/raynayx/) - *DRS Development Supervisor (Technical Oversight/Review), Embedded System Integration*

---

## **STATUS**
## Conceptual design / analytical development - prototype not completed
This repository documents the engineering development and preliminary calculations behind the proposed system. Numerical results should be interpreted within the assumptions and limitations stated above.
