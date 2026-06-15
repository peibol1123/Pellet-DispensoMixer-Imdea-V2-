# Electronic Schematics

This folder contains the electronic wiring documentation for the Pellet DispensoMixer V2.

The electronic system is based on a **BIGTREETECH Octopus Pro V1.1** main control board, **A4988 stepper motor drivers**, **NEMA 17 stepper motors**, an external power supply, and an **ST-LINK/V2** programmer for SWD programming.

The objective of this documentation is to make the electronic assembly easier to reproduce, inspect, modify, and maintain.

---

## Main Components

| Component                    | Function                                     |
| ---------------------------- | -------------------------------------------- |
| BIGTREETECH Octopus Pro V1.1 | Main control board                           |
| A4988 stepper motor drivers  | Motor driver modules                         |
| NEMA 17 stepper motors       | Actuation of the dispensing modules          |
| External power supply        | Power input for the control board and motors |
| ST-LINK/V2                   | SWD programming and debugging interface      |

---

## Electronics Connections
### System Architecture

The electronics are centralized around the **BIGTREETECH Octopus Pro V1.1**, which acts as the main control board for the complete dispensing system.

```text
Power Supply
      │
      ▼
BIGTREETECH Octopus Pro V1.1
      │
      ├── A4988 Driver 1 ── NEMA 17 Motor 1
      ├── A4988 Driver 2 ── NEMA 17 Motor 2
      ├── A4988 Driver 3 ── NEMA 17 Motor 3
      ├── A4988 Driver 4 ── NEMA 17 Motor 4
      ├── A4988 Driver 5 ── NEMA 17 Motor 5
      ├── A4988 Driver 6 ── NEMA 17 Motor 6
      ├── A4988 Driver 7 ── NEMA 17 Motor 7
      └── A4988 Driver 8 ── NEMA 17 Motor 8
```

This architecture simplifies the wiring compared with the previous version of the system, since all motor control is handled from a single main board.


### Power Connection

The external power supply is connected to the main power input of the Octopus Pro board.

| Power Supply    | Octopus Pro Connection |
| --------------- | ---------------------- |
| Positive output | `POWER +` / `VIN +`    |
| Negative output | `POWER -` / `GND`      |

Before powering the system, check:

* Correct polarity of the power input.
* Correct voltage level for the board and motor drivers.
* Correct motor power jumper configuration.
* No loose wires or accidental short circuits.

Do not power the board if the polarity or voltage configuration is uncertain.



### Stepper Driver and Stepper Motor Installation

Each motor has two internal coils. Before connecting the motors, identify the coil pairs using a multimeter in continuity mode.

Each **A4988 stepper motor driver** is inserted into one of the driver sockets of the Octopus Pro board.
<p align="center">
  <img src="Electronic%20Schematic.png" alt="Electronic Schematic" width="800">
</p>
Important notes:

* Check the orientation of each A4988 driver before powering the board.
* Do not insert or remove drivers while the board is powered.
* Use heatsinks if the drivers operate for long periods or under high current.
* Adjust the current limit of each driver before continuous operation.

If a motor vibrates but does not rotate, the coil pairs may be incorrectly connected. If the motor rotates in the opposite direction, reverse the motor direction in firmware or swap one coil pair.

Do not connect or disconnect stepper motors while the board is powered



---

## ST-LINK/V2 Programming Connection

Before connecting the ST-LINK/V2 programmer, make sure that the required USB drivers are installed on the host computer.
The official ST-LINK drivers can be downloaded from [STMicroelectronics](https://www.st.com/en/development-tools/stsw-link009.html):

It is also recommended to install  [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html), which provides the required tools for firmware upload, device detection, memory inspection, and debugging, however the firmware is gonna upload through Arduino Ide:

The following image provides a reference for the ST-LINK/V2 pinout.
<p align="center">
  <img src="St%20link%20v2%20References.jpg" alt="ST Link V2 References" width="800">
</p>
Recommended ST-LINK/V2 to Octopus Pro connection:

| ST-LINK/V2 20-pin Connector | Signal                             | Octopus Pro SWD Connector |
| --------------------------- | ---------------------------------- | ------------------------- |
| Pin 1                       | `VCCIN` / target voltage reference | `3V3`                     |
| Pin 7                       | `TMS` / `SWDIO`                    | `SWDIO`                   |
| Pin 9                       | `TCK` / `SWCLK`                    | `SWCLK`                   |
| Pin 15                      | `NRST`                             | `RST`                     |
| Pin 4 or any GND pin        | `GND`                              | `GND`                     |

The `RST` connection is optional for basic SWD communication, but it is recommended because it allows the programmer to connect using hardware reset if needed.

The following image provides a reference for the BIGTREETECH Octopus Pro V1.1 pinout.
<p align="center">
  <img src="btt_octopus_pro_1.0_pins.png" alt="BTT Octopus Pro V1.1 Pinout" width="900">
</p>

## Suggested Cable Color Code

| Signal                    | Recommended Color |
| ------------------------- | ----------------- |
| `3V3` / voltage reference | Red               |
| `GND`                     | Black             |
| `SWDIO`                   | Blue              |
| `SWCLK`                   | Yellow            |
| `RST`                     | Green             |

This color code is recommended to reduce wiring mistakes during programming and debugging.

---

## Electronics Assembly Procedure

1. Verify that the Octopus Pro board is powered off.
2. Insert the A4988 stepper motor drivers into the driver sockets.
3. Check the orientation of every A4988 driver.
4. Connect each NEMA 17 motor to its corresponding motor output.
5. Verify the coil pairs of each motor before powering the system.
6. Connect the external power supply to the Octopus Pro power input.
7. Connect the ST-LINK/V2 to the SWD connector if firmware programming is required.
8. Power the board and verify that no driver overheats.
9. Test each motor individually before running the full dispensing sequence.
10. If a motor moves in the wrong direction, correct the direction in firmware or swap one coil pair.

---

## Safety Notes

* Always disconnect power before modifying the wiring.
* Do not connect or disconnect motors while the board is powered.
* Do not insert or remove stepper drivers while the board is powered.
* Check the current limit of each A4988 driver before long operation.
* Verify power supply voltage and polarity before testing.
* Keep the board on a non-conductive surface during initial tests.
* If any component becomes excessively hot, power off the system immediately.

---
