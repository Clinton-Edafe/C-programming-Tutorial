# Decision Making in C Programming

## Introduction
Decision-making is a crucial aspect of programming. When writing a program, you often need to execute certain blocks of code only when specific conditions are met. Decision-making in C allows the program to respond to internal or external events dynamically.

A simple example of decision-making is switching off a motor based on a water level threshold. The program must check the water level sensor and take action accordingly.

## Flowchart: Motor Control Based on Water Level
```plaintext
+-----------------+
| Read Water Level |
+-----------------+
        |
        v
+-------------------+
| Water Level > 80%? |
+-------------------+
      | Yes  | No
      v      v
+-------------------+       +---------------+
| Turn OFF Motor   |       | Keep Running  |
+-------------------+       +---------------+
```

## Decision-Making Statements in C
C provides five different decision-making statements:

1. **if Statement**
2. **if-else Statement**
3. **if-else-if Ladder**
4. **Conditional (Ternary) Operator**
5. **switch-case Statement**

---

### 1. `if` Statement
The `if` statement executes a block of code only when a specified condition is true.

#### Syntax
##### Single Statement Execution
```c
if (expression)
    statement;
```

##### Multiple Statement Execution
```c
if (expression) {
    statement_1;
    statement_2;
}
```

#### Example: Simple `if` Statement
```c
#include <stdio.h>

int main(void) {
    unsigned int myData = 20;
    
    if (myData > 40)
        printf("Value = %d\n", myData);
    
    // This statement is outside the if block, so it always executes
    myData++;
    
    return 0;
}
```

---

## Exercise: Voting Eligibility Program
### Problem Statement
Write a C program that takes the user's age as input and determines whether they can cast a vote. The minimum age required to vote is **18 years**.

### Solution
```c
#include <stdio.h>

int main() {
    int age;
    
    // Take user input
    printf("Enter your age: ");
    scanf("%d", &age);
    
    // Decision making using if-else
    if (age >= 18) {
        printf("You are eligible to vote.\n");
    } else {
        printf("Sorry, you must be at least 18 years old to vote.\n");
    }
    
    return 0;
}
```

### Explanation
1. The program prompts the user to enter their age.
2. It uses an `if-else` statement to check if the age is 18 or more.
3. If the condition is met, it prints a message indicating voting eligibility.
4. Otherwise, it prints a message stating that the user cannot vote.

---

## Logical Operators in C
Logical operators allow us to perform logical operations such as AND, OR, and NOT. These are useful when combining multiple conditions in decision-making.

### Types of Logical Operators
| Operator | Description | Example |
|----------|-------------|---------|
| `&&` (AND) | Returns `1` (true) if both operands are non-zero | `(a && b)` |
| `||` (OR) | Returns `1` (true) if at least one operand is non-zero | `(a || b)` |
| `!` (NOT) | Returns `1` (true) if the operand is zero | `(!a)` |

### Logical AND (`&&`)
- The logical AND (`&&`) operator produces `1` if **both** operands are non-zero.
- If either operand is `0`, the result is `0`.
- If the first operand is `0`, the second operand is **not** evaluated (short-circuit evaluation).

#### Example
```c
#include <stdio.h>

int main() {
    int A = -10, B = 20;
    int C = (A && B); // C = 1 (true)
    
    printf("C = %d\n", C);
    
    A = 0; // Changing A to 0
    C = (A && B); // C = 0 (false)
    
    printf("C = %d\n", C);
    
    return 0;
}
```

### Logical OR (`||`)
- The logical OR (`||`) operator produces `1` if **at least one** operand is non-zero.
- If both operands are `0`, the result is `0`.

#### Example
```c
#include <stdio.h>

int main() {
    int X = 0, Y = 5;
    int Z = (X || Y); // Z = 1 (true)
    
    printf("Z = %d\n", Z);
    
    return 0;
}
```

### Logical NOT (`!`)
- The logical NOT (`!`) operator inverts the truth value of its operand.
- If the operand is `0`, it returns `1`.
- If the operand is non-zero, it returns `0`.

#### Example
```c
#include <stdio.h>

int main() {
    int A = 0;
    int B = !(A); // B = 1 (true)
    
    printf("B = %d\n", B);
    
    return 0;
}
```

### Logical Operator Evaluation Example
#### Problem
What is the value of `A` in the following expression?
```c
int x = 7, y = 9;
A = ! ((x > 5) && (y < 5));
```
#### Solution
1. Evaluate `(x > 5)`: `7 > 5` → `1`
2. Evaluate `(y < 5)`: `9 < 5` → `0`
3. `((x > 5) && (y < 5))` → `(1 && 0)` → `0`
4. `!(0)` → `1`

Thus, `A = 1`.

---

## Conclusion
Decision-making statements and logical operators are fundamental concepts in C programming. Logical operators help in evaluating multiple conditions efficiently, making them essential for writing robust and optimized code.
