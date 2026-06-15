# API vs ABI

Status: reviewed
Related skills: C interfaces, library design, firmware architecture, build systems
Related projects: Circular Buffer, Peripheral Driver Library, Custom Embedded Build System

## Short Explanation

API means Application Programming Interface. It is the source-level contract that other code uses: function names, parameters, return values, header files, documented behavior, and expected usage.

ABI means Application Binary Interface. It is the binary-level contract that compiled code depends on: calling convention, symbol names, struct layout, enum sizes, alignment, padding, object file format, and linker-visible behavior.

An API can remain the same while the ABI changes. That means source code may still compile cleanly, but already-compiled objects or libraries may no longer link or run correctly.

## Why It Matters

Embedded projects often mix source code, static libraries, vendor HALs, bootloaders, RTOS ports, startup files, and compiler-specific build settings. ABI mismatches can create failures that do not look like normal source-code bugs.

Examples:

- A struct shared between firmware modules changes layout.
- A compiler option changes enum size or alignment.
- A function signature changes in a header, but one object file was not rebuilt.
- A bootloader and application disagree on a function table or shared memory layout.
- A precompiled vendor library expects a different calling convention or floating-point ABI.

## Example

API-level change:

```c
int buffer_push(struct ring_buffer *buffer, uint8_t value);
```

If this function changes to return a status enum, source users must update their code. That is an API change.

ABI-level change:

```c
struct ring_buffer {
    uint8_t *data;
    uint16_t capacity;
    uint16_t head;
    uint16_t tail;
};
```

If this struct is shared across compiled modules and a new field is inserted in the middle, the binary layout changes. Code compiled against the old layout may read the wrong fields even if the source-level name `struct ring_buffer` still exists.

## Common Pitfalls

- Assuming a successful compile means binary compatibility is preserved.
- Changing public struct layout without rebuilding every dependent object.
- Mixing object files built with different compiler flags.
- Exposing internal structs in public headers when an opaque handle would be safer.
- Treating a bootloader/application shared interface as just normal C code instead of a binary contract.
- Forgetting that ABI stability matters more when distributing precompiled libraries or separating firmware images.

## Practical Rule

If every dependent module is rebuilt from source with the same toolchain settings, API compatibility is usually the main concern.

If any dependent module is already compiled, separately linked, shared across firmware images, or supplied by a vendor, ABI compatibility becomes a first-class concern.

## Open Questions

- Which compiler flags most commonly affect ABI on ARM Cortex-M projects?
- How should bootloader/application shared interfaces be versioned?
- When should embedded C modules use opaque structs to reduce ABI risk?

## References

- C headers and compiler documentation for the active toolchain
- Linker map files and object symbol tables
- Vendor library ABI notes when using precompiled libraries

