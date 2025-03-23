## Unions in Embedded Systems Programming

### What is a Union in C?
A **union** in C is a special data type that allows storing different types of data in the **same memory location**. Unlike structures, where each member has its **own memory space**, all members of a union **share** the same memory space.

### Key Characteristics of Unions
- A union variable can **store only one value at a time**, meaning modifying one member affects all other members.
- The **size of a union** is equal to the size of its largest member.
- **Memory-efficient** compared to structures when storing mutually exclusive data.

### Syntax of a Union
```c
#include <stdio.h>

union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    union Data data;
    
    data.i = 10;
    printf("data.i = %d\n", data.i);
    
    data.f = 220.5;
    printf("data.f = %f\n", data.f);
    
    strcpy(data.str, "Hello");
    printf("data.str = %s\n", data.str);
    
    return 0;
}
```
**Explanation:**
1. `data.i = 10;` → Stores an integer.
2. `data.f = 220.5;` → Overwrites previous data.
3. `strcpy(data.str, "Hello");` → Overwrites float data.

### Difference Between Union and Structure
| Feature       | Structure | Union |
|--------------|----------|-------|
| Memory allocation | Each member has its own memory space | All members share the same memory space |
| Size | Sum of all member sizes | Size of the largest member |
| Data storage | Can hold multiple values at the same time | Can hold only one value at a time |
| Use case | When storing independent data fields | When storing mutually exclusive data |

### Use Cases of Unions
#### 1. **Bit Extraction**
Unions can help extract **individual bytes** from a multi-byte variable.
```c
#include <stdio.h>

union ByteExtractor {
    int num;
    unsigned char byte[4];
};

int main() {
    union ByteExtractor data;
    data.num = 0x12345678;
    printf("Byte 0: %x\n", data.byte[0]);
    printf("Byte 1: %x\n", data.byte[1]);
    printf("Byte 2: %x\n", data.byte[2]);
    printf("Byte 3: %x\n", data.byte[3]);
    return 0;
}
```
**Explanation:**
- The integer `0x12345678` is stored in memory.
- Using a union, we can extract **each byte separately**.

#### 2. **Memory Optimization (Mutually Exclusive Data)**
Unions are useful when **only one variable is needed at a time**.
```c
#include <stdio.h>

union SensorData {
    int temperature;
    float humidity;
};

int main() {
    union SensorData sensor;
    
    sensor.temperature = 25;
    printf("Temperature: %d°C\n", sensor.temperature);
    
    sensor.humidity = 60.5;
    printf("Humidity: %.1f%%\n", sensor.humidity);
    
    return 0;
}
```
**Explanation:**
- A union helps reduce memory usage when storing **mutually exclusive** sensor readings.

### Summary
✅ Unions share memory among members.
✅ Used for **bit extraction** and **memory optimization**.
✅ Size is determined by the **largest member**.
✅ Best suited for **mutually exclusive** data storage.

