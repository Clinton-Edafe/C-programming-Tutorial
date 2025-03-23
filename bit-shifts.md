## Bitwise Shift Operators in Embedded C

### Bitwise Right Shift Operator (`>>`)
The **right shift operator** shifts the bits of a number to the right by a specified number of positions. Each shift operation effectively divides the number by 2.

#### Syntax:
```c
number >> n;
```
This moves all bits `n` positions to the right.

#### Example:
```c
#include <stdio.h>

int main() {
    unsigned int num = 8; // Binary: 00001000
    printf("num >> 1: %d\n", num >> 1); // 00000100 -> 4
    printf("num >> 2: %d\n", num >> 2); // 00000010 -> 2
    return 0;
}
```

#### Application in Embedded Systems:
- Used to extract particular bits from a register.
- Efficient division by powers of 2.

---

### Bitwise Left Shift Operator (`<<`)
The **left shift operator** shifts bits to the left, effectively multiplying the number by 2 for each shift.

#### Syntax:
```c
number << n;
```
This moves all bits `n` positions to the left.

#### Example:
```c
#include <stdio.h>

int main() {
    unsigned int num = 3; // Binary: 00000011
    printf("num << 1: %d\n", num << 1); // 00000110 -> 6
    printf("num << 2: %d\n", num << 2); // 00001100 -> 12
    return 0;
}
```

#### Application in Embedded Systems:
- Used for quick multiplication by powers of 2.
- Efficient bit manipulation for setting flags or registers.

---

## Applicability of Bitwise Shift Operators
1. **Setting specific bits** in microcontroller registers.
2. **Reading and modifying individual bits** of a hardware register.
3. **Multiplication and division** by powers of 2.
4. **Extracting fields** from bit-mapped registers.

---

## Modifying LED ON Exercise Using Bitwise Shift Operators

```c
#include "stm32f4xx.h"

int main(void) {
    // 1. Enable the clock for GPIOD
    RCC->AHB1ENR |= (1 << 3); // Enable GPIOD peripheral clock
    
    // 2. Configure the pin as output
    GPIOD->MODER |= (1 << (2 * 12)); // Set PD12 as output (LED pin)
    
    while (1) {
        // 3. Turn ON LED using left shift
        GPIOD->ODR |= (1 << 12); // Set bit 12
        
        for (volatile int i = 0; i < 500000; i++); // Delay
        
        // 4. Turn OFF LED using left shift
        GPIOD->ODR &= ~(1 << 12); // Clear bit 12
        
        for (volatile int i = 0; i < 500000; i++); // Delay
    }
}
```

---

## Bit Extraction
Bit extraction is used to **isolate specific bits** from a register or variable.

### Extracting the 5th bit of a number:
```c
#include <stdio.h>

int main() {
    unsigned int num = 0b00101100; // Example number
    int bit5 = (num >> 5) & 1; // Extract the 5th bit
    printf("The 5th bit is: %d\n", bit5);
    return 0;
}
```

### Practical Applications:
1. **Checking flags** in microcontroller registers.
2. **Extracting sensor status bits** in embedded systems.
3. **Optimized data compression and transmission.**

---

This guide provides the fundamental understanding and practical applications of **bitwise shift operations** and their significance in **embedded systems programming**.
