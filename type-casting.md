# Typecasting in C

## Introduction
Typecasting is a way of converting a variable or data from one data type to another data type.

When a higher data type is converted into a lower data type, data may be **truncated** (i.e., lost).

There are **two types** of typecasting in C:

1. **Implicit casting**: Done automatically by the compiler based on default settings.
2. **Explicit casting**: Performed by the programmer to override the compiler's default behavior.

---

## Implicit Typecasting (Compiler Handles It)
Implicit typecasting occurs automatically when the compiler converts one data type to another.

### Example of Implicit Casting with Data Loss
```c
#include <stdio.h>

int main(void)
{
    unsigned char data = 0x87 + 0xFF00; 
    float result = 80 / 3;
    printf("Data: %u result: %f\n", data, result);
    return 0;
}
```

### Error Message:
```
warning: conversion from 'int' to 'unsigned char' changes value from '65415' to '87'
```

### Explanation:
- `0x87` (1-byte) + `0xFF00` (2-byte) exceeds the `unsigned char` range (0-255).
- The higher-order bytes are lost, causing incorrect data storage.

---

## Correcting Implicit Typecasting
Below is an example without data loss where implicit casting happens correctly.

```c
#include <stdio.h>

int main(void)
{
    unsigned char data = 0x01 + 0x0089; // 0x8A
    float result = 80 / 3;
    printf("Data: %u result: %f\n", data, result);
    return 0;
}
```

**How the Compiler Sees It:**
```c
unsigned char data = 0x00000001 + 0x00000089; // Implicit casting
```

### Output:
```
Data: 138 result: 26.000000
```

---

## Explicit Typecasting (Programmer Handles It)
To avoid unintended data loss, we explicitly cast the value.

### Example of Explicit Typecasting
```c
#include <stdio.h>

int main(void)
{
    unsigned char data = (unsigned char)(0x87 + 0xFF00);
    float result = 80 / 3;
    printf("Data: %u result: %f\n", data, result);
    return 0;
}
```

### Output:
```
Data: 135 result: 26.000000
```

**Why It Works:**
- The `(unsigned char)` typecast ensures only the least significant byte (LSB) is stored.

---

## Correcting Float Division in Explicit Casting
By default, `80 / 3` is an **integer division**, which leads to loss of precision.
We fix this by explicitly casting one operand to `float`.

### Correct Code
```c
#include <stdio.h>

int main(void)
{
    unsigned char data = (unsigned char)(0x87 + 0xFF00);
    float result = (float)80 / 3;  // or 80 / (float)3
    printf("Data: %u result: %f\n", data, result);
    return 0;
}
```

### Output:
```
Data: 135 result: 26.666668
```

**Explanation:**
- `(float)80` promotes `80` to `float`, making `80 / 3` a **floating-point division** instead of an integer division.

---

## Typecasting Large Integers to Smaller Data Types
Attempting to store a `long long int` into a smaller type causes data loss.

### Example with Potential Data Loss
```c
#include <stdio.h>

int main(void)
{
    unsigned char data = 0x1FFFFFFF0B0 + 0x1245;
    float result = 80 / (float)3;
    printf("Data: %u result: %f\n", data, result);
    return 0;
}
```

### Error Message:
```
warning: overflow in implicit constant conversion
```

### Will There Be an Output?
Yes! Despite the data loss, **an output will still be printed**, but the value stored in `data` will be truncated due to overflow.

---

## Conclusion
- **Implicit casting** happens automatically but may cause unintended data loss.
- **Explicit casting** prevents data loss and ensures correct calculations.
- **Integer division vs. Floating-point division**: Always explicitly cast to `float` when necessary.
- Storing large integers in smaller types leads to overflow, but an output is still produced (with incorrect values).
