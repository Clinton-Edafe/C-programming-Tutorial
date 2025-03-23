## IO Pin Read Exercise

### Objective
Write a program that reads the status of the pin **PA0**. If the status of **PA0** is **LOW**, then turn off the onboard **LED (PD12)**. If the status of **PA0** is **HIGH**, then turn on the **LED**.

Additionally, manually change the status of **PA0** by connecting it between **GND** and **VDD** points on the board.

---

### Hints:
- **PA0 should be configured as an input pin.**
- To read from **PA0**, your code must access the **PORT_A input data register (IDR)**.

---

### Step-by-Step Explanation

#### 1. **Configure PA0 as an Input Pin**
- The GPIO port **PA0** must be set to input mode in the **GPIO_MODER register**.
- Ensure the **PUPDR register** is set correctly (e.g., enabling internal pull-up or pull-down resistors if needed).

#### 2. **Configure PD12 as an Output Pin**
- The GPIO port **PD12** must be set to output mode in the **GPIO_MODER register**.

#### 3. **Read PA0 Input Data Register (IDR)**
- Check the value of the **PA0 pin** from the **GPIOA->IDR** register.
- If **PA0 is HIGH**, set **PD12 HIGH** (turn on the LED).
- If **PA0 is LOW**, set **PD12 LOW** (turn off the LED).

---

### Code Implementation

```c
#include "stm32f4xx.h"  // Include STM32 HAL header

void GPIO_Config(void);
void delay(void);

int main(void) {
    GPIO_Config(); // Configure GPIO Pins
    
    while (1) {
        if (GPIOA->IDR & (1 << 0)) {  // Read PA0 input status
            GPIOD->ODR |= (1 << 12);  // Set PD12 HIGH (Turn ON LED)
        } else {
            GPIOD->ODR &= ~(1 << 12); // Set PD12 LOW (Turn OFF LED)
        }
    }
}

void GPIO_Config(void) {
    RCC->AHB1ENR |= (1 << 0);  // Enable GPIOA clock
    RCC->AHB1ENR |= (1 << 3);  // Enable GPIOD clock
    
    GPIOA->MODER &= ~(3 << (0 * 2));  // Set PA0 as input mode
    
    GPIOD->MODER &= ~(3 << (12 * 2));
    GPIOD->MODER |= (1 << (12 * 2));  // Set PD12 as output mode
}

void delay(void) {
    for (volatile int i = 0; i < 500000; i++); // Simple delay loop
}
```

---

### Explanation of the Code
1. **Enable GPIO Clocks**
   - `RCC->AHB1ENR |= (1 << 0);` → Enables **GPIOA** clock.
   - `RCC->AHB1ENR |= (1 << 3);` → Enables **GPIOD** clock.

2. **Configure PA0 as Input**
   - `GPIOA->MODER &= ~(3 << (0 * 2));` → Clears **PA0 mode bits** to **set it as an input**.

3. **Configure PD12 as Output**
   - `GPIOD->MODER &= ~(3 << (12 * 2));` → Clears previous mode bits.
   - `GPIOD->MODER |= (1 << (12 * 2));` → Sets **PD12** as an **output**.

4. **Read PA0 and Control PD12**
   - `if (GPIOA->IDR & (1 << 0))` → Checks if **PA0 is HIGH**.
   - `GPIOD->ODR |= (1 << 12);` → Turns **ON** the LED.
   - `GPIOD->ODR &= ~(1 << 12);` → Turns **OFF** the LED if PA0 is LOW.

5. **Infinite While Loop**
   - The program continuously checks the status of **PA0** and updates **PD12** accordingly.

---

### Expected Behavior
- When **PA0 is HIGH**, **PD12 LED turns ON**.
- When **PA0 is LOW**, **PD12 LED turns OFF**.
- Manually changing **PA0** between **GND (LOW)** and **VDD (HIGH)** controls the LED state.

---

### Conclusion
- You have learned how to read a **GPIO pin (PA0)**.
- You have used an **if condition** to check input status.
- You have controlled an **LED (PD12)** based on the **PA0 status**.
- This is a fundamental skill in **embedded systems programming**!

---

### Further Exercises
1. Modify the code to toggle **PD12** instead of turning it ON/OFF.
2. Add a **debounce mechanism** to prevent unwanted toggling due to noise.
3. Use an **interrupt-based** approach instead of polling.
4. Implement a **button press counter** that counts the number of times PA0 is HIGH.

