# Disassembly and Manipulating Decimal Numbers in C

## 🔍 What is Disassembly?
Disassembly is the process of **translating machine code** (binary instructions) back into **human-readable assembly language** or a **higher-level programming language** like C.

### Why is Disassembly Important?
- Helps developers **debug** compiled code at the machine level.
- Allows analysis of the **actual execution flow** on the processor.
- Useful in **reverse engineering** and **performance optimization**.

---

## 💡 Processor Architecture and Instruction Set

### 🔹 Processor: **ARM Cortex-M4**
- The ARM Cortex-M4 is a **32-bit RISC processor** widely used in **embedded systems**.
- It is optimized for **low-power** and **high-efficiency** applications.

### 🔹 Processor Architecture: **ARMv7E-M**
- **ARMv7E-M** is an **extension** of the ARMv7-M architecture.
- It includes **DSP (Digital Signal Processing) enhancements**, making it suitable for **real-time applications**.

### 🔹 Instruction Set Architecture (ISA): **Thumb-2 Instruction Set**
- The **Thumb-2 ISA** supports **both 16-bit and 32-bit instructions**.
- It provides a **balance between performance and code density**.
- **Advantages:**
  - **Efficient memory usage** (compact 16-bit instructions).
  - **Power-efficient** execution for embedded systems.

---

## ⚙️ Disassembly Example: ARM Cortex-M4 Assembly Code

```assembly
    MOV R0, #10      ; Load immediate value 10 into register R0
    MOV R1, #20      ; Load immediate value 20 into register R1
    ADD R2, R0, R1   ; Add R0 and R1, store the result in R2
    BX  LR           ; Return from the function
