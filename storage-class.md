# **Storage Class Specifiers in 'C'**

## **Introduction**
In C programming, **storage class specifiers** define three key attributes of variables and functions:

1. **Scope** – Where the variable or function is accessible.
2. **Visibility** – Who can use it (inside or outside a file).
3. **Lifetime** – How long the variable exists in memory.

The most commonly used storage class specifiers in C are:
- `static`
- `extern`

This guide will explain these two specifiers with **clear, beginner-friendly examples**.

---

## **1. `static` Storage Class Specifier**
The `static` keyword in C:
- Extends **lifetime** of a variable to the entire program execution.
- Limits **scope** to the file or function where it is declared.
- Prevents a variable from being reinitialized on each function call.

### **Example 1: Static Variable in a Function**
```c
#include <stdio.h>

void counterFunction() {
    static int count = 0; // Static variable
    count++;
    printf("Count = %d\n", count);
}

int main() {
    counterFunction();
    counterFunction();
    counterFunction();
    return 0;
}
```
#### **Output:**
```
Count = 1
Count = 2
Count = 3
```
🔹 **Why?** Unlike normal variables that reset on each function call, `static` retains its value between calls.

---

### **Use Case: `static` with Functions (Private Variables)**
Static functions **restrict access** to a function **only within the file** it is declared in.

#### **Example 2: Static Function (Private Function)**
```c
#include <stdio.h>

static void privateFunction() { // Private function
    printf("This is a private function inside this file.\n");
}

int main() {
    privateFunction(); // Allowed
    return 0;
}
```
 **Key takeaway:** A `static` function **cannot be called from another file**.

---

## **2. `extern` Storage Class Specifier**
The `extern` keyword:
- Declares a **global variable or function** defined in another file.
- Does **not** allocate memory; only references an existing definition.
- Used to **share variables between files**.

### **Example 3: Using `extern` to Share a Global Variable**
#### **File 1: `file1.c` (Defines the variable)**
```c
#include <stdio.h>

int globalVar = 10; // Global variable
```

#### **File 2: `file2.c` (Uses `extern` to access `globalVar`)**
```c
#include <stdio.h>
extern int globalVar; // Declaration, not definition

int main() {
    printf("Value of globalVar: %d\n", globalVar);
    return 0;
}
```
#### **Output:**
```
Value of globalVar: 10
```
 **Why?** The `extern` keyword allows `file2.c` to access `globalVar` defined in `file1.c`.

---

## **Summary Table: `static` vs `extern`**
| Specifier | Scope | Lifetime | Use Case |
|-----------|--------|-----------|------------|
| `static` (variable) | Function or file | Entire program | Retains value across calls |
| `static` (function) | File | Until program ends | Private function within a file |
| `extern` | Global | Until program ends | Share variables between files |

---

## **Final Notes**
🔹 Use `static` for **private** variables and functions to limit access.
🔹 Use `extern` for **sharing variables across files**.