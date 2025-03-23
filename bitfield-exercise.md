## Bit Field Exercise: Creating Bit-Field Structure for Peripheral Registers

### What is a Bit-Field?
A **bit-field** is a structure in C that allows us to allocate a specific number of bits for a variable, making it useful for working with hardware registers in embedded systems.

### Why Use Bit-Fields?
- Efficient memory usage
- Improves code readability
- Allows direct manipulation of hardware registers

### Defining a Bit-Field Structure
```c
#include <stdint.h>

// Example: Defining a bit-field structure for a 32-bit register
typedef struct {
    uint32_t bit0 : 1;
    uint32_t bit1 : 1;
    uint32_t bit2 : 1;
    uint32_t bit3 : 1;
    uint32_t reserved : 28;
} Register_t;

int main(void) {
    Register_t reg = {0}; // Initialize register
    reg.bit0 = 1;  // Set bit0
    reg.bit1 = 0;  // Clear bit1
    return 0;
}
```

## Bit-Field Structure for RCC_AHB1ENR
The **RCC_AHB1ENR** register in STM32 enables clocks for various peripherals.

### RCC_AHB1ENR Register Layout (32-bit)
| Bit Position | Peripheral    |
|-------------|--------------|
| 0           | GPIOAEN      |
| 1           | GPIOBEN      |
| 2           | GPIOCEN      |
| 3           | GPIODEN      |
| ...         | Reserved     |

### Bit-Field Structure for RCC_AHB1ENR
```c
#include <stdint.h>

typedef struct {
    uint32_t GPIOAEN : 1;
    uint32_t GPIOBEN : 1;
    uint32_t GPIOCEN : 1;
    uint32_t GPIODEN : 1;
    uint32_t reserved : 28;
} RCC_AHB1ENR_t;

#define RCC ((volatile RCC_AHB1ENR_t*)0x40023830) // Example memory address

int main(void) {
    RCC->GPIOAEN = 1; // Enable GPIOA clock
    return 0;
}
```

## Bit-Field Structure for GPIOx_ODR
The **GPIOx_ODR** register controls the output state of GPIO pins.

### GPIOx_ODR Register Layout
| Bit Position | GPIO Pin |
|-------------|---------|
| 0           | GPIOx_0 |
| 1           | GPIOx_1 |
| ...         | ...     |
| 15          | GPIOx_15 |
| 16-31       | Reserved |

### Bit-Field Structure for GPIOx_ODR
```c
#include <stdint.h>

typedef struct {
    uint32_t ODR0 : 1;
    uint32_t ODR1 : 1;
    uint32_t ODR2 : 1;
    uint32_t ODR3 : 1;
    uint32_t ODR4 : 1;
    uint32_t ODR5 : 1;
    uint32_t ODR6 : 1;
    uint32_t ODR7 : 1;
    uint32_t ODR8 : 1;
    uint32_t ODR9 : 1;
    uint32_t ODR10 : 1;
    uint32_t ODR11 : 1;
    uint32_t ODR12 : 1;
    uint32_t ODR13 : 1;
    uint32_t ODR14 : 1;
    uint32_t ODR15 : 1;
    uint32_t reserved : 16;
} GPIOx_ODR_t;

#define GPIO ((volatile GPIOx_ODR_t*)0x40020014) // Example memory address

int main(void) {
    GPIO->ODR5 = 1; // Set GPIO pin 5 HIGH
    return 0;
}
```

## Modifying LED Exercise with Structures and Bit Fields
### Goal:
Modify the LED exercise using bit-fields to control an LED connected to GPIOx_ODR.

### Code:
```c
#include <stdint.h>

// Define GPIO ODR register using bit-fields
typedef struct {
    uint32_t ODR0 : 1;
    uint32_t ODR1 : 1;
    uint32_t ODR2 : 1;
    uint32_t ODR3 : 1;
    uint32_t ODR4 : 1;
    uint32_t ODR5 : 1;
    uint32_t ODR6 : 1;
    uint32_t ODR7 : 1;
    uint32_t ODR8 : 1;
    uint32_t ODR9 : 1;
    uint32_t ODR10 : 1;
    uint32_t ODR11 : 1;
    uint32_t ODR12 : 1;
    uint32_t ODR13 : 1;
    uint32_t ODR14 : 1;
    uint32_t ODR15 : 1;
    uint32_t reserved : 16;
} GPIOx_ODR_t;

#define GPIO ((volatile GPIOx_ODR_t*)0x40020014) // Example memory address

void delay(void) {
    for (volatile uint32_t i = 0; i < 1000000; i++);
}

int main(void) {
    while (1) {
        GPIO->ODR5 = 1; // Turn on LED at GPIO5
        delay();
        GPIO->ODR5 = 0; // Turn off LED at GPIO5
        delay();
    }
    return 0;
}
```

## Summary
- **Bit-fields** allow us to define **peripheral registers** efficiently.
- The **RCC_AHB1ENR** register enables clocks for peripherals.
- The **GPIOx_ODR** register controls GPIO output state.
- Using **bit-fields**, we modified the **LED toggle program** for better readability and efficiency.

This method improves **embedded systems programming** by making register manipulation **more structured and readable**. 
