# Logical Operators in 'C'

## Overview
Logical operators in C perform logical operations such as AND (&&), OR (||), and NOT (!). These operators are used to evaluate conditions and make decisions in programs.

## Logical Operators

| Operator | Description | Example |
|----------|-------------|----------|
| `&&` (AND) | Returns `1` if both operands are non-zero | `a && b` → 1 if both `a` and `b` are non-zero |
| `||` (OR) | Returns `1` if either operand is non-zero | `a || b` → 1 if either `a` or `b` is non-zero |
| `!` (NOT) | Returns `1` if operand is zero | `!a` → 1 if `a` is zero |

## Logical AND Operator (`&&`)
- The logical AND (`&&`) operator returns `1` (true) only if both operands have nonzero values.
- If either operand is `0`, the result is `0` (false).
- If the first operand is `0`, the second operand is not evaluated (short-circuiting behavior).

### Example
```c
#include <stdio.h>

int main() {
    int A = -10, B = 20;
    int C = (A && B); // C = 1 (true) because both A and B are non-zero
    printf("C = %d\n", C);
    
    A = 0, B = 20;
    C = (A && B); // C = 0 (false) because A is zero
    printf("C = %d\n", C);
    
    return 0;
}
```

## Example Problem
**What is the value of A in the following expression?**

```c
int x = 7, y = 9;
int A = !((x > 5) && (y < 5));
```
### Step-by-Step Evaluation
1. `(x > 5)` → `(7 > 5)` → `1` (true)
2. `(y < 5)` → `(9 < 5)` → `0` (false)
3. `(1 && 0)` → `0`
4. `!(0)` → `1`

### Final Answer
```c
A = 1;
