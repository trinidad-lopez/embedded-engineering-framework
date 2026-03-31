# Embedded Engineer Growth – Debugging Playbook

This document is intended to be a **living debugging notebook**. It should grow over time as you encounter real problems, investigate them, and learn new debugging techniques.

The purpose is to capture:

* Debugging strategies
* Common failure patterns
* Tools and workflows
* Lessons learned from real bugs

Unlike a normal guide, this document should be **actively updated during your career** whenever you solve difficult problems.

---

# How to Use This Playbook

Whenever you encounter a difficult bug, record:

1. **Problem description**
2. **System context**
3. **Initial hypotheses**
4. **Tests performed**
5. **Root cause**
6. **Solution implemented**
7. **Lessons learned**

Example template:

```
Bug Title:

System:

Symptoms:

Initial Hypothesis:

Debugging Steps:

Root Cause:

Solution:

Lessons Learned:
```

Over time this becomes a **personal knowledge base of real debugging experience**.

---

# Core Debugging Principles

## Change Only One Variable

When debugging, modify only one element at a time. Multiple simultaneous changes make it impossible to determine the real cause of a problem.

---

## Reproduce the Bug Reliably

Before attempting to fix a problem, try to create a **reliable reproduction method**.

Questions to ask:

* Does the bug happen every time?
* Does it require a specific timing condition?
* Does it depend on startup order?

---

## Trust the Hardware Signals

If software logs and hardware measurements disagree, the hardware is usually correct.

Always verify behavior with:

* Oscilloscope
* Logic analyzer
* GPIO debug pins

---

## Simplify the System

Reduce complexity until the failure disappears.

Example techniques:

* Disable peripherals
* Remove interrupts
* Replace drivers with stubs

The smallest failing configuration often reveals the problem.

---

# Common Embedded Failure Categories

This section lists typical embedded system problems.

---

## Interrupt Issues

Common problems:

* Interrupt not enabled
* Wrong interrupt vector
* ISR execution too long
* Race conditions with main loop

Debugging techniques:

* Toggle GPIO at ISR entry
* Measure interrupt frequency
* Check interrupt priorities

---

## DMA Problems

Common problems:

* Incorrect memory alignment
* Buffer overwritten before transfer complete
* DMA interrupt not handled

Debugging techniques:

* Use small buffers first
* Validate transfer size
* Monitor DMA status registers

---

## Memory Corruption

Common causes:

* Stack overflow
* Out-of-bounds array access
* Incorrect pointer arithmetic

Debugging techniques:

* Add stack guards
* Use static buffers
* Enable compiler warnings

---

## Timing Bugs

Common causes:

* Blocking delays
* Interrupt latency
* Priority inversion

Debugging techniques:

* Use GPIO timing markers
* Measure execution time
* Use cycle counters

---

# Hardware Debugging Tools

## Oscilloscope

Used to verify electrical signals, timing relationships, and waveform integrity.

---

## Logic Analyzer

Useful for digital protocols such as:

* SPI
* I2C
* UART

Allows visualization of communication frames.

---

## JTAG / SWD Debugger

Capabilities:

* Breakpoints
* Register inspection
* Memory inspection

---

# Software Debugging Techniques

## Strategic Logging

Add logs around critical events:

* Interrupt entry
* Peripheral configuration
* Protocol events

Avoid excessive logging in time-critical sections.

---

## Debug GPIO Pins

Toggle GPIO pins at critical points in code to observe behavior with a logic analyzer.

Example uses:

* ISR entry/exit
* Task execution timing
* Protocol state changes

---

## Binary Search Debugging

Disable half the system and test again.

If the bug disappears, the issue is in the disabled half.

Repeat until the faulty module is isolated.

---

# Debugging Checklists

## When Firmware Does Not Start

Check:

* Clock configuration
* Vector table location
* Stack pointer initialization
* Peripheral clocks enabled

---

## When Communication Fails

Check:

* Clock polarity and phase
* Baud rate configuration
* Wiring integrity
* Device addressing

---

## When System Crashes

Check:

* Stack overflow
* Null pointer dereference
* Hard fault registers
* Memory boundaries

---

# Personal Debugging Cases

This section should grow over time.

Document real bugs encountered in projects.

---

## Case 1 – (Example Placeholder)

Problem:

System:

Symptoms:

Investigation:

Root Cause:

Solution:

Lessons Learned:

---

# Long-Term Goal

Over time, this playbook should become a **personal debugging handbook** containing real problems you solved. Experienced embedded engineers rely heavily on this type of accumulated knowledge.

The most valuable insights often come from **difficult bugs that took hours or days to understand**.