## While Loop in C

### Syntax:
```c
/* Multi-statement while loop */
while (expression)
{
    Statement1;
    Statement2;
    Statement3;
    StatementN;
}

/* Single-statement while loop */
while (expression)
    Statement1;
```

### Explanation:
- The execution of code inside the loop body repeats until the expression evaluates to `false (0)`.

### Flowchart for While Loop:
```text
 Start
  |
  v
Evaluate Expression --> [False] --> Exit Loop
  |
 [True]
  |
Execute Loop Body
  |
  v
Re-evaluate Expression
```

### While Loop Example - Printing Numbers from 1 to 10:
```c
#include <stdio.h>
#include <stdint.h>

void wait_for_user_input(void);

int main(void)
{
    uint8_t num = 1;
    while (num <= 10) {
        printf("%d\n", num++);
    }
    wait_for_user_input();
    return 0;
}
```

---

## While Loop and Semicolon:

### Incorrect Usage:
```c
while (num <= 10);
{
    printf("%d\n", num++);
}
```
**Explanation:**
- The semicolon (`;`) after the `while` loop causes an **empty loop**, so `printf()` never executes inside the loop.
- The correct form should be without the semicolon after `while(num <= 10)`.

### Forever Loop:
```c
int main(void)
{
    /* Super loop */
    while (1)
    {
        readDataSensor();
        processData();
        displaySensorData();
    }
}
```
**Explanation:**
- `while(1)` runs indefinitely, which is useful in embedded systems where programs must continuously run.

---

## While Loop Exercise - Print Even Numbers from 0 to 100:

```c
#include <stdio.h>

int main(void)
{
    int num = 0, count = 0;

    while (num <= 100)
    {
        printf("%d\n", num);
        num += 2;
        count++;
    }

    printf("Total even numbers: %d\n", count);
    return 0;
}
```

### Accepting User Input for Boundaries:
```c
#include <stdio.h>

int main(void)
{
    int lower, upper, num, count = 0;

    printf("Enter lower boundary: ");
    scanf("%d", &lower);
    printf("Enter upper boundary: ");
    scanf("%d", &upper);

    num = (lower % 2 == 0) ? lower : lower + 1; // Ensure num starts from an even number

    while (num <= upper)
    {
        printf("%d\n", num);
        num += 2;
        count++;
    }

    printf("Total even numbers: %d\n", count);
    return 0;
}
