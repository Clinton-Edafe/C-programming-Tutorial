# Unary Operators in 'C'

## What are Unary Operators?
Unary operators are operators that act on a single operand. The most common unary operators in C are:

- `++` (Increment Operator)
- `--` (Decrement Operator)

These operators increase or decrease the value of a variable by 1. They can be used in **prefix** or **postfix** notation.

---

## Increment Operator (`++`)

### Post-Increment (`x++`)
In post-increment, the value of the variable is used first, and then it is incremented.

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    uint32_t x = 5;
    uint32_t m;
    
    m = x++; // Post-increment
    
    printf("m = %u, x = %u\n", m, x);
    return 0;
}
```
### Output:
```
m = 5, x = 6
```
**Explanation:**
1. The value of `x` (5) is assigned to `m` first.
2. After that, `x` is incremented by 1.
3. So, `m = 5` and `x = 6` after execution.

### Pre-Increment (`++x`)
In pre-increment, the variable is incremented first, and then the updated value is used.

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    uint32_t x = 5;
    uint32_t y;
    
    y = ++x; // Pre-increment
    
    printf("y = %u, x = %u\n", y, x);
    return 0;
}
```
### Output:
```
y = 6, x = 6
```
**Explanation:**
1. The value of `x` is incremented first (`x = 6`).
2. Then, the updated value of `x` is assigned to `y`.
3. So, `y = 6` and `x = 6` after execution.

---

## Decrement Operator (`--`)

### Post-Decrement (`x--`)
In post-decrement, the value of the variable is assigned first, and then it is decremented.

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    uint32_t n = 5;
    uint32_t m;
    
    m = n--; // Post-decrement
    
    printf("m = %u, n = %u\n", m, n);
    return 0;
}
```
### Output:
```
m = 5, n = 4
```
**Explanation:**
1. The value of `n` (5) is assigned to `m` first.
2. After that, `n` is decremented by 1.
3. So, `m = 5` and `n = 4` after execution.

### Pre-Decrement (`--x`)
In pre-decrement, the variable is decremented first, and then the updated value is used.

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    uint32_t x = 5;
    uint32_t y;
    
    y = --x; // Pre-decrement
    
    printf("y = %u, x = %u\n", y, x);
    return 0;
}
```
### Output:
```
y = 4, x = 4
```
**Explanation:**
1. The value of `x` is decremented first (`x = 4`).
2. Then, the updated value of `x` is assigned to `y`.
3. So, `y = 4` and `x = 4` after execution.

---

## Key Takeaways
- **Pre-Increment (`++x`)**: Increments the value first, then assigns.
- **Post-Increment (`x++`)**: Assigns the value first, then increments.
- **Pre-Decrement (`--x`)**: Decrements the value first, then assigns.
- **Post-Decrement (`x--`)**: Assigns the value first, then decrements.

# **Unary Operators with Pointers in C**  

## **Introduction**  

In C, **unary operators** like `++` (increment) and `--` (decrement) modify the value of a variable by **one unit**. When applied to **pointers**, these operators perform **pointer arithmetic**, moving the pointer to the next or previous memory location based on the **size of the data type**.  

This document explores **unary operators with pointers**, explaining how and why pointer addresses change when incremented or decremented.  

---

## **1. Understanding Pointer Arithmetic with Unary Operators**  

### **Example Code**  

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    uint32_t *pAddress = (uint32_t*) 0xFFFF0000;

    printf("Initial address: %p\n", pAddress);
    
    // Arithmetic addition operation
    pAddress = pAddress + 1;
    printf("After pAddress = pAddress + 1: %p\n", pAddress);

    // Unary increment operation
    pAddress++;
    printf("After pAddress++: %p\n", pAddress);

    // Unary decrement operation
    pAddress--;
    printf("After pAddress--: %p\n", pAddress);

    return 0;
}

