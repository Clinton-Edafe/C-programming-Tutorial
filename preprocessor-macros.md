# Pre-Processor Directives in 'C'

## Introduction
Pre-processor directives in C are commands that are executed before the actual compilation of the program begins. They instruct the compiler to perform specific tasks like file inclusion, macro definition, and conditional compilation.

## Common Pre-Processor Directives

1. **File Inclusion (`#include`)**: Includes header files.
   ```c
   #include <stdio.h> // Standard Input Output Library
   #include "myheader.h" // User-defined header file
   ```

2. **Macro Definition (`#define`)**: Defines constants or inline functions.
   ```c
   #define PI 3.14159
   #define SQUARE(x) ((x) * (x))
   ```

3. **Conditional Compilation (`#ifdef`, `#ifndef`, `#if`, `#else`, `#elif`, `#endif`)**: Compiles specific code based on conditions.
   ```c
   #ifdef DEBUG
   printf("Debug mode enabled\n");
   #endif
   ```

4. **Pragma Directives (`#pragma`)**: Compiler-specific instructions.
   ```c
   #pragma once  // Prevents multiple inclusion of a header file
   ```

---

# Macros in 'C' (`#define`)

Macros are used to define constants and inline functions.

## Defining Macros
```c
#define MAX_SIZE 100
#define AREA(length, breadth) ((length) * (breadth))
```

## Use Cases of Macros
- **Avoid magic numbers**: 
  ```c
  #define TAX_RATE 0.18
  float tax = price * TAX_RATE;
  ```
- **Shorten repetitive code**:
  ```c
  #define PRINT_MSG printf("Hello, World!\n")
  ```

## Best Practices While Writing Macros
- Use parentheses for safety:
  ```c
  #define MULTIPLY(x, y) ((x) * (y))
  ```
- Use `const` when possible instead of macros for type safety.
- Avoid side effects like modifying function arguments inside macros.

---

# Conditional Compilation in 'C'

Conditional compilation allows compiling specific parts of code based on conditions.

### `#if` and `defined` Operator

```c
#if defined(ENABLE_FEATURE)
   printf("Feature Enabled\n");
#endif
```

---

# Modifying LED Toggle Exercise with Macros

### Original Code:
```c
void toggleLED() {
    digitalWrite(LED_PIN, HIGH);
    delay(1000);
    digitalWrite(LED_PIN, LOW);
    delay(1000);
}
```

### Using Macros:
```c
#define LED_ON digitalWrite(LED_PIN, HIGH)
#define LED_OFF digitalWrite(LED_PIN, LOW)
#define DELAY_TIME 1000

void toggleLED() {
    LED_ON;
    delay(DELAY_TIME);
    LED_OFF;
    delay(DELAY_TIME);
}
```

Food thought: Using macros makes the code more readable and maintainable.
