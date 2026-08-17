# EE2016 Microprocessor Theory + Lab — Technical Report

## 1. Overview

EE2016 Microprocessor Theory + Lab covers low-level processor programming and embedded-system interfacing across FPGA, AVR, ARM/LPC2148, and IoT-based experiments.

The submitted repository preserves the implementation artifacts and personal lab reports from the available coursework archive. The emphasis is on the actual code and hardware-facing work rather than course handouts or vendor documentation.

## 2. Technical Coverage

The retained material demonstrates work across:

- FPGA board constraints
- AVR assembly programming
- external interrupt handling
- embedded C
- MQTT publish/subscribe communication
- sensor/ADC integration
- LCD interfacing
- LPC2148 GPIO
- stepper motor control
- ADC conversion and digital readout
- DAC waveform generation
- ARM assembly/emulation

## 3. Experiment 01 — FPGA

The retained artifact is an Artix-7 XDC constraint file.

It assigns physical FPGA pins to interfaces including:

- clock
- 16 switches
- 16 LEDs
- push buttons
- seven-segment display
- Bluetooth TX/RX
- buzzer
- SPI DAC
- HDMI
- 2×16 LCD
- SDRAM

Because the supplied folder does not include a complete HDL top-level source, this repository treats the experiment as a board-constraint artifact rather than claiming a complete FPGA implementation.

## 4. Experiment 02 — AVR Emulation

The supplied personal report is retained under `reports/`. The original coursework archive did not provide a separate source implementation alongside the report, so the repository does not invent or reconstruct one.

## 5. Experiment 03 — AVR Hardware

The supplied personal report documents the hardware experiment. The original archive includes a demonstration video and course documentation, but these are intentionally not part of the GitHub repository.

## 6. Experiment 04 — AVR Interrupts

The repository includes an AVR assembly implementation for external interrupt handling using INT1.

The experiment demonstrates low-level control of processor interrupt mechanisms and interrupt-driven execution.

## 7. Experiment 05 — M2M Communication / IoT

This is the most substantial embedded implementation retained from the course.

### 7.1 MQTT communication

The repository contains separate publisher and subscriber programs, including commented/annotated variants and an LCD-enabled version.

The conceptual communication path is:

```text
AVR-IoT device
     |
     | MQTT publish
     v
MQTT broker
     |
     | MQTT subscribe
     v
Receiving device
```

### 7.2 Sensor and display integration

The second task integrates ADC-derived light information with MQTT and LCD output.

Conceptually:

```text
Light sensor
    ↓
ADC acquisition
    ↓
AVR processing
    ↓
MQTT message
    ↓
MQTT subscriber
    ↓
LCD display
```

This experiment demonstrates a complete embedded data path from sensing to communication to presentation.

## 8. Experiment 06 — ARM Assembly

The supplied personal lab report is retained. The implementation is associated with ARM assembly emulation work. Vendor/reference material from the original coursework archive is excluded.

## 9. Experiment 07 — LPC2148 GPIO and Stepper Motor

The repository includes three embedded C implementations.

### DIP-switch to LED

Reads GPIO switch states and drives corresponding LEDs.

### LED test

Initializes the LED output pins and maps a byte value to the LED bank using bit operations.

### Stepper motor

Uses a four-element sequence:

```text
0x09 → 0x0C → 0x06 → 0x03
```

and repeatedly sends the sequence to the motor control pins to produce stepping motion.

This demonstrates GPIO configuration, bit manipulation, timing loops, and peripheral control on the LPC2148.

## 10. Experiment 08 — ADC / DAC

### ADC

The ADC implementation:

1. selects an ADC channel;
2. configures the ADC clock and operating mode;
3. starts a conversion;
4. waits for the conversion-complete flag;
5. checks for overrun;
6. extracts the 10-bit conversion result;
7. maps the value to LEDs.

The code defines a 3.3 V reference and a 10-bit full-scale conversion count of 1024.

### DAC

The DAC program configures the LPC2148 DAC output and alternates between low and high digital values with a delay, generating a square-wave output.

## 11. Relevance to Embedded / Hardware Roles

The experiments collectively demonstrate low-level interaction with hardware rather than only application-level programming.

The most resume-relevant technical areas are:

- embedded C
- assembly programming
- microcontroller peripherals
- GPIO
- ADC/DAC
- interrupts
- MQTT and embedded networking
- sensor integration
- LCD interfacing
- FPGA board constraints
- ARM/AVR architectures

For an ML-hardware-oriented profile, this coursework is supporting evidence for understanding the lower layers surrounding accelerated and embedded computation.

## 12. Limitations

This repository represents coursework rather than a production embedded system.

Some experiments are represented primarily by lab reports because the supplied archive did not contain the corresponding source code. Hardware-specific libraries, IDE project files, board manuals, and vendor documentation are not included because they are not necessary to demonstrate the student's implementation and may not be appropriate for redistribution.

## 13. Repository Organization

The final repository separates:

```text
experiments/  → source code and hardware constraint files
reports/      → personal lab reports
```

Course manuals, lecture notes, tutorials, vendor manuals, duplicate documents, and unrelated media are intentionally excluded.
