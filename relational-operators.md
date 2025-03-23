# Relational Operators in C

## Introduction
Relational operators in C perform comparisons between two operands and return:
- `1` (true) if the condition is met.
- `0` (false) if the condition is not met.

They are **binary operators**, meaning they require two operands, and are evaluated from **left to right**.

## List of Relational Operators in C

| Operator | Symbol | Description | Example | Output |
|----------|--------|-------------|---------|--------|
| Equal to | `==` | Checks if two values are equal | `10 == 20` | `0` (false) |
| Greater than | `>` | Checks if the left operand is greater than the right operand | `20 > 10` | `1` (true) |
| Less than | `<` | Checks if the left operand is smaller than the right operand | `5 < 10` | `1` (true) |
| Greater than or equal to | `>=` | Checks if the left operand is greater than or equal to the right operand | `10 >= 10` | `1` (true) |
| Less than or equal to | `<=` | Checks if the left operand is smaller than or equal to the right operand | `10 <= 5` | `0` (false) |
| Not equal to | `!=` | Checks if two values are not equal | `10 != 20` | `1` (true) |

## True and False in C
- In C, **zero (`0`)** is interpreted as **false**, and any **non-zero value** is interpreted as **true**.
- Expressions using relational operators evaluate to either **`1` (TRUE)** or **`0` (FALSE)**.
- Relational expressions are commonly used within **if** and **while** statements to control program flow.

## Example Code and Output

### Code:
```c
#include <stdio.h>

int main() {
    int A = 10, B = 20;
    int C;

    // Example 1: Equality Check
    C = (A == B);
    printf("A == B: %d\n", C);  // Output: 0 (false)

    // Example 2: Less than or Equal to
    C = (A <= B);
    printf("A <= B: %d\n", C);  // Output: 1 (true)

    // Example 3: Not Equal to
    C = (A != B);
    printf("A != B: %d\n", C);  // Output: 1 (true)

    // Example 4: Less than
    C = (A < B);
    printf("A < B: %d\n", C);  // Output: 1 (true)

    return 0;
}
