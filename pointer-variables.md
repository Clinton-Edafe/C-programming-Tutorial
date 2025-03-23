# Understanding Pointer Variables in Embedded C

## Pointer Variables: Definition and Initialization

In Embedded C programming, **pointer variables** are special types of variables that store memory addresses instead of actual values. A pointer variable must be defined with a data type, which determines how operations like reading, writing, incrementing, and decrementing will behave.

### Example of Pointer Variable Definition
```c
char* address1 = (char*) 0x00007FFF8EC3824;
```
### Memory Allocation
When we declare a pointer variable, the compiler allocates **8 bytes** (on a 64-bit system) to store this pointer.

### Why Mention the Pointer Data Type?
```c
char* address1 = (char*) 0x00007FFF8EC3824;
```
The **pointer data type** determines the behavior of operations performed on the pointer variable. Different pointer data types yield different read sizes:

- **1-byte read operation**
  ```c
  char* address1 = (char*) 0x00007FFF8E3C3824;
  ```
- **4-byte read operation**
  ```c
  int* address1 = (int*) 0x00007FFF8E3C3824;
  ```
- **8-byte read operation**
  ```c
  long long* address1 = (long long*) 0x00007FFF8E3C3824;
  ```

## Read and Write Operations in Pointers
### Reading Data from a Pointer
```c
char* address1 = (char*) 0x00007FFF8E3C3824; 
char data = *address1;  // Dereferencing a pointer to read data
```
#### Operators Used:
- `*` (Value-at-address operator) → Used to **access the value** stored at a given memory address.
- `&` (Address-of operator) → Used to **retrieve the memory address** of a variable.

### Writing Data to a Pointer
```c
*address1 = 0x89; // Dereferencing a pointer to write data
```
This writes `0x89` to the memory location pointed to by `address1`.

---
## Practical Exercise with Comments
The following code demonstrates how to use pointers for reading and writing operations:

```c
#include <stdio.h>

int main() {
    // Step 1: Create a char variable and initialize it to 100
    char var = 100;
    
    // Step 2: Print the address of the variable
    printf("Address of var: %p\n", (void*)&var);
    
    // Step 3: Create a pointer variable and store the address of var
    char* ptr = &var;
    
    // Step 4: Read 1 byte of data from the pointer variable
    char data = *ptr;
    
    // Step 5: Print the data obtained from the read operation
    printf("Data read from pointer: %d\n", data);
    
    // Step 6: Write value 65 to the memory location pointed by the pointer
    *ptr = 65;
    
    // Step 7: Print the value of var after modification
    printf("Value of var after write operation: %d\n", var);
    
    return 0;
}
```

### Explanation:
1. **Step 1:** Declares a `char` variable `var` and assigns it the value `100`.
2. **Step 2:** Uses `printf` to display the memory address of `var`.
3. **Step 3:** Declares a pointer `ptr` that stores the address of `var`.
4. **Step 4:** Reads the data stored at `ptr`.
5. **Step 5:** Prints the data obtained from the pointer.
6. **Step 6:** Writes `65` into the memory location of `var` via the pointer.
7. **Step 7:** Prints the updated value of `var`, confirming that the memory was modified.

---
## Conclusion
Pointer variables in Embedded C allow efficient memory management and direct hardware interaction. Understanding their behavior based on data types is crucial for operations like reading and writing data. The example provided above demonstrates the practical use of pointers in embedded systems programming.
