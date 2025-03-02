# **Building Blocks of Compiler Stages in C Programming**

Compiling a C program involves multiple stages, transforming source code into an executable file. These stages include:

1. **Preprocessing** (`.c → .i`)
2. **Compilation** (`.i → .s`)
3. **Assembly** (`.s → .o`)
4. **Linking** (`.o → executable`)

---

## **1. Preprocessing Stage (`main.c → main.i`)**
The preprocessor handles directives like `#include`, `#define`, and `#ifdef`. It removes comments, expands macros, and includes the content of header files.

### **Example: `main.c` (Before Preprocessing)**
```c
#include <stdio.h>
#define PI 3.14

int main() {
    printf("Value of PI: %f\n", PI);
    return 0;
}
```

### **Preprocessed File: `main.i`**
```c
// Comments removed
// Header file content included
// Macros expanded

int main() {
    printf("Value of PI: %f\n", 3.14);
    return 0;
}
```

**Command to Generate Preprocessed File:**
```bash
gcc -E main.c -o main.i
```

---

## **2. Compilation Stage (`main.i → main.s`)**
This stage translates the preprocessed C code into assembly code (`.s` file), which contains human-readable assembly instructions.

### **Generated Assembly Code: `main.s`**
```assembly
    .section .rodata
.LC0:
    .string "Value of PI: %f\n"
    .text
    .globl main
main:
    pushq   %rbp
    movq    %rsp, %rbp
    movl    $.LC0, %edi
    movl    $3.14, %esi
    call    printf
    movl    $0, %eax
    popq    %rbp
    ret
```

**Command to Generate Assembly Code:**
```bash
gcc -S main.i -o main.s
```

---

## **3. Assembly Stage (`main.s → main.o`)**
The assembler converts the assembly instructions into machine code (object file `.o`).

### **Object File (`main.o` - Machine Code Representation)**
The `.o` file is in binary format and not human-readable. It contains:
- Machine-level instructions (opcodes)
- Symbol table for unresolved references

**Command to Generate Object File:**
```bash
gcc -c main.s -o main.o
```

---

## **4. Linking Stage (`main.o → Executable`)**
The linker combines the object file with standard libraries (like `libc`) to produce the final executable (`a.out`).

**Command to Generate Executable:**
```bash
gcc main.o -o main
```

**Running the Executable:**
```bash
./main
```

**Expected Output:**
```
Value of PI: 3.140000
```

---

## **Summary of Compilation Stages**
| Stage | Input File | Output File | Purpose |
|-------|------------|------------|---------|
| Preprocessing | `main.c` | `main.i` | Expands macros, includes headers |
| Compilation | `main.i` | `main.s` | Converts C code to assembly |
| Assembly | `main.s` | `main.o` | Converts assembly to machine code |
| Linking | `main.o` | `main` | Produces the final executable |

---


