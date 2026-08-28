# Emergency Drone Rescue System (DRS) Concept | Mechanical Design & Systems Integration.
---
**Institution:** Ghana-India Kofi Annan Centre for Excellence in ICT, Sunyani.

**Tools:** CAD Modeling (Fusion 360) | Analytical Fluid Dynamics |

**Target Platform:** F450 ArduPilot Quadcopter.

**Date:** 2025

## 1. Context & Motivation.

## Design Requirements & Analytical Sizing

### Performance Parameters
* **Max Takeoff Weight (MTOW):** $2.0\text{ kg}$
* **Max Operating Altitude:** $200\text{ m AGL}$
* **Target Terminal Descent Velocity:** $3.0\text{ m/s}$ to $5.0\text{ m/s}$ (Ensuring structural survival upon ground impact).
* **Deployment Response Time:** $0.3\text{ s} - 0.5\text{ s}$

### Aerodynamic Canoy Sizing
Using standard fluid dynamic drag principles, the required projected surface area ($A$) for a hemispherical canopy design with ($C_d\approx 1.5$) under sea-level atmospheric conditions ($\rho = 1.225\text{ kg/m}^3$) targeting a safe landing velocity of $3\text{ m/s}$ for a $2.0\text{ kg}$ vehicle:

$$A =\frac{2 m g}{\rho \cdot C_d \cdot v^2} = \frac{2 (2.0)(9.81)}{(1.225)(1.5)(3.0)^2} = 2.37\text{ m}^2$$

From the $$A = \pi \cdot r^2$$

$$r = \sqrt\frac{A}{\pi} = \sqrt\frac{2.37}{\pi} = 0.8686\text{ m}$$

$$\implies D = 1.737\text{ m}$$

---

Mechanical Ejection Concept
To achieve clean deployment into undisturbed air within the strict $0.3\text{ s} - 0.5\text{ s}$ ejections window without relying on pyrotechnic charges, a mechanical spring-piston canister mechanism was designed:

* **Ejection Mechanism:** A $150\text{ mm}$ cylindrical canister containing a compression spring ($\sim 12\text{ N}$ force) driving a sliding piston placed plate to eject the canopy at a target velocity of $\sim 2\text{ m/s}$ into clean air outside the propeller wash.
* **Release Latch:** A low-latency MG90S micro-servo controlling a dual-pin rotary restraint arm holding the piston in pre-loaded compression until an emergency trigger signal is received. On receiving trigger signal, the servo rotates the arm to instantly release the piston.
* **Control Architecture:** Concept designed for hybrid activation - primarily autonomous free-fall/altitude threshold via ArduPilot IMU telemetry, with manual transmitter override.

---

## Project Outcome & Engineering Trade-Offs
While the initial 3D modeling and aerodynamic sizing were completed, full physical prototyping was deprioritized due to project timeline constraints and resource re-allocation toward the primary agricultural payload development.

However, the preliminary engineering phase successfully established an analytical blueprint for low-cost UAV recovery, proving that a $2.37\text{ m}^2$ canopy deployed via a simple mechanical spring-servo latch can safely recover a $2.0\text{ kg}$ platform within tight altitude margins.

## Team & Credits
* [Mark Asare](https://www.linkedin.com/in/mark-asare-td/) - *Project Lead & Flight Co-Pilot*
* [Amos Ablorh]() [LinkedIn](https://www.linkedin.com/in/amos-ablorh/) - *Co-Lead for DRS Development (Research, Aerodynamic Sizing, CAD Modeling, System Concept)*
* [Rene Novor](https://github.com/raynayx) [LinkedIn](https://www.linkedin.com/in/raynayx/) - *DRS Development Supervisor (Technical Oversight & Review), Embedded System Integration*
