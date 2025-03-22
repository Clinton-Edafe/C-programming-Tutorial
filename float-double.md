# Working with `float` and `double` Variables in C

## Understanding `float` and `double`
In C programming, the `float` and `double` data types are used to store real (floating-point) numbers. The primary difference between them is **precision**:

- `float` (Single Precision): 32-bit storage, approximately 6-7 decimal places.
- `double` (Double Precision): 64-bit storage, up to 15 decimal places.

### **Range of `double`**
- **Storage size**: 8 bytes
- **Precision**: Up to 15 decimal places
- **Value range**: `2.3 × 10^-308` to `1.7 × 10^308`

## **Basic Example: Storing a Floating-Point Number**
```c
#include <stdio.h>

int main(void) {
    float number = 45.78976834578;
    printf("Number = %f\n", number);
    return 0;
}
```
### **Expected Output:**
```
Number = 45.789768
```
💡 **Explanation**: The `float` data type can only store about 6-7 decimal places, leading to precision loss.

## **Controlling Decimal Places in Output**
```c
#include <stdio.h>

int main(void) {
    double number = 45.78976834578;
    printf("Number = %.14lf\n", number);
    printf("Number = %.9lf\n", number);
    return 0;
}
```
### **Expected Output:**
```
Number = 45.78976834578000
Number = 45.789768346
```
💡 **Explanation**:
- `%.14lf` ensures that 14 decimal places are displayed.
- `%.9lf` rounds the number to 9 decimal places.

## **Precision Loss in `float`**
Using `float` leads to precision loss when working with long decimal numbers. 
```c
float number = 45.78976834578; 
```
This will **truncate** after about 6-7 digits.

## **Using Scientific Notation (`%e`)**
Scientific notation is useful for very large or small numbers, such as the **charge of an electron**.
```c
#include <stdio.h>

int main(void) {
    float chargeE = -1.60217662e-19;
    printf("ChargeE = %f\n", chargeE);
    printf("ChargeE = %e\n", chargeE);
    return 0;
}
```
### **Expected Output:**
```
ChargeE = -0.000000
ChargeE = -1.602177e-19
```
💡 **Explanation**:
- `%f` displays the number in normal decimal format (which is impractical for small numbers).
- `%e` displays it in **scientific notation**.

## **Handling Precision with `double`**
A `float` variable **cannot accurately store** the electron charge due to precision loss. **Using `double` solves this issue**.

```c
#include <stdio.h>

int main(void) {
    double chargeE = -1.60217662e-19;
    printf("chargeE = %.28lf\n", chargeE);
    printf("chargeE = %.8le\n", chargeE);
    return 0;
}
```
### **Expected Output:**
```
chargeE = -1.602176620000000020400596780e-19
chargeE = -1.60217662e-19
```
💡 **Explanation**:
- `%.28lf` displays up to 28 decimal places for extra precision.
- `%.8le` prints the value in scientific notation with 8 decimal places.

## **Conclusion**
- Use `float` when memory is limited and precision is not a concern.
- Use `double` when high precision is required.
- Scientific notation (`%e`) is useful for extremely large or small numbers.
- Always specify decimal precision using format specifiers (`%.nf` for normal, `%.ne` for scientific notation).

