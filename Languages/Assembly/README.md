# Assembly

[← Back to Languages](../README.md)

**Why in security:** **Reverse engineering**, **malware analysis**, and **exploit development** often require reading or writing assembly. Disassemblers and debuggers (IDA, Ghidra, x64dbg, radare2) show code as assembly; shellcode and payloads are written in it. You don’t need to be fluent, but recognizing instructions, calling conventions, and structure is essential.

**Relevance:** x86/x64 (Intel/AMD), ARM (including ARM64), and sometimes MIPS appear in malware and embedded targets. Understanding stack layout, registers, and common patterns helps with binary analysis and vulnerability research.

**Format:** Each concept is explained in text first, then illustrated with a **code block** or table where useful. Content is referenced from official or widely used sources; see **Further reading** in each topic and below.

---

## Topics

| # | Topic | File |
| --- | --- | --- |
| 1 | Basics: registers, instructions, addressing (x86/x64 and ARM) | [1_Basics_Registers_And_Instructions.md](./1_Basics_Registers_And_Instructions.md) |
| 2 | Reading disassembly and calling conventions | [2_Reading_Disassembly_And_Calling_Conventions.md](./2_Reading_Disassembly_And_Calling_Conventions.md) |
| 3 | Where it shows up: malware, shellcode, firmware, exploits | [3_Where_It_Shows_Up.md](./3_Where_It_Shows_Up.md) |
| 4 | Tooling: disassemblers, debuggers, and how they present assembly | [4_Tooling.md](./4_Tooling.md) |
| 5 | Environment, basic syntax, and program structure | [5_Environment_Syntax_And_Program_Structure.md](./5_Environment_Syntax_And_Program_Structure.md) |
| 6 | Registers, flags, and Linux system calls | [6_Registers_Flags_And_System_Calls.md](./6_Registers_Flags_And_System_Calls.md) |
| 7 | Addressing modes, variables, and constants | [7_Addressing_Variables_Constants.md](./7_Addressing_Variables_Constants.md) |
| 8 | Arithmetic, logical, and control-flow instructions | [8_Arithmetic_Logical_And_Control_Flow.md](./8_Arithmetic_Logical_And_Control_Flow.md) |
| 9 | Procedures, stack, and macros | [9_Procedures_Stack_And_Macros.md](./9_Procedures_Stack_And_Macros.md) |
| 10 | Numbers, strings, and arrays | [10_Numbers_Strings_And_Arrays.md](./10_Numbers_Strings_And_Arrays.md) |
| 11 | Recursion, file and memory management | [11_Recursion_File_And_Memory_Management.md](./11_Recursion_File_And_Memory_Management.md) |
| 12 | Use cases, ecosystem, and online tools | [12_Use_Cases_Ecosystem_And_Online_Tools.md](./12_Use_Cases_Ecosystem_And_Online_Tools.md) |

---

## Further reading

- [Assembly Programming Tutorial (TutorialsPoint)](https://www.tutorialspoint.com/assembly_programming/index.htm) — Full course; all chapter links have been scraped and merged into topics 5–11.
- [Assembly Quick Guide (TutorialsPoint)](https://www.tutorialspoint.com/assembly_programming/assembly_quick_guide.htm) — Summary reference.
- [Assembly Useful Resources (TutorialsPoint)](https://www.tutorialspoint.com/assembly_programming/assembly_useful_resources.htm) — Links and references.
- [Online Assembly (NASM) Compiler (TutorialsPoint CodeGround)](https://www.tutorialspoint.com/compilers/online-assembly-compiler.htm) — Write, run, and debug NASM in the browser.
- [Online Yasm Compiler (TutorialsPoint CodeGround)](https://www.tutorialspoint.com/compilers/online-yasm-compiler.htm) — NASM-compatible assembly in the browser.
- [C Programming Tutorial (TutorialsPoint)](https://www.tutorialspoint.com/cprogramming/index.htm) — C and system programming; relationship to assembly and assemblers.
- [Ethical Hacking Tutorial (TutorialsPoint)](https://www.tutorialspoint.com/ethical_hacking/index.htm) — Security context where assembly and reverse engineering are used.
- [x86 assembly language (Wikipedia)](https://en.wikipedia.org/wiki/X86_assembly_language)
- [Intel® 64 and IA-32 Architectures Software Developer Manuals](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html)
- [NASM Manual](https://www.nasm.us/doc/) — x86/x64 assembler syntax and directives
- [ARM Documentation](https://developer.arm.com/documentation/)
- [Ghidra](https://ghidra-sre.org/), [IDA Pro](https://hex-rays.com/ida-pro/), [radare2](https://rada.re/n/)
