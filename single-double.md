# 🖥️ Single vs Double Precision & IEEE-754 Floating-Point Standard  

## 📌 Introduction  
The **IEEE-754** is a **standard for representing and manipulating floating-point quantities**, followed by all modern **computer systems** and **microcontrollers**.  

Floating-point numbers are used to represent **real numbers** in a **binary format**, which allows computers to perform calculations with fractional values efficiently.  

---

## 📊 IEEE-754 Floating-Point Standard  

The **IEEE-754 standard** defines:  
- **Single Precision (32-bit)**
- **Double Precision (64-bit)**  

Each floating-point number consists of:  
- **Sign (1 bit)**: Determines whether the number is positive (0) or negative (1).  
- **Exponent (8 or 11 bits)**: Stores the exponent value.  
- **Mantissa/Significand (23 or 52 bits)**: Stores the significant digits of the number.  

### 📌 Example: Representing **+7.432 × 10^48**  

| **Component** | **Binary Representation** |
|--------------|---------------------------|
| **Sign** (1 bit) | `0` (Positive number) |
| **Exponent** (8/11 bits) | Encoded value of `48` |
| **Mantissa (Significand)** | Binary form of `7.432` |

This number is stored in memory using the **IEEE-754 floating-point format**.

---

## 🆚 Single Precision (32-bit) vs Double Precision (64-bit)  

| Precision Type  | Bits | Exponent Bits | Mantissa Bits | Approximate Decimal Precision |
|----------------|------|--------------|--------------|------------------------------|
| **Single Precision (float)** | 32   | 8  | 23  | ~6-7 decimal places  |
| **Double Precision (double)** | 64   | 11 | 52  | ~15-16 decimal places |

### 🔥 **Key Differences**:
1. **Single precision (float)** uses **4 bytes** of memory (faster but less accurate).
2. **Double precision (double)** uses **8 bytes** (higher accuracy but takes more memory).
3. **Double precision** is preferred for scientific and high-precision calculations.

---

## 📝 Representing **125.55** in a Program  

A **floating-point number** consists of:  
- **Integer part** → `125`  
- **Decimal point** → `.`  
- **Fractional part** → `55`  

🔹 **You cannot store this number using integer data types** (`int`, `char`, `long`).  
🔹 You need **special data types** for floating-point numbers:  
   - **float (32-bit, single precision)**  
   - **double (64-bit, double precision)**  

### ⚡ **Example: IEEE-754 Representation of 125.55 in Single Precision (32-bit)**  

| **Component**  | **Binary Representation** |
|---------------|---------------------------|
| **Sign (1 bit)** | `0` (Positive number) |
| **Exponent (8 bits)** | Encoded exponent |
| **Mantissa (23 bits)** | Binary form of `125.55` |

---

## ⚡ Floating-Point Representation Example in C  

```c
#include <stdio.h>

int main() {
    float num1 = 125.55f;   // Single precision (32-bit)
    double num2 = 125.55;   // Double precision (64-bit)

    printf("Float: %f\n", num1);
    printf("Double: %lf\n", num2);
    
    return 0;
}
