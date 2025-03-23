# For Loop in C

## Definition
A `for` loop is a control flow statement used in programming to repeatedly execute a block of code based on a condition. The syntax of a `for` loop consists of three parts:

```c
for(initialization; condition; update)
{
    // Loop body
}
```
- **Initialization**: The loop control variable is initialized.
- **Condition**: The loop runs as long as this condition is true.
- **Update**: The control variable is updated after each iteration.

## Flow Chart of a `for` Loop

```plaintext
+------------------+
| Initialization   |
+------------------+
         |
         v
+------------------+
| Condition check? |
+------------------+
       /   \
      /yes  \no
     v       v
+------------------+    +------------------+
| Execute Loop    | -> | Exit Loop         |
| Body            |    | Continue Program  |
+------------------+    +------------------+
         |
         v
+------------------+
| Update Counter  |
+------------------+
         |
         v
   Loop Back to Condition Check
```

## Converting While Loop Exercise to For Loop
### Printing numbers from 1 to 10 using `for` loop

```c
#include <stdio.h>

int main(void) {
    for (int num = 1; num <= 10; num++) {
        printf("%d\n", num);
    }
    return 0;
}
```

## For Loop Number Pyramid Exercise

```c
#include <stdio.h>

int main(void) {
    int rows = 5;
    
    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= i; j++) {
            printf("%d ", j);
        }
        printf("\n");
    }
    return 0;
}
```

## LED Toggle Program with Software Delay

### Introducing Delay in Programs
- **Software Delay**: Uses loops to create a delay but is not precise.
- **Hardware Delay**: Uses microcontroller timers for accurate delays.

### Implementing Software Delay

```c
#include "stm32f4xx.h"  // Include STM32F4 header file

void delay(void) {
    for (volatile int i = 0; i < 1000000; i++);
}

int main(void) {
    RCC->AHB1ENR |= (1 << 3);  // Enable clock for GPIOD
    GPIOD->MODER |= (1 << (2 * 12));  // Set Pin 12 as output

    while (1) {
        GPIOD->ODR ^= (1 << 12);  // Toggle LED
        delay();  // Software delay
    }
}
```

### Explanation
- The **`delay()`** function introduces a simple delay using a loop.
- The **while(1) loop** ensures the LED toggles continuously.
- **Bitwise XOR (`^=`)** is used to toggle the LED state.

This implementation makes the LED blink with a basic software delay.
