# Analyzing Embedded C Program

## What is a Microcontroller?
A **Microcontroller (MCU, uC)** is a small computer system on a single chip. However, its resources are much more limited than those of a desktop computer because MCUs are designed specifically for embedded applications.

### Anatomy of a Microcontroller
A typical microcontroller consists of:
- **Processor (CPU)**
- **Volatile and Non-Volatile Memories**
- **Input/Output (I/O) Pins**
- **Peripherals**
- **Clocks**
- **Bus Interfaces**

Below is a diagram illustrating the structure of a microcontroller:

```mermaid
graph TD;
  Clock -->|Syncs| CPU;
  CPU -->|Executes| Address_Bus;
  Address_Bus -->|Fetches| Program_Memory(Flash);
  Program_Memory(Flash) -->|Stores Instructions| CPU;
  CPU -->|Processes| Data_Memory(SRAM);
  Data_Memory(SRAM) -->|Stores Data| CPU;
  CPU -->|Controls| Control_Bus;
  Control_Bus -->|Manages| I/O;
  I/O -->|Interacts with| Peripherals;
  Peripherals -->|Includes| {ADC, DAC, Timers, UART, USB};
```

## Identifying Code and Data Parts of the Program
A microcontroller program is split into two key parts:
1. **Code Memory:** Stores the program instructions (non-volatile, typically Flash memory).
2. **Data Memory:** Stores variables and runtime data (volatile, typically SRAM).

### Code Memory (Flash)
- Used for storing program instructions.
- Non-volatile (retains data after power off).

### Data Memory (SRAM)
- Stores program variables and runtime data.
- Volatile (loses data when power is lost).
- Often acts as a scratchpad during execution.

**Example:** An MCU receiving data from Bluetooth and storing it in data memory.

## Disassembly Feature of the IDE
Disassembly is used to examine how C code translates into assembly instructions. This feature is available in IDEs such as **STM32CubeIDE** and **Keil uVision**.

## Analyzing the Executable (.elf) using GNU Tools
### GNU Tools for Analysis:
1. **objdump** - Disassembles and examines binary files.
2. **size** - Reports the sizes of text, data, and BSS sections in the executable.

### Example Usage:
```sh
arm-none-eabi-objdump -D program.elf > disassembly.txt
arm-none-eabi-size program.elf
```

### Sample Output:
```sh
   text    data     bss     dec     hex filename
   1024     256      64    1344     540 program.elf
```
- **Text:** Stores the program instructions.
- **Data:** Stores initialized global and static variables.
- **BSS:** Stores uninitialized global and static variables.

## Summary
- **Code Memory (Flash):** Stores program instructions.
- **Data Memory (SRAM):** Stores program data during runtime.
- **GNU Tools:** Help analyze executable files.
- **Disassembly:** Converts machine code into assembly instructions.

