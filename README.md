# EE2016 Microprocessor Theory + Lab

Coursework archive for **EE2016 – Microprocessor Theory + Lab** at IIT Madras.

This repository contains my implementation files and lab reports from the course, organized by experiment. It focuses on low-level programming, FPGA constraints, AVR assembly, embedded C, MQTT-based machine-to-machine communication, ARM/LPC2148 interfacing, GPIO, ADC, and DAC.

## Scope

The repository keeps **my own code and lab reports** that are useful as a technical record. Course manuals, lecture notes, vendor reference manuals, assignment handouts, duplicate files, and unrelated media are intentionally excluded.

## Experiments Included

| Experiment | Topic | Main technical areas |
|---|---|---|
| 01 | FPGA | Artix-7 board constraints / XDC |
| 02 | AVR Emulation | AVR assembly and emulator-based work |
| 03 | AVR Hardware | AVR peripheral interfacing |
| 04 | AVR Interrupts | AVR assembly, external interrupt INT1 |
| 05 | M2M / IoT | AVR-IoT, MQTT, ADC, LCD, publish/subscribe |
| 06 | ARM Assembly | ARM assembly programming and emulation |
| 07 | LPC2148 GPIO | DIP switches, LEDs, stepper motor control |
| 08 | ADC / DAC | LPC2148 ADC acquisition and DAC waveform generation |

## Repository Structure

```text
.
├── README.md
├── experiments/
│   ├── 01-fpga/
│   ├── 04-avr-interrupt/
│   ├── 05-m2m-mqtt/
│   ├── 07-lpc2148-gpio/
│   └── 08-adc-dac/
├── reports/
│   ├── experiment-01-fpga-report.pdf
│   ├── experiment-02-avr-emulation-report.pdf
│   ├── experiment-03-avr-hardware-report.pdf
│   ├── experiment-04-avr-interrupt-report.pdf
│   ├── experiment-05-m2m-mqtt-iot-report.pdf
│   ├── experiment-06-arm-assembly-report.pdf
│   ├── experiment-07-lpc2148-report.pdf
│   └── experiment-08-adc-dac-report.pdf
└── constraints/
```

## Experiment Highlights

### Experiment 01 — FPGA

The repository retains the Artix-7 master XDC file used for board-level pin constraints. It defines interfaces for clocks, switches, LEDs, push buttons, seven-segment display, Bluetooth, buzzer, SPI DAC, HDMI, LCD, and SDRAM.

The HDL/top-level implementation itself is not present in the supplied coursework folder, so this repository does not claim to contain a complete FPGA design.

### Experiment 04 — AVR Interrupts

Contains AVR assembly demonstrating external interrupt handling through the INT1 mechanism.

### Experiment 05 — M2M Communication / IoT

This is the strongest embedded-systems component in the repository.

The implementation contains publisher/subscriber programs and an LCD-enabled variant. The workflow includes:

```text
Sensor / ADC input
      ↓
AVR-IoT firmware
      ↓
MQTT publish
      ↓
Broker
      ↓
MQTT subscribe
      ↓
LCD / output
```

The repository therefore contains both communication-side code and the sensor/LCD integration code used in the lab.

### Experiment 07 — LPC2148

Contains embedded C programs for:

- DIP-switch to LED interfacing
- LED testing
- stepper-motor control using a standard four-step sequence

### Experiment 08 — ADC / DAC

Contains LPC2148 code for ADC initialization/readout and DAC square-wave generation.

The ADC program configures selectable ADC channels, waits for conversion completion, extracts the 10-bit result, and maps the result to LEDs. The DAC program writes low and high digital values to generate a square-wave output.

## Tools / Platforms

Depending on the experiment, the work uses:

- AVR microcontrollers / AVR assembly
- AVR-IoT hardware
- MQTT / Mosquitto
- LPC2148 ARM7 microcontroller
- Artix-7 FPGA board
- Embedded C
- ARM assembly
- FPGA pin constraints (XDC)

## Reports

The `reports/` directory contains my lab reports for the experiments represented in the original coursework archive. These are kept as supporting documentation; the source code under `experiments/` is the primary technical artifact.

## Important Note

This is a **coursework repository**, not a single standalone software project. The individual experiments were completed as part of EE2016. For placement resumes, a specific experiment such as the M2M/MQTT IoT implementation can be described as a course project only if it satisfies the IIT Madras placement verification requirements.

For IIT Madras Placement Season 2026–27, course projects must be explicitly identified as course projects in the resume and the official course/course number must be included in the master resume.

## Author

Vikas Raj  
EE19B108  
B.Tech Electrical Engineering, IIT Madras
