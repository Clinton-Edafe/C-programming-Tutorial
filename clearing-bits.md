## Clearing of Bits

### Exercise: Clearing of Bits
- Write a program to clear (make bit state to 0) 4th, 5th, 6th bit positions of a given number and print the result.
- `&` is used to 'TEST' and 'CLEAR' but not to 'SET'.
- `|` is used to 'SET' but not to 'TEST'.

### Code Example:
```c
#include <stdio.h>

int main() {
    unsigned int num, result;
    printf("Enter a number: ");
    scanf("%u", &num);
    
    // Clearing 4th, 5th, and 6th bits (bit positions 3, 4, and 5 in 0-based indexing)
    result = num & ~( (1 << 3) | (1 << 4) | (1 << 5) );
    
    printf("Number after clearing 4th, 5th, and 6th bits: %u\n", result);
    return 0;
}
```

---

## Applicability of Bitwise Operators: XOR

### Toggling of Bits
- **XOR (`^`) is used for toggling bits.**
- Toggling means flipping the state of a bit (0 → 1, 1 → 0).
- It is widely used in embedded systems to control hardware components like LEDs.

### Exercise: Toggling of Bits
- Write a program to turn on the LED of your target board.
- For this exercise, knowledge of the following is required:
  - Pointers
  - Bitwise Operations
  - Hardware Connections

### Hardware Connections
- Let's understand how an external hardware (LED) is connected to the STM32 MCU.
- Assume the LED is connected to **GPIO Pin 5**.

### Code Example:
```c
#include <stdint.h>
#include "stm32f4xx.h"  // Replace with appropriate header for your MCU

#define LED_PIN 5  // Assuming LED is connected to pin 5
#define GPIO_PORT GPIOA // Assuming LED is on port A

void toggle_led() {
    GPIO_PORT->ODR ^= (1 << LED_PIN);  // Toggle LED using XOR
}

int main() {
    // Configure GPIO pin as output
    RCC->AHB1ENR |= (1 << 0);  // Enable clock for GPIOA
    GPIO_PORT->MODER |= (1 << (LED_PIN * 2));  // Set LED_PIN as output
    
    while (1) {
        toggle_led();  // Toggle LED
        for (volatile int i = 0; i < 1000000; i++);  // Delay loop
    }
}
```

### Explanation:
1. The program enables the clock for **GPIOA**.
2. It configures **Pin 5** as an output.
3. The `toggle_led()` function flips the state of the LED using **XOR (`^`)**.
4. Inside `main()`, the LED toggles continuously with a delay.

This is how bitwise operations help in embedded systems programming!

---
