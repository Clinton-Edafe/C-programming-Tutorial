# Controlling IO Pin Using Software

In embedded systems, IO pins are controlled using peripheral registers that are mapped onto processor addressable memory locations. This means the registers can be accessed through memory addresses, making them memory-mapped registers.

## Accessing Peripheral Registers
Peripheral registers are accessed using their memory-mapped addresses. Since the processor can directly read and write to these addresses, IO control is achieved via software by modifying register values.

### Key Points:
- IO pins are controlled using peripheral registers.
- These registers are mapped onto processor addressable memory locations.
- The processor accesses these registers using memory addresses.

## Processor Addressable Memory Locations
Since the address bus width is 32 bits, the processor can address memory locations in the range:
```
0x0000_0000 to 0xFFFF_FFFF
```
This 4GB address space includes:
- **Program Memory** (Code Memory)
- **Data Memory**
- **Registers of various peripherals** (GPIO, TIMERS, ADC, I2C, etc.)

This is a generic memory map structure that must be followed by all MCUs using the ARM Cortex-Mx processor.

## ARM Cortex-M4 Memory Map & Peripherals
Below is a labeled diagram illustrating the processor addressable memory locations and connections:

```plaintext
---------------------------------------------------
|  0x0000_0000  |        Code Memory (Flash)       |
|               |  Stores Program Instructions    |
---------------------------------------------------
|  0x2000_0000  |        Data Memory (RAM)        |
|               |  Stores Global/Stack Variables  |
---------------------------------------------------
|  0x4000_0000  |     Peripheral Registers        |
|               | GPIO, TIMERS, ADC, I2C, UART    |
---------------------------------------------------
|  0xE000_0000  |     System Control Registers    |
|               | NVIC, SysTick, Debug Registers  |
---------------------------------------------------
```

### Explanation:
1. **Code Memory (Flash Memory - 0x0000_0000)**
   - Stores the firmware/program code.
   - Read-only during execution.
2. **Data Memory (RAM - 0x2000_0000)**
   - Stores variables, stack, and heap.
   - Read/Write memory accessible by the CPU.
3. **Peripheral Registers (0x4000_0000)**
   - Contains memory-mapped registers for GPIO, TIMERS, ADC, I2C, UART, etc.
   - Each peripheral has a fixed memory address range.
4. **System Control Registers (0xE000_0000)**
   - Includes NVIC (Nested Vectored Interrupt Controller), SysTick Timer, and Debugging Registers.

This structure provides efficient control over the peripherals while maintaining a unified memory architecture.
