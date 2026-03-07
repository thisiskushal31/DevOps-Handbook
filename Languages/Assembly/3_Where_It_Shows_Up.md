# Assembly — Where it shows up: malware, shellcode, firmware, exploits

[← Assembly README](./README.md)

In security and DevOps you encounter assembly in **disassembler and debugger output**, in **shellcode** and **exploit payloads**, in **firmware** and **boot code**, and in **legacy or performance-critical** binaries. This topic summarizes those contexts; see **Further reading** for authoritative sources.

---

## Disassembly and debuggers

When you open a binary in a **disassembler** (IDA, Ghidra, Binary Ninja, objdump) or **debugger** (x64dbg, GDB, WinDbg), you see **assembly** (and often decompiled C-like code). The disassembler maps **machine code** back to **mnemonics and operands** using the CPU’s instruction set. That view is your primary way to reason about:

- What a function does (control flow, arithmetic, memory access).
- Where arguments and return values are (calling convention).
- Suspicious patterns (anti-debug, unpacking, shellcode).

You don’t need to write assembly daily, but **reading** it is essential for reverse engineering and malware analysis.

---

## Malware and implants

Many **malware families** and **implants** are written in C/C++ and compiled to native code; when you analyze them you see **x86/x64** or **ARM** assembly. Packed or obfuscated samples may contain:

- **Decryption/unpacking loops** — Arithmetic and memory operations in assembly.
- **API resolution** — Loading libraries and resolving function pointers (often via PEB/TEB on Windows).
- **Shellcode** — Small, position-independent assembly payloads (injected, in documents, or staged).

Understanding **calling conventions** and **common instruction sequences** helps you follow the logic and identify what the sample does without executing it.

---

## Shellcode and exploit payloads

**Shellcode** is typically **position-independent code** (PIC) in raw machine code (or assembly that assembles to it), often injected into a process or sent over the network. It is used in:

- **Exploit development** — Payload that runs after a buffer overflow or similar bug (e.g. open shell, add user).
- **Red-team tools** — In-memory execution, process injection, reflective loaders.

Shellcode is usually **small** and **avoids** null bytes (or other bad bytes) so it can be embedded in strings or packets. It often uses **system calls** (e.g. Linux `syscall`, Windows API via stack or shellcode-resolved pointers) rather than libc, so you see **direct syscall** or **API call** patterns in the assembly. References: exploit-db, OS-specific syscall/ABI docs, and security research papers.

---

## Firmware and boot code

**BIOS**, **UEFI**, **boot loaders**, and **embedded firmware** often contain hand-written or compiler-generated assembly for:

- **Early bootstrap** — CPU in real mode or early protected/long mode; no OS yet.
- **Low-level hardware** — Registers, interrupts, DMA.
- **Critical paths** — Where every cycle counts.

You may see **16-bit real mode** (segment:offset), **32-bit protected mode**, or **64-bit long mode** depending on the stage. Intel and AMD manuals describe the modes; UEFI and firmware specs describe the environment.

---

## Kernels and drivers

**OS kernels** and **device drivers** mix C with **assembly** for:

- **Trap/interrupt handlers** — Save/restore state, dispatch to C.
- **Context switch** — Save/restore registers and stack.
- **Atomic operations** — Compare-and-swap, barriers (often inline assembly in C).
- **CPU-specific** — CR0/CR4, MSRs, VMX/SVM.

When analyzing a kernel or driver binary, you will see these patterns in disassembly; the OS vendor’s source (e.g. Linux kernel, Windows WRK docs) and processor manuals are the references.

---

## Summary

| Context               | Typical architecture | What you see                          |
| --------------------- | -------------------- | ------------------------------------- |
| Desktop/server binary | x86-64               | Long mode; OS ABI (System V / MS x64) |
| Mobile / embedded     | ARM, AArch64         | AAPCS; possibly Thumb                 |
| Malware / shellcode   | x86-64, ARM          | PIC, syscalls, API calls              |
| Boot / firmware       | x86, ARM             | Real/protected mode; no OS ABI        |

---

## Further reading

- [Intel® 64 and IA-32 Architectures Software Developer Manual, Vol. 3](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html) — System programming (modes, interrupts, VMX).
- [ARM Documentation](https://developer.arm.com/documentation/) — Exception handling, boot, secure state.
- OS and ABI docs (Linux, Windows, macOS) for syscall numbers and calling conventions used in shellcode and malware analysis.
