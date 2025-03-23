# Type of Qualifiers in 'C'

## 1. `const` Qualifier

### Definition:
The `const` keyword in C is used to declare variables whose values cannot be changed after initialization. It tells the compiler that the variable is read-only.

### Syntax:
```c
const int max_value = 100;
```

### Explanation:
- Once assigned, the value of `max_value` cannot be modified.
- Any attempt to change `max_value` will result in a compilation error.

### Example:
```c
#include <stdio.h>

int main() {
    const float pi = 3.14159;
    printf("Value of pi: %f\n", pi);
    // pi = 3.14; // This will cause an error
    return 0;
}
```

## 2. `volatile` Qualifier

### Definition:
The `volatile` keyword is used for variables that can be changed unexpectedly, such as hardware registers, shared memory in multi-threaded programs, or interrupt service routines (ISRs).

### Syntax:
```c
volatile int sensor_value;
```

### Explanation:
- Tells the compiler not to optimize the variable since its value may change at any time.
- Useful when working with hardware registers or shared memory.

### Example:
```c
#include <stdio.h>

volatile int flag = 0; // Shared variable modified by ISR

void ISR() {
    flag = 1; // Flag modified by interrupt
}

int main() {
    while (!flag) {
        // Wait until flag changes
    }
    printf("Flag changed!\n");
    return 0;
}
```

---

# Placement of `const` Variables in Memory

### RAM Placement (Local `const` Variables):
- Local `const` variables behave like normal variables and are stored in RAM.
- Example:
  ```c
  void function() {
      const int local_const = 10; // Stored in RAM
  }
  ```

### Flash Memory Placement (Global `const` Variables in STM32):
- In STM32 microcontrollers, global `const` variables are stored in flash memory.
- Flash memory is write-protected, so modifying `const` variables through pointers has no effect.
- Example:
  ```c
  #include <stdio.h>

  const int global_const = 50; // Stored in Flash

  int main() {
      printf("Value: %d\n", global_const);
      return 0;
  }
  ```

- Trying to modify `global_const` via its address will not work:
  ```c
  int *ptr = (int*)&global_const;
  *ptr = 100; // Has no effect on STM32 hardware
  ```

### Summary:
| Variable Type      | Memory Location |
|--------------------|----------------|
| Local `const`     | RAM             |
| Global `const`    | Flash Memory    |
| Non-`const`       | RAM             |

This ensures that firmware stored in flash remains protected while RAM is used for temporary and changeable data.
