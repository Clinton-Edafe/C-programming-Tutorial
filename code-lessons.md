# C Programming Learning Notes - Neso Academy

## Features of C Programming
- **Procedural Programming:** Programs are structured as a series of procedures or functions, making code easier to understand and debug.
- **Middle-Level Language:**
  - Combines features of both high-level and low-level languages.
  - **Direct Access to Memory:** Through pointers, programmers can directly access and manipulate memory addresses.
  - **Bit Manipulation:** Using bitwise operators such as `&`, `|`, `^`, `~`, `<<`, and `>>` for low-level data manipulation.
  - **Assembly Code:** Inline assembly allows writing assembly instructions within C code for performance-critical sections.
- **Rich Standard Libraries:**
  - Built-in functions for input/output, string manipulation, math operations, memory management, and more.
  - Standard libraries and header files like `stdio.h`, `stdlib.h`, `math.h`, `string.h`, etc., simplify development.

## Writing the First C Program
```c
#include <stdio.h>

int main() {
    printf("Embedded Systems Ch1\n");
    return 0;
}
```
### Output:
```
Embedded Systems Ch1
```
### Explanation:
- **Preprocessor Directive:** `#include <stdio.h>` tells the compiler to include the Standard Input Output library before compilation.
- **Main Function:** Entry point of every C program; execution starts from `main()`.
- **printf():** A standard library function used to print output to the console.
- **Escape Sequence:** `\n` is used to print a newline.
- **Return Statement:** `return 0;` signifies successful program execution to the operating system.

## Variables and Naming Conventions
- **Variables:** Used to store data that can be modified during program execution.
- **Naming Rules:**
  - Must begin with a letter (A-Z or a-z) or an underscore `_`.
  - Can be followed by letters, digits (0-9), or underscores.
  - Cannot be a reserved keyword like `int`, `float`, `return`, etc.
  - Case-sensitive.

## Basic Output Functions
- `printf()` is the primary function to print data to the console.
- Format specifiers like `%d` (integer), `%f` (float), `%c` (character), and `%s` (string) are used in `printf()`.

## Fundamental Data Types
| Data Type | Size (Bytes) | Range |
|-----------|---------------|-------------------------|
| `char` | 1 | -128 to 127 (signed) / 0 to 255 (unsigned) |
| `int` | 4 | -2,147,483,648 to 2,147,483,647 |
| `float` | 4 | ~3.4E-38 to ~3.4E+38 |
| `double` | 8 | ~1.7E-308 to ~1.7E+308 |
| `long` | 8 | -9.2E+18 to 9.2E+18 |
| `short` | 2 | -32,768 to 32,767 |

### Using `sizeof` Operator
```c
#include <stdio.h>

int main() {
    printf("Size of int: %lu bytes\n", sizeof(int));
    printf("Size of char: %lu bytes\n", sizeof(char));
    printf("Size of float: %lu bytes\n", sizeof(float));
    return 0;
}
```
### Output:
```
Size of int: 4 bytes
Size of char: 1 bytes
Size of float: 4 bytes
```

## Exceeding Valid Range
- Assigning values beyond the valid range leads to **overflow** or **underflow**, causing unpredictable results.
- Example:
```c
#include <stdio.h>

int main() {
    char ch = 128; // Beyond the range of signed char (-128 to 127)
    printf("ch: %d\n", ch);
    return 0;
}
```
### Output:
```
ch: -128
```

## Characters
- **Size:** 1 byte.
- **Range:**
  - Signed: -128 to 127
  - Unsigned: 0 to 255

## Floating-Point Types
- `float` (4 bytes): Suitable for single-precision decimal values.
- `double` (8 bytes): Used for double-precision values.
- `long double` (10-16 bytes): Extended precision depending on the system.

## Scope of Variables
### Local vs Global Variables
- **Local Variable:** Declared inside a function; accessible only within that function.
- **Global Variable:** Declared outside any function; accessible throughout the program.

```c
#include <stdio.h>

int globalVar = 10;

int main() {
    int localVar = 5;
    printf("Local Variable: %d\n", localVar);
    printf("Global Variable: %d\n", globalVar);
    return 0;
}
```

## Variable Modifiers
### Auto & Extern
- **Auto:** Default storage class for local variables.
- **Extern:** Refers to a global variable declared in another file or outside the current function.

### Register
- Suggests the variable be stored in a CPU register for fast access (depends on the compiler).

### Static
- Retains its value between function calls.

## Constants in C
- `const` keyword:
  ```c
  const int x = 10;
  ```
- `#define` directive:
  ```c
  #define PI 3.14159
  ```

## Basic Input Function
- `scanf()` is used to read input from the user.
- Format specifiers used similarly to `printf()`.

```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    printf("You entered: %d\n", num);
    return 0;
}
```
### Output (Example):
```
Enter a number: 10
You entered: 10
```

