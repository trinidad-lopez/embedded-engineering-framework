# Project Brief

## Circular Buffer (Ring Buffer)

Status: scoped
Scale: quick
Related skills: C pointers, memory layout, data structures, API design, unit testing, API vs ABI

## Problem / Motivation

A circular buffer is a small but important embedded data structure. It appears in UART receive buffers, telemetry queues, producer/consumer paths, logging systems, and interrupt-to-main-loop handoff.

The goal is to build a reusable C ring buffer module with a clear API, predictable behavior, and tests that expose boundary conditions.

## Expected Outcome

A small C module that supports byte-oriented push/pop operations with explicit overflow and empty-buffer behavior.

Expected artifacts:

- public header
- implementation file
- test file or simple test runner
- short design notes
- session log after implementation

## Minimum Useful Version

Implement:

- fixed-size caller-owned storage
- initialization from external buffer memory
- push one byte
- pop one byte
- check empty/full
- get current count and capacity
- deterministic overflow behavior

Do not use dynamic allocation in the minimum version.

## Stretch Goals

- generic element-size support
- bulk push/pop
- interrupt-safe usage notes
- lock-free single-producer/single-consumer variant notes
- compile-time configuration option
- benchmark or cycle-count notes on target hardware

## Validation

Minimum tests:

- initialized buffer starts empty
- push then pop returns the same value
- FIFO order is preserved
- full condition is detected
- empty condition is detected
- wraparound preserves order
- overflow behavior is explicit and tested
- invalid initialization is rejected or documented

Manual review:

- public API is clear enough to use without reading implementation
- ownership of storage is obvious
- no hidden dynamic allocation
- behavior is deterministic at boundaries

## Notes

This project is a good first test of the framework because it connects:

- roadmap project scoping
- concept notes such as API vs ABI
- session logging
- future debugging cases
- portfolio extraction if implemented cleanly

Potential next action:

```text
Create projects/active/circular-buffer/ when implementation starts.
```

