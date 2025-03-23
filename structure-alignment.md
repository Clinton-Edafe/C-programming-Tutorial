# Structures in Embedded Systems Programming

## Introduction to Structures

In C programming, a **structure** (struct) is a user-defined data type that allows grouping of different data types under a single name. It helps in organizing related data efficiently and is widely used in embedded systems for memory-mapped registers, sensor data, and configuration settings.

### Syntax of a Structure
```c
struct SensorData {
    uint16_t temperature;
    uint16_t humidity;
    uint16_t pressure;
};
```
Here, we define a structure `SensorData` that groups three variables together.

## Accessing Structure Members

We can access structure members using the **dot (.)** operator if we have a structure variable, or the **arrow (->)** operator if we are dealing with a pointer to a structure.

### Example
```c
#include <stdio.h>
#include <stdint.h>

struct SensorData {
    uint16_t temperature;
    uint16_t humidity;
    uint16_t pressure;
};

int main() {
    struct SensorData sensor = {25, 60, 1013};
    
    // Accessing structure members using dot operator
    printf("Temperature: %d\n", sensor.temperature);
    printf("Humidity: %d\n", sensor.humidity);
    printf("Pressure: %d\n", sensor.pressure);
    
    return 0;
}
```

## Size of a Structure

The `sizeof` operator is used to determine the size of a structure in memory.

### Example
```c
#include <stdio.h>
#include <stdint.h>

struct SensorData {
    uint16_t temperature;
    uint16_t humidity;
    uint16_t pressure;
};

int main() {
    printf("Size of structure: %lu bytes\n", sizeof(struct SensorData));
    return 0;
}
```

## Aligned vs Unaligned Data Access

### **Aligned Data Access**
Aligned access means that data is stored at memory addresses that match their size requirements.
For example, a `uint32_t` (4 bytes) is stored at an address that is a multiple of 4.

**Example:**
```c
struct Aligned {
    uint32_t a;  // 4-byte aligned
    uint16_t b;  // 2-byte aligned
    uint16_t c;  // 2-byte aligned
};
```

### **Unaligned Data Access**
When structure members are not naturally aligned, the processor may require additional cycles to fetch them, causing performance issues.

**Example of unaligned structure:**
```c
struct Unaligned {
    uint8_t a;   // 1-byte aligned
    uint32_t b;  // 4-byte aligned but stored at a misaligned address
    uint16_t c;  // 2-byte aligned
};
```
This structure might have padding inserted between members to maintain proper memory alignment.

### **How to Ensure Proper Alignment**
Using the `__attribute__((packed))` directive in GCC or `#pragma pack(1)` in MSVC compilers forces compact memory layout.

**Example:**
```c
struct __attribute__((packed)) PackedStruct {
    uint8_t a;
    uint32_t b;
    uint16_t c;
};
```
This eliminates unnecessary padding but may cause unaligned memory access issues on certain architectures.

## Conclusion
Structures are a powerful tool in embedded systems programming, allowing efficient data grouping and access. Understanding structure alignment is crucial to optimize memory usage and performance, especially in low-power embedded environments.
