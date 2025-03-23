# Switch Case Statement in C

## Syntax of Switch/Case Statement
```c
switch (expression)
{
    case value1: 
        // Statements for case value1
        break;
    
    case value2: 
        // Statements for case value2
        break;
    
    default:
        // Default statements if no case matches
}
```

### Example: Using Switch-Case in C
The following C program reads an input from a keypad and performs different LED operations based on the input.

```c
#include <stdio.h>
#include <stdint.h>

uint8_t read_keypad();  // Function prototype for reading keypad
void all_leds_race();   // Function prototype for LED race pattern
void all_leds_on();     // Function prototype for turning all LEDs on
void all_leds_toggle(); // Function prototype for toggling all LEDs
void all_leds_blink();  // Function prototype for blinking LEDs
void all_leds_off();    // Function prototype for turning all LEDs off

int main(void) 
{
    uint8_t key_read = read_keypad(); // Read input from keypad

    switch (key_read)
    {
        case 1: 
            all_leds_race();  // Execute LED race pattern
            break;

        case 2: 
            all_leds_on();  // Turn all LEDs on
            break;

        case 3: 
            all_leds_toggle();  // Toggle all LEDs
            break;

        case 4: 
            all_leds_blink();  // Blink LEDs
            break;

        default: 
            all_leds_off();  // Turn off all LEDs if input is invalid
            printf("Invalid key! Please enter a number between 1 to 4 only.\n");
    }
    return 0;
}
```
### Explanation:
1. The `switch` statement evaluates the value of `key_read`.
2. Each `case` represents a possible value of `key_read` (1 to 4).
3. When a case matches, the corresponding function is called.
4. `break` is used to exit the `switch` after a case is executed.
5. The `default` case handles invalid inputs.

---

## Switch Case Exercise

### Problem Statement:
Write a program to calculate the area of different geometrical figures: 
- Circle
- Triangle
- Trapezoid
- Square
- Rectangle

### Requirements:
- The program should prompt the user to enter a shape selection code.
- Based on the selection, the program should calculate and display the area.

### Example Implementation:
```c
#include <stdio.h>
#define PI 3.14159

int main() 
{
    int choice;
    float area;
    float base, height, radius, length, width, a, b;

    printf("Select the shape to calculate area:\n");
    printf("1. Circle\n");
    printf("2. Triangle\n");
    printf("3. Trapezoid\n");
    printf("4. Square\n");
    printf("5. Rectangle\n");
    printf("Enter your choice (1-5): ");
    scanf("%d", &choice);

    switch(choice) 
    {
        case 1: // Circle
            printf("Enter radius: ");
            scanf("%f", &radius);
            area = PI * radius * radius;
            printf("Area of Circle = %.2f\n", area);
            break;

        case 2: // Triangle
            printf("Enter base and height: ");
            scanf("%f %f", &base, &height);
            area = 0.5 * base * height;
            printf("Area of Triangle = %.2f\n", area);
            break;

        case 3: // Trapezoid
            printf("Enter base1, base2, and height: ");
            scanf("%f %f %f", &a, &b, &height);
            area = 0.5 * (a + b) * height;
            printf("Area of Trapezoid = %.2f\n", area);
            break;

        case 4: // Square
            printf("Enter side length: ");
            scanf("%f", &length);
            area = length * length;
            printf("Area of Square = %.2f\n", area);
            break;

        case 5: // Rectangle
            printf("Enter length and width: ");
            scanf("%f %f", &length, &width);
            area = length * width;
            printf("Area of Rectangle = %.2f\n", area);
            break;

        default:
            printf("Invalid choice! Please enter a number between 1 and 5.\n");
    }
    return 0;
}
```

### Explanation:
1. **User Input:**
   - The user selects a shape by entering a number between 1 and 5.
2. **Switch Case Execution:**
   - Based on the input, the corresponding `case` executes the appropriate formula.
3. **Area Calculation:**
   - The program calculates the area using predefined mathematical formulas.
4. **Break Statements:**
   - Each case ends with `break` to prevent fall-through behavior.
5. **Default Case:**
   - Handles invalid user input.

---

### Expected Output:
**Example 1:**
```
Select the shape to calculate area:
1. Circle
2. Triangle
3. Trapezoid
4. Square
5. Rectangle
Enter your choice (1-5): 2
Enter base and height: 5 10
Area of Triangle = 25.00
```

**Example 2:**
```
Select the shape to calculate area:
1. Circle
2. Triangle
3. Trapezoid
4. Square
5. Rectangle
Enter your choice (1-5): 6
Invalid choice! Please enter a number between 1 and 5.
