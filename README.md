# Emergency Drone Rescue System (DRS) - Conceptual Design

## Mechanical Design, Analytical Sizing & Systems Integration.
---
**Institution:** Ghana-India Kofi Annan Centre for Excellence in ICT, Sunyani.

**Target Platform:** F450 ArduPilot Quadcopter.

**Target MTOW:** $2.0\text{ kg}$

**Tools:** CAD Modeling (Fusion 360) | ArduPilot | Analytical Fluid Dynamics | Embedded System Concepts |

**Date:** 2025

---

## 1. Background.
During operational flight testing of a F450 quadcopter drone for agricultural applications, repeated crash events caused by mid-air instability, complex in-flight manoeuvres, rapid takeoffs and harsh landings, and motor/ESC failures resulted in expensive component repairs and project delays. While off-the shelf commercial recovery systems (e.g. DRS-M210, DRS-300, DRS-15, UAVOS Emergency Rescue System, PARASAFE, etc.) existed, it proved cost-prohibitive for the test vehicle's budget, and spatial integration challenge for our custom F450 frame.

To mitigate hardware loss, the team explored the conceptual design for a **low-cost, lightweight, custom-integrated mechanical deployment emergency Drone Rescue System (DRS)** capable of deploying a recovery parachute at low altitude following an emergency event.


## 2. Overview
The Drone Rescue System (DRS) is a conceptual recovery system intended to reduce the impact of a herd landing or loss of control in a small unmanned aerial vehicle (UAV). The concept combines a parachute, a spring-loaded deployment mechanism, and a servo-operated restraint.

This project explores preliminary parachute sizing, mechanical deployment, component selection, and integration with a UAV control concept. Calculations and design choices are intended to provide a basis for further engineering development; they do not establish that the system is safe or flight-ready.

## 3. Design Objectives
* Develop a compact emergency recovery mechanism for a lightweight UAV.
* Investigate rapid deployment of a recovery parachute following an emergency.
* Operate within the limited space available on an F450 platform.
* Minimise additional payload mass and packaging requirements.
* Avoid pyrotechnic deployment methods.
* Investigate both autonomous and manual activation possibilities.
* Use components and mechanisms that could be fabricated or sourced at low cost.
* Deploy the parachute clear of the propeller wash where practical.


## 3. Design Requirements & Analytical Sizing
### a. Preliminary Design Assumptions:
| **Parameter** | **Preliminary target** |
| ----------- | ----------- |
| **Max Takeoff Weight (MTOW)** | $2.0\text{ kg}$ (with provision for future payload scaling) |
| **Max Operating Altitude** | $200\text{ m AGL}$ |
| **Target Terminal Descent Velocity** | $3.0\text{ m/s} - 5.0\text{ m/s}$ (Ensuring structural survival upon ground impact) |
| **Target Deployment Response Time** | $0.3\text{ s} - 0.5\text{ s}$ |
| Target piston ejection velocity |  $\approx 2\text{ m/s}$ |
| Canister length | $150\text{ mm}$ |
| Canister diameter | $65\text{ mm}$ |
| Assumed piston + parachute mass | $\sim\ 0.3\text{ kg}$ |
| Assumed piston travel | $40\text{ mm}$

*The values provided in the table represent initial design targets and assumptions.*

### b. Parachute Canopy Sizing
Using standard fluid dynamic drag principles, the required projected surface area ($A$) for a hemispherical canopy design with ($C_d\approx 1.5$) under sea-level atmospheric conditions ($\rho = 1.225\text{ kg/m}^3$) targeting a safe landing velocity of $3\text{ m/s}$ for a $2.0\text{ kg}$ vehicle:

$$A =\frac{2 m g}{\rho \cdot C_d \cdot v^2}$$

$$A = \frac{2 (2.0)(9.81)}{(1.225)(1.5)(3.0)^2}$$

$$A = 2.37\text{ m}^2$$

Assume a circular projected area [ $$A = \pi \cdot r^2$$ ] gives;

$$r = \sqrt\frac{A}{\pi}$$
$$= \sqrt\frac{2.37}{\pi}$$
$$= 0.8686\text{ m}$$

$$\implies D = 1.737\text{ m}$$

The calculation produced a required projected area of approximately $2.37\ \text{m}^2$, corresponding to an equivalent circular diameter of approximately $1.74\ \text{m}$. This provided an initial basis for evaluating the canopy packaging and development mechanism.

**Limitations:** The calculation assumes steady descent and a constant drag coefficient. Actual performance depends on canopy geometry, inflation dynamics, porosity, suspension-line arrangement, vehicle attitude and atmospheric conditions. The calculated area is a preliminary sizing estimate, not evidence that the selected canopy would achieve the target descent velocity.

## 4. Deployment Mechanism Selection
A major design challenge was deploying the folded canopy rapidly enough while keeping the mechanism compact and avoiding interference with the propellers. The table below highlights several deployment concepts considered during the design process:

| **Concept** | **Advantages considered** | **Limitations considered** |
| --- | --- | --- |
| Spring-loaded deployment | Rapid ejection; Low electrical demand during release; Resettable | Requires a reliable restraint and suitable spring sizing |
| Servo-operated hatch or release | Direct control; Relatively simple; Actuation | Release alone may not provide sufficient positive canopy ejection |
Slingshot-style mechanism | Potentially rapid ejection | More complex geometry, restraint and reset arrangements |
| Spring-servo hybrid | Separates energy storage from release control; Resettable | Requires coordination between spring, piston and latch |
| $\text{CO}_2$ cartridge | Potentially rapid; Forceful deployment | Cartridge availability, pressure-system complexity; and Consumable cost |
| Pyrotechnic deployment | Compact and rapid in specialized systems | Safety; Regulatory; Handling; and Reusability concerns |
| Gravity-assisted deployment | Simple and mechanically minimal | Strong dependence on orientation and surrounding airflow | 

The spring-servo hybrid concept was selected for further development. The rationale was to use a compression spring to supply the ejection energy while a small servo operated the mechanical restraint. This avoided relying on the servo to provide the entire deployment force and offered the possibility of resetting the mechanism after deployment.

***NB:** The concept was selected on engineering grounds, but its relative speed, reliability and deployment effectiveness were not experimentally compared with the alternatives.*

## 5. Spring-Piston Ejection Mechanism
### a. Concept Description
The proposed development assembly will consist of:
* A cylindrical canister
* A circular sliding piston
* A compression-spring arrangement
* A folded parachute stored above the piston
* A mechanical restraint and release mechanism
* A servo actuator

The spring-loaded piston is restrained before activation. When the release mechanism disengages, the spring expands and drives the piston upward, ejecting the folded canopy from the canister.

The preliminary packaging dimensions were approximately **$15O\ \text{mm}$ in length** and **$65\ \text{mm}$ in diameter**

### b. Preliminary spring-force calculation
The design aimed for an acceleration magnitude of approximately *three times* the gravitational acceleration:

$$a_{\text{target}} = 3\text{g} = 29.43\ \text{m/s}^2$$

$$\approx 30\ \text{m/s}^2$$

Assuming a combined moving mass of the piston and parachute to be $\text{m} = 0.3\ \text{kg}$; for an upward-moving assembly, the approximated spring force required at the start of motion is:

$$\text{F} = m (g+a)$$

where $\text{a} = a_\text{target} = 30\ \text{m/s}^2$

$$\implies F = 0.30 \times (9.81 + 30)$$

$$\therefore\ F = 11.943\ \text{N}$$
$$\approx 12\ \text{N}$$

The $12\ \text{N}$ calculated spring force represents the initial force estimate. It does not cover the net acceleration throughout the stroke, as spring force decreases with compression spring extension.

### c. Spring stiffness
From Hooke's Law;

$$ F = kx $$

For a spring force of $11.943\ \text{N}$, assuming a spring compression of $40\ \text{mm}$ ($0.04\ \text{m}$)

$$ k = \frac{11.943}{0.04}$$
$$ k\ \boxed{\approx\ 298.6\ \text{N/m}}$$


### d. Multi-spring Arrangement Consideration
After further design consideration, a four smaller compression springs configuration arranged in a circular layout was chosen. Reasons include:
* The flexibility in sourcing suitable springs;
* Piston load will be distributed equally across the springs;
* High likelihood of reduction in tilting;
* Better choice for the selected canister cross-section.
  
The total initial force of $12\ \text{N}$ would now correspond to $\approx4\ \text{N}$, and a nominal stiffness of $\approx75\ \text{N/m}$ per spring.

## 6. Piston and Canister Design
The piston was considered as a circular plate fitted inside a canister with preliminary dimensions as follows"
* Canister length: approximately $150\ \text{mm}$
* Canister diameter: approximately $65\ \text{mm}$
* Piston configuration: circular plate with sufficient radial clearance for sliding.
* Parchute location: storage bay above the piston.
* Spring arrangement: $4-\text{spring}$ configuration in a circular layout.

The piston was intended to transmit the spring force to the folded canopy while maintaining reasonably aligned motion inside the canister. The clearance would need to balance low friction against execessive lateral movement or tiltling. Actual clearance, piston dimensions, surface finish and binding resistance remain to be established throgh detailed design and prototype testing.

***NB:*** Canopy folding, packing density, extraction force and inflation clearance would therefore need to be evaluated before finalizing the canister dimensions.

### Material Consideration
The table below highlights the provisional material choices for the proposed concept:
| Component | Material | Consideration |
| --- | --- | --- |
| Canister housing | PLA, ABS, or Lightweight aluminum | Weight, stiffness and manufacturability |
| Piston | PLA or ABS | Mass, dimensional accuracy and sliding friction |
| Compression springs | Steel | Stiffness, working travel and durability |
| Parchute | Nylon (provisional) | Strength, folding and deployment behaviour |



## 7. Mechanical Ejection Concept
To achieve clean deployment into undisturbed air within the strict $0.3\text{ s} - 0.5\text{ s}$ ejections window without relying on pyrotechnic charges, a mechanical spring-piston canister mechanism was designed:

* **Ejection Mechanism:** A $150\text{ mm}$ cylindrical canister containing a compression spring ($\sim 12\text{ N}$ force) driving a sliding piston placed plate to eject the canopy at a target velocity of $\sim 2\text{ m/s}$ into clean air outside the propeller wash.
* **Release Latch:** A low-latency MG90S micro-servo controlling a dual-pin rotary restraint arm holding the piston in pre-loaded compression until an emergency trigger signal is received. On receiving trigger signal, the servo rotates the arm to instantly release the piston.
* **Control Architecture:** Concept designed for hybrid activation - primarily autonomous free-fall/altitude threshold via ArduPilot IMU telemetry, with manual transmitter override.

---

## Project Outcome
The project established a preliminary engineering design for a lightweight, mechanically deployed UAV recovery system.

The work progressed from identifying the operational problem through preliminary requirement definition, analytical canopy sizing, comparison of deployment concepts, mechanism selection, spring-force estimation, release-latch design, component selection, CAD development, and control-integration considerations.

While the initial CAD modeling and aerodynamic canopy sizing were completed, full physical prototyping was deprioritized due to project timeline constraints and resource re-allocation toward the primary agricultural payload development. Nevertheless, it established a basis for further mechanical design, component selection and experimental development.


## Team & Credits
* [Mark Asare](https://www.linkedin.com/in/mark-asare-td/) - *Project Lead & Flight Co-Pilot*
* [Amos Ablorh](https://github.com/Snamosr) [LinkedIn](https://www.linkedin.com/in/amos-ablorh/) - *Co-Lead for DRS Development (Research, Aerodynamic Sizing, CAD Modeling, System Concept)*
* [Rene Novor](https://github.com/raynayx) [LinkedIn](https://www.linkedin.com/in/raynayx/) - *DRS Development Supervisor (Technical Oversight/Review), Embedded System Integration*

---

## **STATUS**
## Conceptual design and preliminary analytical development - prototype not completed
This repository documents the design rationale, preliminary calculations, assumptions, and unresolved engineering tasks associated with the proposed Drone Rescue System. It is intended as a technical design record and basis for future development, not as evidence of a flight-qualified recovery system. 

Numerical results should be interpreted within the assumptions and limitations stated above.
