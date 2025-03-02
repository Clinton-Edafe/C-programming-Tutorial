# Functions in C

## Introduction

In C, functions are fundamental building blocks that allow modular programming, making code easier to debug, modify, and maintain. Every C program contains at least one function, which is the `main()` function. Functions help in reducing code redundancy and provide abstraction.

## General Form of a Function Definition

```c
return_data_type function_name (parameter list)
{
    // Function body
}
```

### Example: Main Function with No Input Arguments

```c
int main(void)
{
    /* Code execution starts here */
    return 0;
}
```

### Example: Main Function with Command-Line Arguments

```c
int main(int argc, char *argv[])
{
    /* argc - argument count, argv - argument vector (array of arguments) */
    return 0;
}
```

### Why Command-Line Arguments Are Rare in Embedded Systems

In embedded systems, programs typically run autonomously without user input from a command line. Therefore, passing arguments via `argc` and `argv` is not common. Instead, embedded systems rely on external inputs from sensors, hardware buttons, or communication interfaces.

## Importance of `int main()`

As per the C standard (C89 and above), `main()` should return an integer value:

```c
int main()
{
    return 0; // 0 means SUCCESS, non-zero means ERROR
}
```

Returning `void` in `main()` may trigger warnings because `main()` is expected to return an exit status to the parent process.

## Function Calls and Parameters

Functions can accept parameters, which are known as "formal parameters." These variables receive values when a function is called.

### Example: Function to Add Numbers

```c
#include <stdio.h>

void function_add_numbers(int a, int b, int c)
{
    int sum = a + b + c;
    printf("Sum = %d\n", sum);
}

int main()
{
    function_add_numbers(12, 13, 14);
    function_add_numbers(-20, 20, 4);
    int valueA = 90, valueB = 70;
    function_add_numbers(valueA, valueB, 90);

    return 0;
}
```

### Expected Output

```
Sum = 39
Sum = 4
Sum = 250
```

## Function Prototype

A function prototype informs the compiler about the function's return type and the types of arguments it accepts.

### Example with Function Prototype

```c
#include <stdio.h>

void function_add_numbers(int, int, int);

int main()
{
    function_add_numbers(12, 13, 14);
    function_add_numbers(-20, 20, 14);
    int valueA = 90, valueB = 70;
    function_add_numbers(valueA, valueB, 90);

    return 0;
}

// Function definition
void function_add_numbers(int a, int b, int c)
{
    int sum = a + b + c;
    printf("Sum = %d\n", sum);
}
```

### Expected Output

```
Sum = 39
Sum = 14
Sum = 250
```

## Common Mistake: Extra Semicolon in Function Definition

Incorrect function definition:

```c
void function_add_numbers(int a, int b, int c);
{
    int sum = a + b + c;
    printf("Sum = %d\n", sum);
}
```

This code will cause a compilation error because of the extra semicolon after `function_add_numbers(int a, int b, int c);`. The correct way is:

```c
void function_add_numbers(int a, int b, int c)
{
    int sum = a + b + c;
    printf("Sum = %d\n", sum);
}
```

## Conclusion

Functions in C provide modularity, reduce redundancy, and improve maintainability. The `main()` function serves as the program's entry point and should return an integer. Understanding function prototypes and proper function definitions is crucial to avoid errors. 


