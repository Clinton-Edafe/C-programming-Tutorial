## Memory Map of STM32 MCU

### Memory Map of the Microcontroller
The memory map of an STM32 microcontroller can be found in the datasheet or reference manual of the specific MCU model. The STM32F4xx devices have a structured memory map that is essential for understanding how peripherals and memory are accessed.

### Memory Usage and Details
The memory address range is divided into several sections, each serving a different purpose.

| Address Range | General Use | Details & Description |
|--------------|------------|-----------------------|
| 0x00000000 - 0x1FFFFFFF | Code Memory | Flash memory and boot ROM |
| 0x20000000 - 0x3FFFFFFF | Data Memory | RAM used for program execution |
| 0x40000000 - 0x5FFFFFFF | Peripheral Registers | Used to control hardware peripherals |
| 0x60000000 - 0x9FFFFFFF | External Memory | External RAM or Flash |

### Address Range of GPIOD Peripheral Registers
GPIOD is mapped within the peripheral register space. The base address for GPIOD in STM32F4xx microcontrollers is typically **0x40020C00**.

---
## Peripheral Registers in STM32 MCUs

- All peripheral registers in STM32 microcontrollers are **32 bits wide**.
- Different peripherals have a **different number of registers**.
- You should **never assume** the address of peripheral registers. Always refer to the reference manual.

### GPIOD Peripheral Registers List and Explanation
| Register | Address Offset | Description |
|----------|---------------|-------------|
| MODER | 0x00 | GPIO Mode Register (input, output, alternate function, analog) |
| OTYPER | 0x04 | Output type register (push-pull or open-drain) |
| OSPEEDR | 0x08 | Output speed register (low, medium, high, very high) |
| PUPDR | 0x0C | Pull-up/pull-down register |
| IDR | 0x10 | Input data register (read pin state) |
| ODR | 0x14 | Output data register (write to pin) |
| BSRR | 0x18 | Bit set/reset register (atomic bit operations) |
| LCKR | 0x1C | Lock register (prevents accidental modifications) |
| AFRL | 0x20 | Alternate function low register |
| AFRH | 0x24 | Alternate function high register |

---
## Procedure to Turn on an LED (Newbie Guide)
Turning on an LED in an embedded system requires knowledge of the **memory map**, **peripheral registers**, and **hardware connections**.

### Steps to Turn on the LED

1. **Identify the GPIO port (a peripheral) used to connect the LED (GPIOD)**
2. **Identify the GPIOD pin where the LED is connected**
3. **Activate the GPIOD peripheral (Enable the clock)**
   - Until you enable the clock for a peripheral, it remains inactive.
   - Activating the clock makes the peripheral ready for configuration.
   - Some microcontrollers have peripherals **enabled by default** (refer to the datasheet).
4. **Configure the GPIOD pin mode as output**
5. **Write to the GPIO pin to turn on the LED**

### Practical Example in Embedded C
```c
#include "stm32f4xx.h"  // Include the STM32F4xx standard peripheral library

void LED_Init(void) {
    // Enable clock for GPIOD (bit 3 of AHB1ENR register)
    RCC->AHB1ENR |= (1 << 3);

    // Set GPIOD Pin 12 as output mode
    GPIOD->MODER &= ~(3 << (12 * 2)); // Clear previous mode
    GPIOD->MODER |= (1 << (12 * 2));  // Set mode to output
}

void LED_On(void) {
    GPIOD->ODR |= (1 << 12);  // Set Pin 12 high (turn on LED)
}

int main(void) {
    LED_Init();  // Initialize LED
    while(1) {
        LED_On();  // Turn LED on
    }
}
```

### Explanation:
- `RCC->AHB1ENR |= (1 << 3);` → Enables the clock for **GPIOD**
- `GPIOD->MODER |= (1 << (12 * 2));` → Configures **Pin 12 as output**
- `GPIOD->ODR |= (1 << 12);` → Writes **1 to Pin 12 to turn on the LED**

Final Thought: By following this structured approach, a beginner can understand the memory-mapped peripheral registers and control GPIOs effectively.
