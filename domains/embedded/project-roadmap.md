# Embedded Engineer Growth – Personal Project Roadmap

This document defines a sequence of personal projects designed to progressively build practical embedded systems skills. Each project aligns with the levels defined in the **Embedded Engineer Skill Tree** and focuses on developing real engineering experience rather than only theoretical knowledge.

The projects increase in complexity and introduce new concepts gradually.

---

# Level 1 – Programming Foundations Projects

Goal: Become comfortable writing correct and efficient C code.

## Project 1: Bit Manipulation Library

Build a small C library implementing common bit operations.

Features:

* Set / clear bits
* Toggle bits
* Extract bitfields
* Bit masks

Skills learned:

* Bitwise operations
* Header file organization
* Unit testing

---

## Project 2: Circular Buffer (Ring Buffer)

Implement a reusable circular buffer module.

Features:

* Push / pop operations
* Overflow protection
* Configurable buffer size

Skills learned:

* Pointers
* Memory management
* Data structure design

---

# Level 2 – Microcontroller Fundamentals Projects

Goal: Understand how peripherals work at the register level.

## Project 3: Bare-Metal LED Scheduler

Write firmware that schedules LED blinking patterns using timers.

Features:

* Timer interrupts
* Multiple blinking patterns
* Non-blocking delays

Skills learned:

* Timer configuration
* Interrupt handling
* Basic scheduling concepts

---

## Project 4: UART Communication Tool

Create a simple UART communication program.

Features:

* Send / receive characters
* Echo terminal
* Command parser

Skills learned:

* UART configuration
* Interrupt-driven communication
* Basic protocol design

---

# Level 3 – Driver Development Projects

Goal: Learn to build reusable hardware drivers.

## Project 5: Peripheral Driver Library

Write drivers for common peripherals without using vendor HAL.

Drivers to implement:

* GPIO
* UART
* SPI
* I2C
* Timers

Skills learned:

* Datasheet reading
* Register programming
* Hardware abstraction

---

## Project 6: DMA-Based Data Transfer

Use DMA to transfer data between memory and peripherals.

Features:

* DMA UART transmission
* DMA ADC sampling
* Interrupt callbacks

Skills learned:

* DMA controllers
* Interrupt coordination
* Performance optimization

---

# Level 4 – Firmware Architecture Projects

Goal: Build structured firmware systems.

## Project 7: Command Line Interface (CLI)

Create a firmware CLI over UART.

Features:

* Command parser
* Configurable commands
* Help system

Skills learned:

* Modular design
* Command dispatching
* Interface design

---

## Project 8: Telemetry and Logging System

Build a binary telemetry protocol between a microcontroller and a PC.

Features:

* Packet framing
* CRC error checking
* Telemetry messages
* Logging system

Skills learned:

* Communication protocol design
* Data serialization
* Debugging tools

---

# Level 5 – Real-Time Systems Projects

Goal: Understand scheduling and concurrency.

## Project 9: Mini RTOS Scheduler

Implement a simple cooperative scheduler.

Features:

* Task list
* Context switching simulation
* Timer tick

Skills learned:

* Task scheduling
* System timing
* Concurrency concepts

---

## Project 10: FreeRTOS Application

Develop a real application using FreeRTOS.

Features:

* Multiple tasks
* Message queues
* Mutex protection

Skills learned:

* RTOS architecture
* Synchronization
* Task communication

---

# Level 6 – Embedded System Integration Projects

Goal: Integrate multiple hardware components into a single system.

## Project 11: Sensor Fusion Node

Build a node that collects and processes data from multiple sensors.

Sensors:

* IMU
* Barometer
* Temperature sensor

Features:

* Sensor drivers
* Data filtering
* Telemetry output

Skills learned:

* Sensor integration
* Data processing
* Multi-peripheral coordination

---

## Project 12: Telemetry Ground Station

Create a desktop program that receives telemetry data.

Features:

* Packet decoding
* Data visualization
* Logging to files

Skills learned:

* Cross-platform communication
* Data visualization
* Tool development for embedded systems

---

# Level 7 – Debugging and Reliability Projects

Goal: Develop advanced debugging skills.

## Project 13: Fault Injection System

Intentionally introduce faults and detect them.

Examples:

* Memory corruption
* Stack overflow
* Communication failure

Skills learned:

* Defensive programming
* System diagnostics
* Reliability techniques

---

# Level 8 – Build Systems and Toolchains

Goal: Learn how complex embedded projects are structured.

## Project 14: Custom Embedded Build System

Create a project using a full build system.

Features:

* CMake configuration
* Cross-compilation toolchain
* Automated build scripts

Skills learned:

* Toolchain configuration
* Project structure
* Dependency management

---

# Level 9 – Advanced Projects

Goal: Work on complex embedded platforms.

## Project 15: Bootloader with Firmware Update

Develop a firmware update mechanism.

Features:

* Dual firmware images
* UART update protocol
* CRC verification

Skills learned:

* Flash memory management
* Boot process
* System reliability

---

## Project 16: Distributed Embedded System

Create multiple embedded nodes communicating together.

Features:

* Message bus
* Device discovery
* Synchronization

Skills learned:

* Distributed architecture
* Communication protocols
* System coordination

---

# Notes

These projects are designed to simulate real-world embedded engineering challenges. Completing even a subset of them will significantly strengthen practical skills and help bridge the gap between theoretical knowledge and professional embedded development.

The recommended approach is:

1. Select a project
2. Design the architecture
3. Implement incrementally
4. Document the system
5. Analyze failures and improve the design
