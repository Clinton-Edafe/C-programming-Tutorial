# **Running `sizeof` on an Embedded Target in STM32 CubeIDE**  

## **Introduction**  
In embedded systems programming, it is crucial to understand how different data types occupy memory. Since microcontrollers have limited RAM, **memory efficiency** is a key factor in designing embedded applications.

The `sizeof` operator in C helps determine the amount of memory (in bytes) a particular data type occupies. However, this can vary based on:
- The microcontroller’s architecture (e.g., ARM Cortex-M)
- The compiler (e.g., GCC for ARM)
- The compiler settings

This guide walks you through using `sizeof` to determine the **storage size** of fundamental data types in STM32 CubeIDE while cross-compiling for an STM32 microcontroller.

---

## **Why is `sizeof` Important in Embedded Systems?**  
- Ensures **efficient memory allocation** on devices with limited RAM.
- Helps in **struct alignment and padding** for optimized memory usage.
- Avoids **overflow issues** by selecting appropriate data types.
- Assists in **debugging** by verifying expected memory sizes.

---

## **Understanding Memory Allocation in Embedded Systems**  

Each data type in C occupies a certain number of bytes. This depends on whether the system is **32-bit, 64-bit, or an embedded architecture**.

| **Data Type**   | **Size in x86 (PC)** | **Size in ARM Cortex-M (Embedded)** |
|----------------|----------------------|--------------------------------------|
| `char`         | 1 byte                | 1 byte                              |
| `int`          | 4 bytes               | 4 bytes                             |
| `long`         | 4 bytes               | 4 bytes                             |
| `long long`    | 8 bytes               | 8 bytes                             |
| `double`       | 8 bytes               | 8 bytes                             |

**Note**: In embedded systems, `sizeof(int)` may still be 4 bytes, even on 16-bit microcontrollers, due to compiler optimizations.

---

## **Checking Data Type Sizes in STM32 CubeIDE**  

We will create a simple C program that prints the `sizeof` value for different data types when compiled and executed on an **STM32 microcontroller**.

### **Step 1: Writing the C Code**
Create a file **`sizeof_test.c`** and add the following code:

```c
#include <stdio.h>

void sizeof_test() {
    printf("Size of char: %lu bytes\n", sizeof(char));
    printf("Size of int: %lu bytes\n", sizeof(int));
    printf("Size of long: %lu bytes\n", sizeof(long));
    printf("Size of long long: %lu bytes\n", sizeof(long long));
    printf("Size of double: %lu bytes\n", sizeof(double));
}
