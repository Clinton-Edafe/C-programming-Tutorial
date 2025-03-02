# Mathematical Operations in C using Functions and Separate Files

## Introduction
In this guide, we will write a C program that performs basic mathematical operations: **addition, subtraction, multiplication, and division**. The key objective is to:

1. Define these mathematical operations as separate functions in a file called `math.c`.
2. Call these functions from `main.c` to test them.
3. Understand how to compile and run a multi-file C program.

## Steps to Implement

### Step 1: Creating `math.h` (Header File)
A header file is needed to declare the function prototypes so that they can be used in `main.c`.

```c
// math.h
#ifndef MATH_H
#define MATH_H

// Function prototypes
tint add(int a, int b);
int subtract(int a, int b);
int multiply(int a, int b);
double divide(int a, int b);

#endif
```

### Step 2: Implementing `math.c`
This file contains the actual function definitions for addition, subtraction, multiplication, and division.

```c
// math.c
#include "math.h"
#include <stdio.h>

// Function to add two numbers
int add(int a, int b) {
    return a + b;
}

// Function to subtract two numbers
int subtract(int a, int b) {
    return a - b;
}

// Function to multiply two numbers
int multiply(int a, int b) {
    return a * b;
}

// Function to divide two numbers
// Returns a double to handle division properly
double divide(int a, int b) {
    if (b == 0) {
        printf("Error: Division by zero!\n");
        return 0.0;
    }
    return (double)a / b;
}
```

### Step 3: Writing `main.c`
The `main.c` file will include `math.h` and call the functions defined in `math.c`.

```c
// main.c
#include "math.h"
#include <stdio.h>

int main() {
    int num1 = 20, num2 = 5;

    printf("Addition: %d + %d = %d\n", num1, num2, add(num1, num2));
    printf("Subtraction: %d - %d = %d\n", num1, num2, subtract(num1, num2));
    printf("Multiplication: %d * %d = %d\n", num1, num2, multiply(num1, num2));
    printf("Division: %d / %d = %.2f\n", num1, num2, divide(num1, num2));

    return 0;
}
```

## Compilation and Execution
To compile and run the program:

```sh
gcc -o math_program main.c math.c
./math_program
```

## Expected Output
```
Addition: 20 + 5 = 25
Subtraction: 20 - 5 = 15
Multiplication: 20 * 5 = 100
Division: 20 / 5 = 4.00
```

## Key Takeaways
- **Functions** allow code modularity and reusability.
- **Header files (`math.h`)** define function prototypes for multiple file usage.
- **Separate source files (`math.c`)** help in organizing the logic of different operations.
- **Multi-file compilation** ensures a clean structure and easy debugging.