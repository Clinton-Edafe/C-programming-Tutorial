# Understanding `scanf()` and `getchar()` in C  

## Introduction  

In C programming, interacting with users through input and output is essential for building dynamic applications. The `scanf()` function is used to read various types of user input, while `getchar()` helps in handling character-based inputs.  

This documentation provides a **comprehensive guide** to using `scanf()` and `getchar()` effectively, covering:  
- The syntax and working of `scanf()`  
- The importance of memory addresses in `scanf()`  
- Reading different types of data  
- `getchar()` for character input  
- An example exercise: computing the **average of three numbers**  

---

## What is `scanf()`?  

The `scanf()` function is a **standard library function** in C used to read input from the standard input device (**keyboard**). It belongs to the **Standard Input/Output Library (`stdio.h`)** and is useful for receiving **various types of input** such as integers, floating-point numbers, and characters.

### Features of `scanf()`  
✔ Reads **formatted input** based on type specifiers  
✔ Stores values **at memory locations** using the `&` operator  
✔ Supports multiple inputs separated by spaces  
✔ Stops reading when it encounters a **whitespace** (space, tab, newline)  

---

## Syntax of `scanf()`  

```c
scanf("format_specifier", &variable);
