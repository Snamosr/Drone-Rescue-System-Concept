# Emergency Drone Rescue System (DRS) - Conceptual Design

## Mechanical Design, Analytical Sizing & Systems Integration.

**Institution:** Ghana-India Kofi Annan Centre for Excellence in ICT, Sunyani.\
**Target Platform:** F450 ArduPilot Quadcopter.\
**Target MTOW:** $2.0\text{ kg}$\
**Tools:** CAD Modeling (Fusion 360) || ArduPilot || Analytical Fluid Dynamics || Embedded System Concepts ||\
**Date:** 2025

---
## **STATUS**
### Conceptual design and preliminary analytical development - Physical prototype not completed
This repository documents the design rationale, preliminary calculations, assumptions, and unresolved engineering tasks associated with the proposed Drone Rescue System. It is intended as a technical design record and basis for future development, not as evidence of a flight-qualified recovery system. 

*Numerical results should be interpreted within the assumptions and limitations stated below.*

---

## 1. Background.
During operational flight testing of a F450 quadcopter drone for agricultural applications, repeated crash events caused by mid-air instability, complex in-flight manoeuvres, rapid takeoffs and harsh landings, and motor/ESC failures resulted in expensive component repairs and project delays. While off-the shelf commercial recovery systems (e.g. DRS-M210, DRS-300, DRS-15, UAVOS Emergency Rescue System, PARASAFE, etc.) existed, it proved cost-prohibitive for the test vehicle's budget, and spatial integration challenge for our custom F450 frame.

To mitigate hardware loss, the team explored the conceptual design for a **low-cost, lightweight, custom-integrated mechanical deployment emergency Drone Rescue System (DRS)** capable of deploying a recovery parachute at low altitude following an emergency event.

---
## 2. Overview
The Drone Rescue System (DRS) is a conceptual recovery system intended to reduce the impact of a herd landing or loss of control in a small unmanned aerial vehicle (UAV). The concept combines a parachute, a spring-loaded deployment mechanism, and a servo-operated restraint.

This project explores preliminary parachute sizing, mechanical deployment, component selection, and integration with a UAV control concept. Calculations and design choices are intended to provide a basis for further engineering development; they do not establish that the system is safe or flight-ready.

---
## 3. Design Objectives
* Develop a compact emergency recovery mechanism for a lightweight UAV;
* Investigate rapid deployment of a recovery parachute following an emergency;
* Operate within the limited space available on an F450 platform;
* Minimise additional payload mass and packaging requirements;
* Avoid pyrotechnic deployment methods;
* Investigate both autonomous and manual activation possibilities;
* Use components and mechanisms that could be fabricated or sourced at low cost;
* Deploy the parachute clear of the propeller wash where practical.

---
## 4. Design Requirements & Analytical Sizing
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

---
## 5. Deployment Mechanism Selection
A major design challenge was deploying the folded canopy rapidly yet slow enough to catch wind while keeping the mechanism compact and avoiding interference with the propellers. The table below highlights several deployment concepts considered during the design process:

| **Concept** | **Advantages considered** | **Limitations considered** |
| --- | --- | --- |
| Spring-loaded ejection | Rapid ejection; Low electrical demand during release; Resettable | Requires a reliable restraint and suitable spring sizing |
| Servo-operated hatch or release | Direct control; Relatively simple; Actuation | Release alone may not provide sufficient ejection force |
Slingshot-style mechanism | Potentially rapid ejection | More complex geometry, restraint and reset arrangements |
| Spring-servo hybrid | Separates energy storage from release control; Resettable | Requires coordination between spring, piston and latch |
| $\text{CO}_2$ cartridge | Potentially rapid; Forceful deployment | Cartridge availability, pressure-system complexity; and Consumable cost |
| Pyrotechnic deployment | Compact and rapid in specialized systems | Safety; Regulatory; Handling; and Reusability concerns |
| Gravity-assisted deployment | Simple and mechanically minimal | Strong dependence on orientation and surrounding airflow | 

The spring-servo hybrid concept was selected for further development. The rationale was to use a compression spring to supply the ejection energy while a small servo operated the mechanical restraint. This avoided relying on the servo to provide the entire deployment force and offered the possibility of resetting the mechanism after deployment.

***NB:** The concept was selected on engineering grounds, but its relative speed, reliability and deployment effectiveness were not experimentally compared with the alternatives.*

---
## 6. Spring-Piston Ejection Mechanism
### a. Concept Description
The proposed development assembly will consist of:
* A cylindrical canister;
* A circular sliding piston (custom component);
* A compression-spring arrangement;
* A folded parachute/canopy stored above the piston;
* A mechanical restraint and release mechanism;
* A servo actuator ($\text{MG90S micro servo}$).

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
$$ k = 298.575\ \text{N/m}$$

$$ \boxed{\approx\ 300\ \text{N/m}}$$


### d. Multi-spring Arrangement Consideration
After further design consideration, a four smaller compression springs configuration arranged in a circular layout was chosen. Reasons include:
* The flexibility in sourcing suitable springs;
* Piston load will be distributed equally across the springs;
* High likelihood of reduction in tilting;
* Better choice for the selected canister cross-section.
  
The total initial force of $12\ \text{N}$ would now correspond to $\approx4\ \text{N}$, and a nominal stiffness of $\approx75\ \text{N/m}$ per spring.

---
## 7. Piston and Canister Design
### a. Conceptual Design Description
The piston was considered as a circular plate fitted inside a canister. The objective was to produce a compact mechanism that could be integrated into the UAV without significantly interfering with the existing flight hardware. The conceptual design has dimensions as follows;"
* Canister length: approximately $150\ \text{mm}$;
* Canister diameter: approximately $65\ \text{mm}$;
* Piston configuration: circular plate with sufficient radial clearance for sliding;
* Parchute location: storage bay above the piston;
* Spring arrangement: $4-\text{spring}$ configuration in a circular layout.

The piston was intended to transmit the spring force to the folded canopy while maintaining reasonably aligned motion inside the canister. The clearance would need to balance low friction against execessive lateral movement or tiltling. Actual clearance, piston dimensions, surface finish and binding resistance remain to be established throgh detailed design and prototype testing.


### b. Parachute packing
The canopy's estimated projected area was approximately $2.37\ \text{m}^2$. A separate preliminary packing-volume estimate was considered during concept development.

However, the original packing-volume ratio requires verification of its units and reference basis before a defensible packed volume can be calculated. The available information does not establish that the folded canopy would fit inside the proposed canister.

***NB:*** Canopy folding, packing density, extraction force and inflation clearance would therefore need to be evaluated before finalizing the canister dimensions.

---
## 8. Servo-Operated Restraint
### a. Release Mechanism operating principle
The concept uses a $\text{MG90S metal-gear micro-servo}$ with a dual-arm restraint arrangement. The two servo-operated arms retains the piston against the spring force until deployment is initiated. This proposed arrangement ensures that the piston is restrained at both cut-outs on the piston legs.

### Operating sequence
1. Spring and piston are preloaded.
2. The latch restrains the piston.
3. The servo remains in the locked position during normal flight.
4. An emergency trigger is recieved.
5. The servo arm rotates $90\deg$ out of the cut-out to disengage the restraint.
6. The compressed spring accelerates the piston.
7. The piston ejects the folded canopy.
8. The canopy moves into the surrounding airflow and begins deployment.

*The servo therefore functions primarily as a release actuator, rather than as the source of deployment energy.*

### b. Torque Estimation
The preliminary torque estimates can be made by assuming a $12\ \text{N}$ load acting at a $10 \text{mm}$ ($0.01 \text{m}$) moment arm:

$$ T = F\times\ r$$

$$ = 12 \times\(0.01)$$

$$\implies\ T = 0.12\ \text{N.m}$$

$$ \approx\ 1.22\ \text{kgf.cm}$$

***NB:** The calculation does not establish the actual servo torque required to release the proposed restraint arrangement. The actual torque required depends on the contact forces, friction, alignment, and how the spring load is transferred through the restraint. A mechanism that will carry the spring load without continuously loading the servo may be preferable.*

---
## 9. Material Consideration
The table below highlights the provisional material choices for the proposed concept:
| Component | Material | Consideration |
| --- | --- | --- |
| Canister housing | PLA, ABS, or Lightweight aluminum | Weight, stiffness and manufacturability, and durability |
| Piston | PLA or ABS for initial concept development | Mass, dimensional accuracy and sliding friction |
| Compression springs | Steel | Force-deflection characteristics, fatigue, working travel and durability |
| Parachute | Nylon (provisional) | Strength, mass, folding and deployment behaviour |
| Actuator | MG90S metal-geared servo | Torque margin, geometry, power supply, repeatability |
| Control electronics | UAV controller (integrated with a deployment interface) | Trigger logic, power integrity, and fail-safe behaviour |

*Final selection may require component specifications, dimensional checks, and verificaiton against the operating loads.*

---
## 10. Activation and Control Concept
### a. Activation and Control
The proposed control concept would initiate recovery when a defined abnormal flight condition is detected or when a manual deployment is initiated.

Further development must define:
* The conditions that trigger deployment and how false triggers are prevented;
* The electrical and mechanical sequence for releasing the restraint.;
* The controller-to-servo interface and power requirements;
* Behaviour during loss of control power, communication, or sensor input;
* Ground-safety procedures, arming logic, and a method to prevent unintended deployment.

In **autonomous activation**, the ArduPilot flight controller will monitor relevant flight-state information and issue a deployment command when predefined emergency conditions are detected. Possible inputs include altitude, inertial measurement data, flight mode and abnormal descent behaviour.

For **manual activation**, the operator can initiate deployment in an emergency not captured by the autonomous trigger logic.

The control architecture remains conceptual. Autonomous triggering, manual override and servo actuation were not implemented and validated as a complete system.


### b. UAV Integration considerations
The proposed DRS was intended for an F450-class quadcopter.Integration would require consideration of the canister's mounting position, centre-of-gravity effects, structural attachment and vibration, parachute line routing, propeller clearance, possibility of canopy entanglement, electrical supply and servo control, and access for servicing and resetting the mechanism.

Deployment directions is particularly important because the canopy must clear the aircraft and inflate without becoming entangled in the frame or propellers.

The available altitude and time of recovery must also be assessed against the complete sequence: fault detection, command processing, restraint release, canopy extraction, inflation, and deceleration.

The proposed operation altitude and deployment-response targets are not evidence that recovery can be achieved within those limits.

---
## 11. Limitations and Validation Status
This project remained at the conceptual and preliminary analytical stage.

The following activities were not completed:
* Physical prototype fabrication;
* Verification of spring force and stiffness against a purchased component;
* Bench testing of the loaded restraint mechanism;
* Measurement of piston accelertion or ejection velocity;
* Verification of parachute packing and extraction;
* Canopy inflation and descent testing;
* Validation of servo torque under actual release conditions;
* Integration and testing of emergency-trigger logic;
* Ground and fight testing of the complete recovery system;
* Full structural and operational verification.

Consequently, the numerical values presented in this repository are design assumptions, analytical estimates or targets, as identified in the relevant sections. The Should not be interpreted as measured deployment performance or proof of safe recovery.


---

## Project Outcome
The project established a preliminary engineering design for a lightweight, mechanically deployed UAV recovery system.

The work progressed from identifying the operational problem through preliminary requirement definition, analytical sizing calculations, comparison of deployment concepts, mechanism selection, spring-force estimation, release mechanism design, component selection, CAD development, and control-integration considerations.

While the initial CAD modeling and analytical sizing calculations were completed, full physical prototyping was deprioritized due to project timeline constraints and resource re-allocation toward the primary agricultural payload development. Nevertheless, it established a basis for further mechanical design, component selection and experimental development.


## Team & Credits
* [Mark Asare](https://www.linkedin.com/in/mark-asare-td/) - *Project Lead & Flight Co-Pilot*
* [Amos Ablorh](https://github.com/Snamosr) [LinkedIn](https://www.linkedin.com/in/amos-ablorh/) - *Co-Lead for DRS Development (Research, Aerodynamic Sizing, CAD Modeling, System Concept)*
* [Rene Novor](https://github.com/raynayx) [LinkedIn](https://www.linkedin.com/in/raynayx/) - *DRS Development Supervisor (Technical Oversight/Review), Embedded System Integration*

---



***‼️‼️ NO PHYSICAL PROTOTYPE OR FLIGHT VALIDATION IS CLAIMED ‼️‼️***
