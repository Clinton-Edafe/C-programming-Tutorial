# Operators in C

An **operator** is a symbol that tells the compiler to perform a certain mathematical or logical manipulation on the operands.

## Types of Operators
- **Unary Operators**
- **Binary Operators**
- **Ternary Operators**
- **Arithmetic (Mathematical) Operators**

## Arithmetic Operators
| Operator | Description |
|----------|-------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus (Remainder of division) |

### Example: Modulus Operator
```c
#include <stdio.h>
int main() {
    int result = 14 % 4; // 14 divided by 4 gives remainder 2
    printf("14 %% 4 = %d\n", result);
    return 0;
}
```
#### Output:
```
14 % 4 = 2
```

## Operator Precedence in C
Operator precedence rules determine which mathematical operation takes place first. Parentheses `()` may be used to force an expression to a higher precedence.

### Example
```c
#include <stdio.h>
int main() {
    uint32_t value;
    value = 2 + 3 * 4; // Is value = 20 or value = 14?
    printf("value = %d\n", value);
    return 0;
}
```
#### Output:
```
value = 14  // Multiplication (*) has higher precedence than addition (+)
```

### Precedence Table
The lower the precedence number, the higher the priority.

| Operator | Description | Precedence |
|----------|-------------|------------|
| `()` | Parentheses | **1 (Highest)** |
| `* / %` | Multiplication, Division, Modulus | 2 |
| `+ -` | Addition, Subtraction | 3 |
| `< > <= >=` | Relational Operators | 4 |
| `== !=` | Equality Operators | 5 |

### Example: Forced Precedence with `()`
```c
#include <stdio.h>
int main() {
    uint32_t value;
    value = (2 + 3) * 4; // Using parentheses to force precedence
    printf("value = %d\n", value);
    return 0;
}
```
#### Output:
```
value = 20  // Parentheses override multiplication precedence
```

### Associativity
Associativity determines how an expression is evaluated when two or more operators of the same precedence appear in an expression.

- **Left-to-right associativity**: Operators of the same precedence are evaluated from left to right.
- **Right-to-left associativity**: Operators of the same precedence are evaluated from right to left.

#### Example:
```c
#include <stdio.h>
int main() {
    int result = 12 + 3 - 4 / 2 < 3 + 1;
    printf("Result = %d\n", result);
    return 0;
}
```
#### Output:
```
Result = 1  // Due to left-to-right evaluation order
```

## Important Notes
- **All arithmetic operators are binary operators** (i.e., they require at least two operands).
- **Use parentheses `()` to control precedence** in complex expressions.
- **Understand precedence and associativity** to write clear and correct code.
