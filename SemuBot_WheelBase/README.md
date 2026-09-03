# Wheelbase

## Overview

This project implements a 3-motor BLDC wheelbase controller using an STM32G4 microcontroller and three independent 3-phase gate-driver/MOSFET power stages, one per wheel.

---

## Components

### Microcontroller
* **STM32G474RET6**
  Main controller (LQFP-64).

### BLDC Drivers
* **DRV8353FSRTAR** (x3)
  3-phase gate driver with integrated current-shunt amplifiers, one per motor.

### MOSFETs
* **AON7262E** (x18)
  N-channel MOSFETs for the power stage, 6 per motor (3-phase half-bridges).

### Current Sensing
* 9x 10 mΩ shunt resistors (2512 package), 3 per motor, read out through each DRV8353's integrated current-shunt amplifiers.

### Voltage Regulation
* **RT9013-33GB**
  3.3V LDO regulator.

### Power Input & Connectors
* **XT30PW-M**
  Main DC power input connector.

* **MR30PW-M** (x3)
  Motor phase power connectors, one per motor.

* **10155435-00011LF (Amphenol)**
  USB Type-C connector.

* **B5B-XH-A_LF(SN) (JST XH)** (x6)
  5-pin connectors for Hall/sensor inputs.

* **MTSW-104-09-L-S-400 (Samtec)**
  4-pin header, general purpose/debug I/O.

* **DS1013-10SSIB1**
  10-pin connector for general purpose I/O.

### ESD / Overvoltage Protection
* **PRTR5V0U2X**
  ESD protection for data lines (standard KiCad library part).
* **SMCJ33A**
  33V TVS diode for transient/overvoltage protection.
* **BZX84C3V3**
  3.3V zener diode.

### Timing & Clock
* **X322516MLB4SI**
  Crystal resonator for the STM32's HSE clock.

### User Interface
* 1x green + 4x red status LEDs.

---

## Technical Summary

### Power Stage
* **MOSFETs:** 18x AON7262E (6 per motor)
* **Gate Drivers:** 3x DRV8353FSRTAR
* **Current Sense Resistors:** 9x 10mΩ (2512 package), read via the DRV8353's built-in current-shunt amplifiers (no separate current-sense ADC on this revision)
