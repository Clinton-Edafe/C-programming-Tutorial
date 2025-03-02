# Returning Data from a Function in C

## Introduction
In C programming, functions can return values to the calling function. Returning data from a function is crucial when the function computes a value that must be used elsewhere in the program. The `return` statement is used to send a value back to the caller.

## Why Return Data from a Function?
Returning data from a function allows:
- Code reusability by encapsulating logic.
- Modularity by separating computations.
- Efficient data handling in large programs.

## The `return` Statement
The `return` statement in C is used to exit from a function and optionally send a value back to the calling function. The return type of the function must match the data type of the value being returned.

### General Syntax
```c
return expression;
```

## Example: Incorrect Function Code
Let's analyze an incorrect function code example to understand why proper return types and function definitions are necessary.

### Incorrect Code
```c
#include <stdio.h>
void function_add_numbers (int, int, int);

int main ()
{
    int retValue;
    retValue = function_add_numbers (12, 13, 0); // Expecting return value

    printf("Sum = %d\n", retValue);

    return 0;
}

// Incorrect Function Definition
int function_add_numbers (int a, int b, int c);
{
    int sum;
    sum = a + b + c;

    return sum;
}
```

### Errors in the Above Code:
1. **Function Prototype Mismatch:** The function prototype declares `function_add_numbers` as `void`, which means it should not return a value, yet the function definition attempts to return `sum`.
2. **Incorrect Function Definition Syntax:** The semicolon `;` after the function header is incorrect. It should be removed.

## Correcting the Function Code with a Proper Function Prototype

### Correct Code
```c
#include <stdio.h>

// Function Prototype
int function_add_numbers (int, int, int);

int main ()
{
    int retValue;
    retValue = function_add_numbers (12, 13, 0); // Calling function

    printf("Sum = %d\n", retValue);

    return 0;
}

// Correct Function Definition
int function_add_numbers (int a, int b, int c) // No semicolon here
{
    int sum;
    sum = a + b + c;

    return sum; // Correctly returning sum
}
```

### Expected Output:
```
Sum = 25
```

## Explanation of the Correct Code:
- **Function Prototype:** `int function_add_numbers(int, int, int);` declares that the function will return an `int` value.
- **Function Call:** The function is called in `main()` and its return value is stored in `retValue`.
- **Function Definition:** The function now correctly computes the sum and returns it.
- **Proper Return Handling:** `return sum;` ensures that the computed sum is sent back to `main()`.

## Key Takeaways
1. **Match Function Prototype and Definition:** Ensure the return type in the prototype matches the function definition.
2. **Use `return` to Send Data:** A function with a return type other than `void` must return a value.
3. **Avoid Extra Semicolons in Function Definitions:** The function header should not have a trailing semicolon.

