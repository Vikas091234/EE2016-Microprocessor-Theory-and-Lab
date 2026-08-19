# EE2016 — Microprocessor Theory + Lab

## 1. Overview

This report summarizes the laboratory work completed for EE2016 – Microprocessor Theory + Lab.

The experiments cover FPGA arithmetic implementation, AVR assembly programming, microcontroller peripherals and interrupts, MQTT-based IoT communication, ARM assembly, LPC2148 GPIO interfacing, and ADC/DAC implementation.

---

## 2. Experiment 1 — FPGA Multiplier

The first experiment implements two 4-bit multiplication techniques on an FPGA:

1. serial-parallel multiplication
2. Booth multiplication

The design targets an EDGE Artix-7 FPGA development board using Xilinx Vivado.

The submitted report contains Verilog implementations and discusses the computational efficiency of the two multiplication approaches.

The serial-parallel multiplier uses an accumulator and repeated shift/add operations. Booth multiplication reduces unnecessary operations for suitable signed binary patterns through recoding of the multiplier.

---

## 3. Experiment 2 — ATmega8 Assembly Emulation

The second experiment develops arithmetic and logical programs for the ATmega8 using assembly-language emulation.

The submitted work includes:

- 8-bit addition
- 16-bit addition
- multiplication
- comparison

The experiment provides practical exposure to:

- AVR registers
- immediate and register operations
- arithmetic instructions
- status flags
- instruction-level debugging

---

## 4. Experiment 3 — AVR Peripheral Interfacing

The third experiment moves from emulation to hardware interfacing.

The submitted work implements:

### LED blinking

An AVR assembly program configures an LED output and generates a periodic blink using delay loops.

### Push-button controlled LED

A push-button input is read through an AVR input port and used to control an LED.

### DIP-switch nibble addition

An 8-bit DIP-switch input is used to obtain values for a 4-bit/nibble addition operation.

The experiment demonstrates direct manipulation of AVR I/O registers:

```text
DDRx   → pin direction
PORTx  → output / pull-up control
PINx   → input reading
```

---

## 5. Experiment 4 — External Interrupts

The fourth experiment implements the ATmega8 external interrupts:

```text
INT0
INT1
```

Push buttons connected to the interrupt pins trigger the corresponding interrupt service routines.

The submitted implementation configures falling-edge detection and enables the interrupts through the AVR interrupt-control registers.

The ISR:

1. saves required processor state;
2. performs the LED blinking operation;
3. restores the saved state;
4. returns using `RETI`.

The experiment demonstrates event-driven execution instead of continuously polling an input.

---

## 6. Experiment 5 — MQTT and AVR-IoT

The fifth experiment introduces embedded networking using MQTT.

The hardware platform is the **AVR-IoT WG**, based on an ATmega4808 and equipped with Wi-Fi connectivity.

### MQTT publisher/subscriber model

A Mosquitto broker is used as the central MQTT server.

```text
MQTT Publisher
       |
       | publish(topic, message)
       v
   Mosquitto
    Broker
       |
       | subscribe(topic)
       v
MQTT Subscriber
```

The submitted report demonstrates communication between clients connected through the same network.

### AVR-IoT integration

The repository includes C implementations for MQTT publishing and subscription.

The second task extends the communication system with ADC-derived light information and an LCD.

```text
Light / ADC input
       ↓
AVR-IoT processing
       ↓
MQTT publisher
       ↓
Mosquitto broker
       ↓
MQTT subscriber
       ↓
LCD
```

This experiment combines embedded programming, networking, sensing, and display interfacing.

---

## 7. Experiment 6 — ARM Assembly

The sixth experiment introduces ARM assembly programming and emulation using Keil µVision.

The submitted report discusses:

- ARM architecture
- register organization
- RISC characteristics
- load/store operation
- ARM instruction set

The report includes assembly implementation of a factorial computation.

The experiment provides experience with low-level programming on a 32-bit ARM architecture.

---

## 8. Experiment 7 — LPC2148 GPIO Interfacing

The seventh experiment uses the LPC2148 ARM7 microcontroller.

The work includes three embedded-C programs.

### 8.1 DIP-switch and LED interfacing

The DIP-switch program configures the switch pins as inputs and reads their state through GPIO registers.

The corresponding LEDs are controlled according to the switch inputs.

### 8.2 LED output

The LED test program configures the LED pins as GPIO outputs and displays a byte value using the LED bank.

The implementation uses explicit bit masks for the LED pins.

### 8.3 Stepper motor

The stepper-motor program configures the motor-control pins as outputs and repeatedly applies the sequence:

```text
0x09
0x0C
0x06
0x03
```

The sequence is applied with a software delay between steps.

This demonstrates direct GPIO control and timing-sensitive peripheral operation.

---

## 9. Experiment 8 — ADC and DAC

The final experiment implements analog-to-digital and digital-to-analog conversion on the LPC2148.

### 9.1 ADC

The ADC implementation uses a 10-bit conversion system with a 3.3 V reference.

The processing flow is:

```text
Select ADC channel
       ↓
Configure ADC
       ↓
Start conversion
       ↓
Wait for ADC_DONE
       ↓
Check ADC_OVERRUN
       ↓
Extract conversion result
       ↓
Display result using LEDs
```

The implementation supports ADC channels through channel-selection constants.

### 9.2 DAC

The DAC implementation configures the LPC2148 DAC output and generates a square wave.

The output alternates between:

```text
DACR = 0 | DAC_BIAS
```

and:

```text
DACR = (0x3FF << 6) | DAC_BIAS
```

with a software delay between the two levels.

---

## 10. Technical Skills

The experiments collectively provide experience in several layers of embedded and digital-system design.

### Low-level programming

- AVR assembly
- ARM assembly
- embedded C
- register-level programming
- bit manipulation

### Digital hardware

- FPGA arithmetic
- FPGA pin constraints
- GPIO
- interrupts
- ADC
- DAC

### Embedded systems

- sensor acquisition
- LCD interfacing
- LED and switch interfacing
- stepper-motor control
- microcontroller peripherals

### Embedded networking

- MQTT
- publisher/subscriber architecture
- Mosquitto broker
- AVR-IoT Wi-Fi communication

---

## 11. Conclusion

The EE2016 laboratory work progresses from instruction-level programming to complete embedded-system interfaces.

The major progression is:

```text
AVR Assembly
     ↓
AVR Hardware Interfacing
     ↓
Interrupts
     ↓
IoT / MQTT
     ↓
ARM Assembly
     ↓
ARM GPIO
     ↓
ADC / DAC
```

The coursework provides practical exposure to processor architecture, assembly programming, embedded C, peripheral registers, interrupt-driven execution, digital I/O, analog interfaces, FPGA computation, and embedded networking.
