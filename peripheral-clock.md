## Enabling Peripheral Clock

### How to Enable the Peripheral Clock?
1. **Through peripheral clock control registers of the Microcontroller**
2. **In STM32 MCU, all clock control registers are mapped at the below address range in the memory map of the Microcontroller:**
   
   ```plaintext
   0x4002 3800 - 0x4003 BFFF | RCC -> Reset & clock control
   ```

---

## Calculating Peripheral Register Addresses

### Step-by-Step Guide to LED ON Exercise Coding

As a beginner in embedded systems programming, follow this structured approach to mastering the process of turning on an LED using STM32 microcontrollers.

### 1) Identify the GPIO Port Used to Connect the LED (GPIOD)
- Each GPIO port has specific registers associated with it.
- Reference the STM32 datasheet to determine the GPIO port your LED is connected to.

### 2) Identify the GPIOD Pin Where the LED is Connected
- Locate the specific pin of the GPIOD where your LED is wired.

### 3) Activate the GPIOD Peripheral (Enable the Clock)
- **Important:** Until you enable the clock for a peripheral, it remains inactive and does not accept any configuration commands.
- For STM32F4 series, enabling the clock involves modifying the **RCC_AHB1ENR** register.

```c
// Enable clock for GPIOD
#define RCC_AHB1ENR   (*(volatile uint32_t*)0x40023830)
#define GPIODEN       (1 << 3)  // Enable bit for GPIOD

void enable_GPIOD_clock() {
    RCC_AHB1ENR |= GPIODEN;
}
```

### 4) Configure the GPIOD Pin Mode as Output
- Modify the **GPIOx_MODER** register to set the pin mode to output.

```c
#define GPIOD_BASE     (0x40020C00)
#define GPIOD_MODER    (*(volatile uint32_t*)(GPIOD_BASE + 0x00))
#define GPIOD_PIN      12  // Example: LED connected to GPIOD Pin 12

void configure_GPIOD_pin() {
    GPIOD_MODER |= (1 << (GPIOD_PIN * 2));  // Set mode as output
}
```

### 5) Write to the GPIO Pin
- Use the **GPIOx_ODR** register to turn the LED on or off.

```c
#define GPIOD_ODR      (*(volatile uint32_t*)(GPIOD_BASE + 0x14))

void turn_on_LED() {
    GPIOD_ODR |= (1 << GPIOD_PIN);  // Set bit to turn LED ON
}

void turn_off_LED() {
    GPIOD_ODR &= ~(1 << GPIOD_PIN); // Clear bit to turn LED OFF
}
```

### 6) Complete Embedded C Program for LED ON

```c
#include <stdint.h>

// Define necessary registers and bit positions
#define RCC_AHB1ENR   (*(volatile uint32_t*)0x40023830)
#define GPIODEN       (1 << 3)
#define GPIOD_BASE    (0x40020C00)
#define GPIOD_MODER   (*(volatile uint32_t*)(GPIOD_BASE + 0x00))
#define GPIOD_ODR     (*(volatile uint32_t*)(GPIOD_BASE + 0x14))
#define GPIOD_PIN     12

void enable_GPIOD_clock() {
    RCC_AHB1ENR |= GPIODEN;
}

void configure_GPIOD_pin() {
    GPIOD_MODER |= (1 << (GPIOD_PIN * 2));
}

void turn_on_LED() {
    GPIOD_ODR |= (1 << GPIOD_PIN);
}

int main() {
    enable_GPIOD_clock();   // Enable clock for GPIOD
    configure_GPIOD_pin();  // Set pin mode as output
    turn_on_LED();          // Turn on LED
    while (1);
    return 0;
}
```

### Summary
- **Step 1:** Enable the clock for the GPIOD peripheral.
- **Step 2:** Configure the corresponding GPIO pin as an output.
- **Step 3:** Write a value to the output data register to turn the LED ON.


