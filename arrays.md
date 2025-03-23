# Arrays in Embedded Systems Programming

## Introduction to Arrays in 'C'

An **array** is a collection of elements of the same data type stored in contiguous memory locations. It allows efficient storage and manipulation of multiple values using a single variable name.

### Array Declaration in 'C'
```c
int numbers[5]; // Declares an array of 5 integers
char letters[10]; // Declares an array of 10 characters
float temperatures[7]; // Declares an array of 7 floating-point numbers
```

### Array Initialization
```c
int numbers[5] = {1, 2, 3, 4, 5};
char vowels[] = {'a', 'e', 'i', 'o', 'u'};
float temperatures[3] = {36.5, 37.2, 38.1};
```

If an array is not fully initialized, the remaining elements are set to zero.

## Array Storage in Memory
Arrays are stored in contiguous memory locations, meaning the address of an element can be calculated using:

**Formula:**
```
Address of numbers[i] = Base Address + (i * Size of each element)
```

Example:
```c
int arr[3] = {10, 20, 30};
printf("Address of arr[0]: %p\n", &arr[0]);
printf("Address of arr[1]: %p\n", &arr[1]);
printf("Address of arr[2]: %p\n", &arr[2]);
```
This demonstrates how memory is allocated sequentially for array elements.

## Read and Write Operations on an Array
### Writing to an Array
```c
int data[5];
data[0] = 10;  // Assign 10 to first element
data[1] = 20;  // Assign 20 to second element
```

### Reading from an Array
```c
int x = data[0]; // Read first element
int y = data[1]; // Read second element
```

### Looping through an Array
```c
for(int i = 0; i < 5; i++) {
    printf("data[%d] = %d\n", i, data[i]);
}
```

## Passing an Array to a Function
When an array is passed to a function, only its reference (base address) is passed.

```c
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    printArray(numbers, 5);
    return 0;
}
```

## Swapping Arrays
Swapping arrays involves exchanging the contents of two arrays.

### Swapping Two Arrays Using a Temporary Array
```c
void swapArrays(int a[], int b[], int size) {
    int temp[size];
    for (int i = 0; i < size; i++) {
        temp[i] = a[i];
        a[i] = b[i];
        b[i] = temp[i];
    }
}
```

### Swapping Two Arrays Using Pointers
```c
void swapArrays(int *a, int *b, int size) {
    for (int i = 0; i < size; i++) {
        int temp = *(a + i);
        *(a + i) = *(b + i);
        *(b + i) = temp;
    }
}
```

### Example Usage
```c
int main() {
    int arr1[] = {1, 2, 3};
    int arr2[] = {4, 5, 6};
    swapArrays(arr1, arr2, 3);
}
```

## Conclusion
Arrays provide an efficient way to store and manipulate multiple values. Understanding memory storage, access operations, and passing arrays to functions is crucial for embedded systems programming. Proper handling of arrays enhances performance and optimizes memory usage.
