# Firmware Compilation and Upload

This folder contains the firmware documentation for the Pellet DispensoMixer V2.

The firmware is compiled and uploaded using the **Arduino IDE**. The system is based on the **BIGTREETECH Octopus Pro V1.1** control board, which uses an STM32 microcontroller. For the initial board connection and firmware upload, an **ST-LINK/V2** programmer can be used through the SWD interface.

---

A detailed tutorial on configuring and programming STM32 microcontrollers with STM32Duino can be found in the following blog post:

[Luis Llamas – Programming STM32 with Arduino IDE and a USB-TTL Converter](https://www.luisllamas.es/programar-stm32-con-ide-de-arduino-y-conversor-usb-ttl/)

---

## Required Software

Before compiling or uploading the firmware, install the following software:

| Software                | Purpose                                                    |
| ----------------------- | ---------------------------------------------------------- |
| Arduino IDE             | Firmware development, compilation, and upload              |
| STM32 MCU board package | STM32 board support inside Arduino IDE                     |
| ST-LINK/V2 drivers      | Required for the computer to detect the ST-LINK programmer |
| STM32CubeProgrammer     | Required for STM32 firmware upload and device detection    |

The official ST-LINK/V2 drivers can be downloaded from [STMicroelectronics](https://www.st.com/en/development-tools/stsw-link009.html).

STM32CubeProgrammer can also be downloaded from [STMicroelectronics](https://www.st.com/en/development-tools/stm32cubeprog.html).

The Arduino IDE can be downloaded from [Arduino](https://www.arduino.cc/en/software).

---

## Installing STM32 Support in Arduino IDE

1. Open the Arduino IDE.
2. Go to:

```text
File → Preferences
```

3. In **Additional Boards Manager URLs**, add the following URL:

```text
https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json
```

4. Then go to:

```text
Tools → Board → Boards Manager
```

5. Search for:

```text
STM32 MCU based boards
```

6. Install the STM32 board package.

---


---


## ST-LINK/V2 Connection

The ST-LINK/V2 is used to connect to the STM32 microcontroller through the SWD interface.

The SWD wiring documentation is available in:

```text
Electronics Schematics/
```

## Compiling the Firmware

To compile the firmware in Arduino IDE:

```text
Sketch → Verify/Compile
```

or press:

```text
Ctrl + R
```

If the compilation is successful, the Arduino IDE will generate the firmware binary without errors.

---

## Uploading the Firmware Through Arduino IDE

To upload the firmware:

1. Connect the ST-LINK/V2 to the computer.
2. Connect the ST-LINK/V2 to the SWD connector of the Octopus Pro V1.1.
3. Power the Octopus Pro board using USB-C or the external power supply.
4. Open the firmware project in Arduino IDE.
5. Select the correct STM32 board configuration.
6. Select the upload method: St Link v2


After the upload is complete, the board should restart and run the uploaded firmware.

---

## Firmware Upload Workflow

```text
Install ST-LINK/V2 drivers
        ↓
Install STM32CubeProgrammer
        ↓
Install STM32 board package in Arduino IDE
        ↓
Open firmware in Arduino IDE
        ↓
Select STM32 board configuration
        ↓
Connect ST-LINK/V2 through SWD
        ↓
Compile firmware
        ↓
Upload firmware from Arduino IDE
```

---

## Troubleshooting

### The ST-LINK/V2 is not detected

Check that:

* The ST-LINK/V2 drivers are installed.
* The USB cable is working.
* The ST-LINK/V2 appears correctly in the device manager.
* STM32CubeProgrammer can detect the programmer.

### The board is not detected

Check that:

* The Octopus Pro board is powered.
* `3V3`, `GND`, `SWDIO`, and `SWCLK` are correctly connected.
* The SWD cable order is correct.
* A lower SWD frequency is selected.
* The `RST` wire is connected if using hardware reset.

### Upload fails

Check that:

* The correct board is selected in Arduino IDE.
* The selected upload method is `STM32CubeProgrammer (SWD)`.
* STM32CubeProgrammer is installed.
* The ST-LINK/V2 drivers are correctly installed.
* The board is not shorted or incorrectly powered.

### Compilation errors

Check that:

* The STM32 board package is installed.
* All required libraries are installed.
* The firmware files are in the correct folder.
* The selected board matches the STM32 microcontroller used by the Octopus Pro V1.1.

---

## Safety Notes

* Do not connect or disconnect wiring while the board is powered.
* Do not connect 5 V to the SWD connector.
* Verify the polarity of the external power supply before powering the board.
* Keep the board on a non-conductive surface during testing.
* If any component overheats, disconnect power immediately.
* Always verify the wiring before uploading or running the firmware.

---

## Notes

The Pellet DispensoMixer V2 firmware is developed and uploaded using the Arduino IDE. The ST-LINK/V2 programmer is used for SWD communication with the STM32 microcontroller, especially during initial configuration, firmware upload, or debugging.
