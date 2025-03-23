## Strings in C

### What is a String in C?
A string in C is a sequence of characters stored in an array, terminated by a null character `\0`. Unlike some other programming languages, C does not have a built-in `string` data type, so strings are implemented as character arrays.

### Declaring and Initializing Strings
You can declare a string in different ways:

```c
// Method 1: Character array with explicit size
char str1[6] = {'H', 'e', 'l', 'l', 'o', '\0'};

// Method 2: Character array with implicit size
char str2[] = "Hello"; // Automatically adds '\0'

// Method 3: Pointer to string literal
char *str3 = "Hello"; // Stored in read-only memory
```

> **Note:** `char *str3` points to a string literal, and modifying it may cause undefined behavior.

---

## String Literals
A **string literal** is a sequence of characters enclosed in double quotes (`" "`). It is automatically null-terminated and stored in read-only memory.

Example:

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

Here, "Hello, World!" is a string literal stored in memory.

---

## Inputting and Printing Strings
### Printing a String
You can print strings using `printf()` or `puts()`.

```c
#include <stdio.h>

int main() {
    char greeting[] = "Hello, World!";
    printf("%s\n", greeting);  // Using printf
    puts(greeting);              // Using puts (automatically adds newline)
    return 0;
}
```

### Inputting a String
To take user input as a string, use `scanf()` or `gets()`. However, `gets()` is unsafe and should be avoided in favor of `fgets()`.

```c
#include <stdio.h>

int main() {
    char name[50];
    printf("Enter your name: ");
    scanf("%s", name); // Reads until space or newline
    printf("Hello, %s!\n", name);
    return 0;
}
```

> **Limitation:** `scanf("%s", name);` cannot read multi-word input. To overcome this, use `fgets()`:

```c
#include <stdio.h>

int main() {
    char fullName[100];
    printf("Enter your full name: ");
    fgets(fullName, sizeof(fullName), stdin); // Reads the full line
    printf("Hello, %s", fullName);
    return 0;
}
```

`fgets()` ensures that input is safely stored within the array size limit and includes spaces.

---

### Summary
- Strings in C are character arrays terminated by `\0`.
- String literals are stored in read-only memory.
- Use `printf()` or `puts()` to print strings.
- Use `scanf()` for single-word input, and `fgets()` for multi-word input.
