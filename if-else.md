# 'if' and 'else' Statements in C

## Overview
The `if` and `else` statements in C are used to perform decision-making operations based on conditions. They allow a program to execute certain code blocks only when specific conditions are met.

### Syntax:
```c
if (condition) {
    // Code to execute if condition is true
} else {
    // Code to execute if condition is false
}
```

## Example 1: Voting Eligibility
### Problem Statement
Write a program that takes the user's age as input and determines whether they are eligible to vote.
- The minimum age for voting is 18.
- The program should print an appropriate message.

### Solution
```c
#include <stdio.h>

int main() {
    int age;
    
    // Prompt the user to enter their age
    printf("Enter your age: ");
    scanf("%d", &age);
    
    // Check voting eligibility
    if (age >= 18) {
        printf("You are eligible to vote.\n");
    } else {
        printf("You are not eligible to vote.\n");
    }
    
    return 0;
}
```

### Explanation
1. The program prompts the user to enter their age.
2. It reads the user's input and stores it in the variable `age`.
3. The `if` statement checks if `age` is 18 or more.
4. If the condition is true, it prints "You are eligible to vote."
5. If the condition is false, the `else` statement executes and prints "You are not eligible to vote."

### Sample Outputs
#### Case 1: User enters `20`
```
Enter your age: 20
You are eligible to vote.
```
#### Case 2: User enters `15`
```
Enter your age: 15
You are not eligible to vote.
```

---

## Example 2: Finding the Biggest Number
### Problem Statement
Write a program that receives two integers from the user and prints the larger of the two.
- If both numbers are equal, print "Both numbers are equal."

### Solution
```c
#include <stdio.h>

int main() {
    int num1, num2;
    
    // Prompt the user for two numbers
    printf("Enter two integers: ");
    scanf("%d %d", &num1, &num2);
    
    // Compare the numbers
    if (num1 > num2) {
        printf("%d is the larger number.\n", num1);
    } else if (num2 > num1) {
        printf("%d is the larger number.\n", num2);
    } else {
        printf("Both numbers are equal.\n");
    }
    
    return 0;
}
```

### Explanation (Step-by-Step with Comments)
1. Declare two integer variables `num1` and `num2`.
2. Prompt the user to enter two numbers.
3. Use `scanf` to store user input in `num1` and `num2`.
4. Compare `num1` and `num2` using `if-else`:
   - If `num1` is greater, print it as the largest number.
   - If `num2` is greater, print it as the largest number.
   - If both numbers are equal, print "Both numbers are equal."

### Sample Outputs
#### Case 1: User enters `8` and `5`
```
Enter two integers: 8 5
8 is the larger number.
```
#### Case 2: User enters `3` and `10`
```
Enter two integers: 3 10
10 is the larger number.
```
#### Case 3: User enters `7` and `7`
```
Enter two integers: 7 7
Both numbers are equal.
```

---

### Summary
- `if` and `else` are used for decision-making in C.
- Conditions determine which block of code executes.
- Using `else if` allows checking multiple conditions.
- Programs should be user-friendly with clear messages and prompts.
