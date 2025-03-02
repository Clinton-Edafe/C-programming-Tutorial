# Functions in C

In C programming, functions help in modularizing code, making it easier to debug, maintain, and reuse. Every C program must have at least one function, the `main` function, which serves as the entry point for execution.

## Function Definition in C
A C function is defined using the following general syntax:

```c
return_data_type function_name (parameter list)
{
    // Function body
}
```

### `main` Function Variants
1. **Main function without arguments**:
   ```c
   int main(void)
   {
       // Code execution starts here
   }
   ```

2. **Main function with command-line arguments**:
   ```c
   int main(int argc, char *argv[])
   {
       // Code execution with command-line arguments
   }
   ```
   In embedded systems, programs typically run autonomously without user input from a command line. Therefore, passing arguments via argc and argv is not common. Instead, embedded systems rely on external inputs from sensors, hardware buttons, or communication interfaces.
### Importance of `int main()`
According to C89 and above standards, `main` should return an `int` value. Returning `void` may trigger warnings. 

- `main()` takes zero or two arguments.
- It returns the program’s execution status to the parent process:
  - `0` → SUCCESS
  - Non-zero → ERROR

### Incorrect Function Example
The following code defines and calls a function, but it lacks a function prototype before calling it:

```c
#include <stdio.h>

int main()
{
    function_add_numbers(12, 13, 14);  // Function is used before declaration
    function_add_numbers(-20, 20, 4);
    int valueA = 90, valueB = 70;
    function_add_numbers(valueA, valueB, 90);
    return 0;
}

// Function definition
void function_add_numbers(int a, int b, int c)
{
    int sum;
    sum = a + b + c;
    printf("Sum = %d\n", sum);
}
```
**Error:** The function `function_add_numbers` is used before it is declared, which can cause implicit declaration issues.

### Corrected Function with Prototype
To fix this issue, we use a function prototype before calling the function:

```c
#include <stdio.h>

// Function prototype
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
    int sum;
    sum = a + b + c;
    printf("Sum = %d\n", sum);
}
```

### Expected Output
```
Sum = 39
Sum = 14
Sum = 250
```

By adding the function prototype, the compiler now knows the function’s return type and parameters before encountering the function call, preventing errors.
