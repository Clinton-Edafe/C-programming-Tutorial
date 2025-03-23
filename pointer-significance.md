# Pointer Variables in Embedded C Programming

## Pointer Variables: Definition and Initialization

A **pointer variable** is a variable that stores the memory address of another variable. In C, pointers are essential for efficient memory management and direct hardware access, making them particularly useful in embedded systems.

### Example of Pointer Variable Initialization
```c
char *address1 = (char*) 0x00007FFF8EC3824;
```
Here, `address1` is a pointer variable of type `char*`, and it holds the memory address `0x00007FFF8EC3824`. The compiler allocates **8 bytes** for this pointer variable.

## Significance of Pointer Data Types
The **pointer data type** determines how the compiler interprets memory operations on the pointer variable. The type defines the size of data that the pointer accesses when dereferenced.

### Effect of Different Pointer Data Types on Pointer Operations

#### Example: Pointer to Different Data Types
```c
char* address1 = (char*) 0x00007FFF8E3C3824;  // Reads 1 byte
int* address1 = (int*) 0x00007FFF8E3C3824;   // Reads 4 bytes
long long* address1 = (long long*) 0x00007FFF8E3C3824; // Reads 8 bytes
```

Each pointer type affects how many bytes are read or written during operations. 

## Read and Write Operations in Pointers
### Read Operation
```c
char* address1 = (char*) 0X00007FFF8E3C3824; 
char data = *address1; // Dereferencing a pointer to read data
```
- `*` (dereference operator) retrieves the value stored at the pointer's address.
- `&` (address-of operator) is used to obtain the address of a variable.

### Write Operation
```c
*address1 = 0x89; // Writing a value to the memory location
```
This stores the value `0x89` at the memory address held by `address1`.

## Exercise: Implementing Pointer Operations

1. Create a `char` type variable and initialize it to value `100`.
2. Print the address of the variable.
3. Create a pointer variable and store the address of the variable.
4. Perform a **read operation** on the pointer to fetch 1 byte of data.
5. Print the fetched data.
6. Perform a **write operation** to store the value `65`.
7. Print the updated value of the original variable.

### Solution
```c
#include <stdio.h>

int main() {
    char var = 100; // Step 1: Declare and initialize a variable
    printf("Address of var: %p\n", (void*)&var); // Step 2: Print address

    char *ptr = &var; // Step 3: Pointer stores address of var

    char data = *ptr; // Step 4: Read operation
    printf("Read data from pointer: %d\n", data); // Step 5: Print read value

    *ptr = 65; // Step 6: Write operation
    printf("Updated value of var: %d\n", var); // Step 7: Print updated value

    return 0;
}
```

## How Pointers Are Used in Embedded Systems
### 1. Storing Data into SRAM
Pointers allow direct access to **SRAM locations**, ensuring efficient memory management.
```c
char *sram_ptr = (char*) 0x20000000; // Assume SRAM address
*sram_ptr = 0x55; // Store data
```

### 2. Copying Data from Peripheral Registers to SRAM
Microcontrollers use **memory-mapped registers** to communicate with peripherals.
```c
volatile int *peripheral_reg = (int*) 0x40021000; // Peripheral register address
int data = *peripheral_reg; // Read from peripheral
```

### 3. Configuring Peripheral Registers
Since peripherals are mapped to specific memory locations, **pointers** allow direct register modification.
```c
volatile int *gpio_mode_reg = (int*) 0x48000000; // GPIO register
*gpio_mode_reg |= (1 << 5); // Configure a pin
```

### 4. Using Pointers in Interrupt Service Routines (ISRs)
Pointers to ISRs are stored in the **vector table**, linking interrupts to their handlers.
```c
void (*ISR_Ptr)(void); // Pointer to an ISR
ISR_Ptr = &InterruptHandler; // Assign ISR function
```

### 5. Configuring Memory-Mapped Processor Registers
Pointers configure processor-specific registers like **interrupt control registers**.
```c
volatile int *NVIC_Enable = (int*) 0xE000E100;
*NVIC_Enable = (1 << 6); // Enable interrupt 6
```

Pointers play a crucial role in **low-level programming** in embedded systems by providing efficient memory access and peripheral control. Mastering pointer operations helps in writing **efficient**, **optimized**, and **hardware-specific** embedded C code.
