# Embedded Engineer Growth – Progress Tracker

This document tracks progress through the learning resources and practical work defined in the **Skill Tree**, **Project Roadmap**, and **Books** documents. It is designed to be **progress‑based rather than time‑based**, allowing advancement whenever tasks are completed rather than on a fixed schedule.

Each stage corresponds to a level in the Skill Tree. Within each stage, tasks are divided into categories to make progress clearer and easier to organize.

Recommended usage:

* Mark tasks as completed when you feel confident with them.
* Add notes or links to your implementations.
* Add new tasks when your work experience introduces new topics.

---

# Stage 1 – Programming Foundations

Goal: Achieve strong mastery of C fundamentals and low‑level programming behavior.

## Knowledge

[ ] Understand memory layout (stack, heap, static, flash)

[ ] Understand pointer arithmetic

[ ] Understand bitwise operations

[ ] Understand undefined behavior in C

[ ] Understand compiler warnings and optimization basics

## Books

[ ] Read **The C Programming Language**

[ ] Read **Expert C Programming: Deep C Secrets**

## Projects

[ ] Implement Bit Manipulation Library

[ ] Implement Circular Buffer (Ring Buffer)

## Tools

[ ] Use Git comfortably for version control

[ ] Compile C programs with GCC or Clang

[ ] Use GDB to inspect variables and memory

---

# Stage 2 – Microcontroller Fundamentals

Goal: Understand how microcontrollers interact with hardware at the register level.

## Knowledge

[ ] Understand memory‑mapped I/O

[ ] Understand interrupt mechanisms

[ ] Understand timers and clock configuration

[ ] Understand peripheral clock enabling

[ ] Understand GPIO configuration

## Books

[ ] Study **Embedded Systems: Introduction to ARM Cortex‑M Microcontrollers – Jonathan Valvano**

## Projects

[ ] Bare‑Metal LED Scheduler using timers

[ ] UART Communication Tool with command parsing

## Tools

[ ] Use an oscilloscope to observe signals

[ ] Use a logic analyzer for protocol inspection

[ ] Use a hardware debugger (JTAG / SWD)

---

# Stage 3 – Driver Development

Goal: Develop reusable peripheral drivers from datasheets.

## Knowledge

[ ] Understand peripheral register configuration

[ ] Understand interrupt‑driven drivers

[ ] Understand DMA fundamentals

[ ] Understand hardware abstraction layers

## Books

[ ] Review **Making Embedded Systems – Elecia White**

## Projects

[ ] Implement GPIO driver

[ ] Implement UART driver

[ ] Implement SPI driver

[ ] Implement I2C driver

[ ] Implement Timer driver

[ ] Implement DMA transfer example

## Practice

[ ] Read and interpret datasheets independently

[ ] Debug peripheral configuration errors

---

# Stage 4 – Firmware Architecture

Goal: Design structured and maintainable embedded firmware systems.

## Knowledge

[ ] Understand modular firmware architecture

[ ] Understand event‑driven systems

[ ] Understand state machines

[ ] Understand communication protocol structure

## Books

[ ] Study **Designing Embedded Systems with PIC Microcontrollers – Tim Wilmshurst**

[ ] Study **Patterns in the Machine – John Bennett**

## Projects

[ ] Implement UART Command Line Interface (CLI)

[ ] Implement Telemetry and Logging System

## Practice

[ ] Design a layered firmware architecture

[ ] Document system architecture before implementation

---

# Stage 5 – Real‑Time Systems

Goal: Understand deterministic timing and concurrent task execution.

## Knowledge

[ ] Understand interrupt latency

[ ] Understand task scheduling

[ ] Understand concurrency issues

[ ] Understand synchronization primitives

## Books

[ ] Study **Real‑Time Concepts for Embedded Systems – Qing Li & Caroline Yao**

## Projects

[ ] Implement Mini RTOS Scheduler

[ ] Build a small FreeRTOS application

## Practice

[ ] Analyze timing behavior of firmware

[ ] Measure execution time of critical code paths

---

# Stage 6 – Embedded System Integration

Goal: Build complete systems with multiple hardware and software components.

## Knowledge

[ ] Understand sensor integration

[ ] Understand telemetry architectures

[ ] Understand fault detection strategies

[ ] Understand power management considerations

## Books

[ ] Study **Computer Systems: A Programmer's Perspective – Bryant & O'Hallaron**

## Projects

[ ] Implement Sensor Fusion Node

[ ] Implement Telemetry Ground Station tool

## Practice

[ ] Integrate multiple peripherals in a single system

[ ] Design communication protocols between nodes

---

# Stage 7 – Debugging and Reliability

Goal: Develop strong diagnostic and troubleshooting skills.

## Knowledge

[ ] Understand memory corruption causes

[ ] Understand race conditions

[ ] Understand stack overflow behavior

[ ] Understand fault handling (HardFault analysis)

## Books

[ ] Read **Debugging: The 9 Indispensable Rules – David J. Agans**

## Practice

[ ] Document real debugging cases in Debugging Playbook

[ ] Practice systematic debugging workflows

[ ] Use trace tools and hardware instrumentation

## Projects

[ ] Implement Fault Injection System

---

# Stage 8 – Build Systems and Toolchains

Goal: Understand how complex embedded projects are built and managed.

## Knowledge

[ ] Understand cross‑compilation

[ ] Understand linker scripts

[ ] Understand build dependency systems

## Projects

[ ] Create Embedded Project with CMake

[ ] Configure cross‑compilation toolchain

## Practice

[ ] Analyze build output and compiler flags

[ ] Configure reproducible builds

---

# Stage 9 – Advanced Embedded Systems

Goal: Develop expertise in advanced firmware topics.

## Knowledge

[ ] Understand boot process

[ ] Understand firmware update strategies

[ ] Understand distributed embedded systems

## Projects

[ ] Implement Bootloader with Firmware Update

[ ] Build Distributed Embedded Node Network

## Books

[ ] Study **Computer Organization and Design – Patterson & Hennessy**

---

# Work Sessions (Core System)

Use this section to track every work session. This is your **main driver for progress**.

You do NOT need long sessions. Even 20–30 minutes counts.

Template:

### Session XXX

Date: YYYY-MM-DD
Time spent: XX min / hours

Project:

* (Name of the project from your Project Roadmap)

Focus:

* (What you worked on)

What I did:

* (Concrete actions taken)

Blockers:

* (Problems encountered)

Next step:

* (Clear next action to resume quickly)

Skills used:

* (e.g., UART, Debugging, Timers, C pointers)

---

Example:

### Session 001

Date: 2026-03-16
Time spent: 45 min

Focus:

* UART driver debugging

What I did:

* Fixed baud rate mismatch
* Tested communication with logic analyzer

Blockers:

* Occasional framing error still present

Next step:

* Verify clock configuration

Skills used:

* UART, Debugging, Timing analysis

---

# Project Index

This section groups all sessions by project. It helps you:

* Track progress per project
* See development history
* Easily extract portfolio content

How to use:

* When you start a new project, create an entry here
* Add session references as you progress

---

## Project: (Project Name)

Description:

* (Short description of the project)

Sessions:

* Session XXX
* Session XXX

Status:

* (In Progress / Completed / On Hold)

Key Outcomes:

* (What was achieved)

---

# Milestones

Use this section to record **important completions** (not small tasks).

Examples:

* Completed full UART driver with interrupt support
* Finished Mini RTOS Scheduler
* Built working telemetry system

Milestones should represent **meaningful engineering achievements**.

---

# Personal Progress Notes

Use this section to record reflections and major milestones.

Example:

* "Completed driver library using STM32 registers"

* "Implemented telemetry protocol for personal project"

* "Solved DMA race condition bug"

These notes help track real engineering growth over time.

---

# Portfolio Extraction Template

Use this template to convert any project from the **Project Index** (and its sessions) into a clean, interview-ready portfolio entry.

---

## Project Title

(Use the same name as in Project Index)

### Overview

* What the system does
* Context (personal project, team project, job-related without sensitive details)

### Objectives

* What you set out to build or solve

### System Architecture

* High-level structure (modules, data flow)
* Key components (MCU, peripherals, interfaces)

### Your Responsibilities

* What YOU specifically designed, implemented, or debugged

### Key Features

* (e.g., interrupt-driven communication, DMA transfers, CLI interface, telemetry protocol)

### Technical Details

* Important implementation choices
* Algorithms, state machines, timing strategies
* Interfaces and protocols used

### Challenges & Debugging

* Main issues encountered
* How you diagnosed them
* Tools used (oscilloscope, logic analyzer, debugger)

### Results

* What works (validated behavior)
* Performance notes (latency, reliability, throughput if applicable)

### Lessons Learned

* What you would improve
* Key takeaways

### Artifacts (Optional)

* Diagrams (block diagram, timing diagram)
* Screenshots (logic analyzer, serial output)
* Public code links (if available)

---

## How to Use This Template

1. Go to a project in **Project Index**
2. Review its linked **Sessions**
3. Extract:

   * Objectives → from early sessions
   * Challenges → from Blockers
   * Solutions → from What I did
   * Skills → from Skills used
4. Fill this template

Tip:

* Focus on **engineering decisions and problem-solving**, not just features
* Avoid including sensitive or proprietary information

---

# Progress Philosophy

Progress in embedded engineering should be measured by:

* Systems built

* Bugs solved

* Concepts understood

* Architecture designed

Rather than by time spent studying.

Small, consistent improvements accumulate into deep expertise over time.