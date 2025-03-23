# **`do while` Loop in C**

The **`do while` loop** is a control flow statement that executes a block of code at least once before evaluating the condition.

## **Syntax**
```c
do {
    // Statements to execute
} while (condition);
```

### **Key Features**
- Executes the loop body **at least once**, even if the condition is false.
- The condition is evaluated **after** the execution of the statements.

## **Flowchart**
```
START
  |
  v
Execute Statements → Evaluate Condition (True?) → Yes → Execute Again
                          ↓ 
                        No  
                          ↓  
                     EXIT LOOP  
```

---

## **Examples**

### **1. Basic `do while` Loop**
```c
#include <stdio.h>

int main() {
    int num = 1;
    do {
        printf("%d\n", num);
        num++;
    } while (num <= 5);
    
    return 0;
}
```
💡 *This prints numbers from 1 to 5.*

---

### **2. PIN Verification (ATM System)**
```c
#include <stdio.h>

int main() {
    int pin;
    int correct_pin = 1234;

    do {
        printf("Enter your PIN: ");
        scanf("%d", &pin);
    } while (pin != correct_pin);

    printf("Access Granted!\n");

    return 0;
}
```
💡 *User must enter the correct PIN to exit the loop.*

---

### **3. Infinite Loop Using `do while`**
```c
#include <stdio.h>

int main() {
    do {
        printf("This is an infinite loop.\n");
    } while (1);

    return 0;
}
```
💡 *Runs forever because `while (1)` is always true.*

---

### **4. Printing Even Numbers from 0 to 100**
```c
#include <stdio.h>

int main() {
    int num = 0, count = 0;

    do {
        printf("%d ", num);
        count++;
        num += 2;
    } while (num <= 100);

    printf("\nTotal even numbers: %d\n", count);

    return 0;
}
```
💡 *Prints all even numbers from 0 to 100 and counts them.*

---

## **`while` vs `do while` Loop**
| Feature | `while` Loop | `do while` Loop |
|---------|------------|----------------|
| Condition Check | Before execution | After execution |
| Executes at Least Once? | No | Yes |
| Example Usage | Menu navigation, sensor readings | PIN verification, loops needing first execution |

### **Example Comparison**
#### **Using `while` Loop**
```c
int num = 10;
while (num < 5) {
    printf("%d\n", num);
}
```
💡 *This loop never runs since `num < 5` is false initially.*

#### **Using `do while` Loop**
```c
int num = 10;
do {
    printf("%d\n", num);
} while (num < 5);
```
💡 *This prints `10` once before exiting.*

---

## **Common Mistakes**
### **1. Missing Semicolon**
🚫 Incorrect:
```c
do {
    printf("Hello\n");
} while (1)
```
✅ Correct:
```c
do {
    printf("Hello\n");
} while (1);
```

### **2. Unintentional Infinite Loop**
🚫 Incorrect:
```c
int i = 1;
do {
    printf("%d\n", i);
} while (i > 0);
```
✅ Correct:
```c
int i = 1;
do {
    printf("%d\n", i);
    i--;
} while (i > 0);
```

---

## **Conclusion**
- **`do while` ensures at least one execution** before checking the condition.
- **Common in user authentication, menu navigation, and continuous processes.**
- **Always remember the semicolon after `while(condition);`**.
