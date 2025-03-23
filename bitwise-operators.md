## Bitwise Operators in Embedded C Programming

### Introduction
Bitwise operators in C are used to manipulate individual bits of data. They are especially useful in embedded systems where memory and processing power are limited. Unlike arithmetic operators that work at the byte or word level, bitwise operators allow us to work directly with binary digits (bits).

### Bitwise Operators in C

| Operator | Name | Description |
|----------|------|-------------|
| `&` | AND | Performs bitwise AND operation |
| `|` | OR | Performs bitwise OR operation |
| `^` | XOR | Performs bitwise XOR operation |
| `~` | NOT | Performs bitwise negation |
| `<<` | Left Shift | Shifts bits to the left |
| `>>` | Right Shift | Shifts bits to the right |

### Real-World Applications of Bitwise Operators
1. **Memory Optimization** – Efficient data storage and retrieval by packing multiple values into a single byte.
2. **Peripheral Control** – Setting, clearing, and toggling hardware registers.
3. **Data Encryption** – XOR operations in cryptographic algorithms.
4. **Error Detection** – Parity checks in data transmission.

### Difference Between Logical and Bitwise Operators

| Feature | Logical Operators (`&&`, `||`, `!`) | Bitwise Operators (`&`, `|`, `^`, `~`) |
|---------|--------------------------------|--------------------------------|
| Operates on | Boolean values (true/false) | Individual bits |
| Returns | Boolean result (0 or 1) | New binary value |
| Example | `(a > 5) && (b < 10)` | `a & b` |
| Use Case | Control flow (if statements) | Hardware-level operations |

### Applicability of Bitwise Operations

#### 1. Testing Bits (`&`)
Checking if a particular bit is set or cleared.
```c
if (number & (1 << bit_position)) {
    printf("Bit is set");
} else {
    printf("Bit is cleared");
}
```

#### 2. Setting Bits (`|`)
Setting a particular bit to 1.
```c
number |= (1 << bit_position);
```

#### 3. Clearing Bits (`~` and `&`)
Clearing a particular bit to 0.
```c
number &= ~(1 << bit_position);
```

#### 4. Toggling Bits (`^`)
Flipping a particular bit.
```c
number ^= (1 << bit_position);
```

### Exercises
#### 1. Bitwise Operations on Two Integers
Write a program that takes two integers from the user and computes bitwise `&`, `|`, `^`, and `~` operations.

```c
#include <stdio.h>

int main() {
    int a, b;
    printf("Enter two integers: ");
    scanf("%d %d", &a, &b);

    printf("AND: %d\n", a & b);
    printf("OR: %d\n", a | b);
    printf("XOR: %d\n", a ^ b);
    printf("NOT A: %d\n", ~a);
    printf("NOT B: %d\n", ~b);
    
    return 0;
}
```

#### 2. Even or Odd using Bitwise Operations

```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter an integer: ");
    scanf("%d", &num);

    if (num & 1) {
        printf("%d is Odd\n", num);
    } else {
        printf("%d is Even\n", num);
    }
    return 0;
}
```

#### 3. Setting 4th and 7th Bits
```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    
    num |= (1 << 3); // Set 4th bit (0-based index)
    num |= (1 << 6); // Set 7th bit
    
    printf("Modified number: %d\n", num);
    return 0;
}
```

### Conclusion
Bitwise operators are fundamental in embedded systems for efficient data manipulation. Mastering them allows developers to write optimized, low-level code crucial for hardware interaction.
