# EE2016 — Microprocessor Theory + Lab

Coursework, laboratory implementations, reports, and supporting material for **EE2016 – Microprocessor Theory + Lab at IIT Madras**.

The work covers FPGA-based arithmetic, AVR assembly programming, AVR peripheral interfacing, external interrupts, MQTT-based IoT communication, ARM assembly, LPC2148 GPIO control, stepper-motor interfacing, and ADC/DAC programming.

## Repository Structure

```text
.
├── README.md
├── REPORT.md
│
├── Experiment1-FPGA/
│   ├── EDGE-Artx7FPGA-UsrMnlWth-SDRAM-V2.0.pdf
│   ├── EDGE_Artix7_Master.xdc
│   ├── EE2016F24Expr1InfoBthsMltplr.pdf
│   ├── EE2016F24Exprmnt1HndOutFPGA.pdfA
│   └── experiment1_report.pdf
│
├── Experiment2AVR-Emltn/
│   ├── EE19B108_Report2.pdf
│   └── EE2016F24Exprmnt2AVR-AssmblyEmltn.pdf
│
├── Experiment3AVR-Hrdwre/
│   ├── EE2016F24Exprmnt3AVR-Prphrls.pdf
│   ├── Exp2HrdwreAVRVideo-20240827.mp4
│   └── Experiment -3 Report.pdf
│
├── Experiment4-AVR-Intrrpt/
│   ├── EE2016F24ExpIntrrpt-INT1Mdle.asm
│   ├── EE2016F24HndtExprmnt4AVR-Intrrpt.pdf
│   └── EXPERIMENT4-REPERT.pdf
│
├── Experiment5M2M-CmmnctnsIoT-AVR/
│   ├── AVR-IoT-WG-Manual.pdf
│   ├── EE19B108_RprtLab5.pdf
│   ├── EE2016S24Exprmnt5AVR-M2M-V2.0.pdf
│   ├── Exp5OfflneM2M-CmmnctnsBtwn2MblsPrcdre.pdf
│   ├── MPLAB-Code-Cnfgrtr-MQTT-Lbrry.pdf
│   ├── Task1M2M-c-filesCmmntd/
│   │   ├── M2M-MQTT-MosquitoPblshM-Cmmntd.c
│   │   ├── M2M-MQTT-MosquitoSbscrbeM-Cmmntd.c
│   │   ├── mainPublishCmmntd.c
│   │   └── mainSubscribeCmmntd.c
│   └── Task2M2M-WithLCD/
│       ├── LCD-ConnectionsFnl.docx
│       ├── M2M-MQTT-MosquittoPublish.c
│       ├── M2M-MQTT-MosquittoSubscribeMdle.c
│       ├── mainPublishLuxADC-Mdle.c
│       └── mainSubscribeLuxLCD.c
│
├── Experiment6AssmblyEmltnARM/
│   ├── BkTxtARM.AssmblyPrgrmmngWelsh.pdf
│   ├── EE19B108_Expt6_LABREPORT.pdf
│   └── EE2016F24Exprmnt6AssmblyEmltnARM.pdf
│
├── Experiment7DIP-SwitchLED-Stppr/
│   ├── Demo-C-Codes/
│   │   ├── DIP-SwtchToLED-InLPC2148Mdle.c
│   │   ├── StpprMtrCntrlInLPC2148Mdle.c
│   │   └── TstLED-InLPC2148Mdle.c
│   ├── EE2016F24Exprmnt7SwtchLEDStpprMtrCntrl.pdf
│   ├── EXP_7_REPORT.pdf
│   ├── LPC2148-UM10139.pdf
│   └── SunTechLPC2148Manual.pdf
│
└── Experiment8ADCDAC/
    ├── EE2016F24Exprmnt8ADCDAC.pdf
    ├── EXP_7_MUP.pdf
    ├── SquareDAC.c
    └── adc2148.c
```

## Experiments

| Experiment | Topic | Main work |
|---|---|---|
| 1 | FPGA multiplier | 4-bit serial-parallel multiplier and Booth multiplier |
| 2 | AVR assembly emulation | Arithmetic and logical operations using ATmega8 assembly |
| 3 | AVR hardware peripherals | LED, push-button, DIP-switch interfacing using AVR assembly |
| 4 | AVR interrupts | External INT0/INT1 interrupt handling |
| 5 | M2M / IoT | MQTT communication using AVR-IoT and Mosquitto |
| 6 | ARM assembly emulation | ARM instruction programming using Keil µVision |
| 7 | LPC2148 interfacing | DIP switches, LEDs, and stepper motor control |
| 8 | ADC / DAC | ADC acquisition and DAC waveform generation on LPC2148 |

---

## Experiment 1 — FPGA Multiplier

The FPGA experiment implements and compares two multiplication approaches:

- 4-bit serial-parallel multiplication
- 4-bit Booth multiplication

The experiment uses an **EDGE Artix-7 FPGA development board** and Xilinx Vivado.

The report includes Verilog implementations and a comparison of the two algorithms in terms of computation/clock-cycle requirements.

### Files

- `experiment1_report.pdf` — submitted report
- `EDGE_Artix7_Master.xdc` — FPGA board pin constraints
- `EE2016F24Exprmnt1HndOutFPGA.pdf` — experiment handout
- `EE2016F24Expr1InfoBthsMltplr.pdf` — Booth multiplier material
- `EDGE-Artx7FPGA-UsrMnlWth-SDRAM-V2.0.pdf` — board reference manual

---

## Experiment 2 — AVR Assembly Emulation

The experiment uses the **Atmel ATmega8** instruction set in an emulation environment.

The submitted report implements arithmetic and comparison operations including:

- 8-bit addition
- 16-bit addition using an 8-bit processor
- multiplication
- comparison

The work uses AVR assembly instructions and Microchip Studio for development and debugging.

---

## Experiment 3 — AVR Hardware Peripherals

The experiment demonstrates peripheral access on the ATmega8 using assembly programming.

The submitted report covers:

- LED blinking
- push-button controlled LED operation
- 4-bit nibble addition using an 8-bit DIP switch

The work introduces AVR GPIO registers including:

- Data Direction Registers
- PORT registers
- PIN registers

The experiment also covers practical handling of input pins and pull-up/pull-down behavior.

---

## Experiment 4 — AVR External Interrupts

The experiment implements external interrupts **INT0 and INT1** on the ATmega8.

The submitted implementation uses push buttons connected to the interrupt inputs and an LED connected to PB0.

When an interrupt is triggered, the corresponding interrupt service routine makes the LED blink approximately ten times with one-second ON/OFF intervals.

The repository includes:

```text
EE2016F24ExpIntrrpt-INT1Mdle.asm
```

and the submitted experiment report.

Key concepts:

- interrupt vectors
- INT0 / INT1
- falling-edge detection
- interrupt enable registers
- stack initialization
- interrupt service routines
- `RETI`
- global interrupt enable

---

## Experiment 5 — M2M Communication and IoT

This experiment uses the **AVR-IoT board**, MQTT, and a Mosquitto broker.

The submitted work contains two tasks.

### Task 1 — MQTT communication

The MQTT publisher/subscriber model is demonstrated using a Mosquitto broker.

The repository includes commented and implementation C files for:

- MQTT publishing
- MQTT subscription
- main publisher program
- main subscriber program

The communication flow is:

```text
Publisher
    ↓
MQTT topic
    ↓
Mosquitto broker
    ↓
Subscriber
```

### Task 2 — MQTT with LCD and ADC

The second task integrates the AVR-IoT board with an LCD and ADC-based sensor data.

The repository contains:

- MQTT publisher module
- MQTT subscriber module
- ADC/lux publishing program
- LCD subscriber program
- LCD connection documentation

The experiment demonstrates sensing, communication, and display in an embedded IoT workflow.

---

## Experiment 6 — ARM Assembly Emulation

The experiment introduces ARM assembly programming and emulation using **Keil µVision**.

The submitted report includes ARM assembly programs such as factorial computation and discusses:

- ARM architecture
- ARM registers
- RISC instruction set
- load/store architecture
- ARM assembly instructions
- program emulation

---

## Experiment 7 — LPC2148 Interfacing

The experiment uses an **LPC2148 ARM7-based development board** and embedded C.

Three implementation files are included.

### DIP Switch to LEDs

`DIP-SwtchToLED-InLPC2148Mdle.c`

Reads the DIP-switch inputs and controls the corresponding LEDs.

### LED Test

`TstLED-InLPC2148Mdle.c`

Configures the LED GPIO pins and displays a byte value using the LED bank.

### Stepper Motor Control

`StpprMtrCntrlInLPC2148Mdle.c`

Controls a stepper motor connected to LPC2148 GPIO pins using the sequence:

```text
0x09 → 0x0C → 0x06 → 0x03
```

The program repeatedly applies the sequence with a delay between steps.

---

## Experiment 8 — ADC / DAC

The experiment implements ADC and DAC functionality on the LPC2148 using C.

### ADC

`adc2148.c` configures ADC0 and reads a 10-bit conversion result.

The implementation includes:

- selectable ADC channels
- ADC clock configuration
- conversion-complete detection
- overrun detection
- 3.3 V reference
- 10-bit conversion
- LED-based representation of the ADC result

### DAC

`SquareDAC.c` configures the LPC2148 DAC output and generates a square wave by alternating between low and high digital values.

The DAC output uses:

```text
0
```

and

```text
0x3FF
```

with the DAC bias bit enabled.

---

## Hardware and Software

The coursework uses several embedded platforms and development environments:

### Hardware

- EDGE Artix-7 FPGA board
- Atmel ATmega8 / ATmega8L
- AVR-IoT WG
- LPC2148 ARM7 development board
- LEDs
- DIP switches
- push buttons
- LCD
- stepper motor
- ADC/DAC interfaces

### Software

- Xilinx Vivado
- Microchip Studio
- MPLAB X
- Keil µVision 5
- Flash Magic
- AVR Burn-O-Mat
- Mosquitto MQTT broker

## Technical Areas

- Verilog / FPGA design
- AVR assembly
- ARM assembly
- Embedded C
- GPIO
- interrupts
- ADC/DAC
- MQTT
- sensor interfacing
- LCD interfacing
- stepper-motor control
- FPGA pin constraints
- microcontroller architecture
