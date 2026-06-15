# Pellet DispensoMixer V2

Developed at IMDEA Materials Institute.

<p align="center">
  <img src="Images/Image%201.png" alt="Pellet DispensoMixer V2 Assembly" width="750">
</p>

## Project Overview

The Pellet DispensoMixer V2 is an updated and improved version of the original Pellet DispensoMixer developed at IMDEA. The main objective of this redesign was to increase system reliability, simplify assembly and maintenance procedures, and improve the overall integration of the platform.

The new version replaces the previous actuation system with NEMA 17 stepper motors and consolidates the electronic architecture into a single control board, reducing wiring complexity and improving maintainability.

This repository contains the complete design package generated during the development of the project, including CAD models, manufacturing files, electrical schematics, and supporting documentation.

## Key Features

- NEMA 17 stepper motor actuation.
- Single integrated control PCB: BIGTREETECH Octopus V1.1
- Modular and maintainable mechanical architecture.
- Complete CAD documentation.
- Manufacturing-ready 3D models.
- Electrical schematics and wiring documentation.
- Improved assembly workflow.
- Open and editable design files.

## Improvements Over the Original Pellet DispensoMixer

This project represents a significant redesign of the original Pellet DispensoMixer platform.

| Feature | Original Version | V2 |
|---|---|---|
| Actuation System | 28BYJ-48 unipolar geared stepper motor | NEMA 17 stepper motors |
| Electronics | 8x Arduino UNO | Single integrated PCB |
| Assembly | More complex integration | Tool-free cascade assembly with vertically stacked components and sequential insertion |
| Reliability | Baseline performance | Improved robustness |


## Bill of Materials

| Component | Quantity |
|---|---|
| NEMA 17 Stepper Motor | 8 |
| A4988 Stepper Motor Driver | 8 |
| BTT Octopus Pro Main Control Board | 1 |
| Power Supply | 1 |
| 3D Printed Components |  |
| Feed Ramp | 8 |
| Module Coupling Pin | 8 |
| Rotor Mount | 8 |
| Rotor | 8 |
| Structural Frame | 8 |
## Repository Structure

```text
CAD/
├── Assembly/
  ├── FreeCAD/
  ├── STEP/
├── Parts/
  ├── FreeCAD/
  ├── STEP/

Electronics/
├── Schematics/
├── PCB/
└── Wiring/

Images/
├── FinalAssembly.png
└── PrototypePhotos/

Documentation/
└── AdditionalFiles/
```
## Assembly Instructions

The Pellet DispensoMixer V2 follows a screwless cascade assembly method. Each module is inserted vertically on top of the previous component, using the geometry of the base to guide the assembly.

The motor module is first positioned onto the base structure. The upper rotor mount is then inserted above the motor, aligning the central shaft and the surrounding guide columns. Finally, the rotor is aligned on top of the cylindrical chamber and inserted onto the motor shaft.
<p align="center">
  <img src="Images/Image%207.png" alt="Pellet DispensoMixer V2 Assembly" width="750">
</p>

This approach reduces the need for additional fasteners, simplifies the assembly process, and makes the system easier to disassemble, inspect, and maintain.
