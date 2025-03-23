# Scanf and Scanset in C

## `scanf()` Function in C

The `scanf()` function is used for taking formatted input from the standard input (keyboard). It reads data according to the specified format specifiers.

### Syntax:
```c
int scanf(const char *format, ...);
```

### Example:
```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    printf("You entered: %d\n", num);
    return 0;
}
```

## Scanset (`[^ ]`) in `scanf()`

The `scanf()` function provides a scanset feature using `[^ ]` to define a set of characters that should or should not be read.

### Example:
```c
#include <stdio.h>

int main() {
    char str[50];
    printf("Enter a string without spaces: ");
    scanf("%[^\n]", str); // Reads everything until newline
    printf("You entered: %s\n", str);
    return 0;
}
```

---

# Student Records Management System

## Problem Statement
Write a C program to manage student records with the following features:
- Display all records
- Add a new record
- Delete a record
- Prevent duplication of records
- Alert when no space is available for a new record
- Alert when attempting to delete an unknown record

## Code Implementation:
```c
#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 10

typedef struct {
    char name[50];
    int id;
    float grade;
} Student;

Student students[MAX_STUDENTS];
int count = 0;

// Function to add a student
void addStudent() {
    if (count >= MAX_STUDENTS) {
        printf("No space to add a new record!\n");
        return;
    }
    
    Student newStudent;
    printf("Enter Name: ");
    scanf("%s", newStudent.name);
    printf("Enter ID: ");
    scanf("%d", &newStudent.id);
    printf("Enter Grade: ");
    scanf("%f", &newStudent.grade);
    
    // Check for duplicate ID
    for (int i = 0; i < count; i++) {
        if (students[i].id == newStudent.id) {
            printf("Error: Duplicate student record!\n");
            return;
        }
    }
    
    students[count++] = newStudent;
    printf("Student added successfully!\n");
}

// Function to display student records
void displayStudents() {
    if (count == 0) {
        printf("No records available.\n");
        return;
    }
    
    printf("\nStudent Records:\n");
    for (int i = 0; i < count; i++) {
        printf("Name: %s, ID: %d, Grade: %.2f\n", students[i].name, students[i].id, students[i].grade);
    }
}

// Function to delete a student record
void deleteStudent() {
    if (count == 0) {
        printf("No records to delete.\n");
        return;
    }
    
    int id;
    printf("Enter ID to delete: ");
    scanf("%d", &id);
    
    for (int i = 0; i < count; i++) {
        if (students[i].id == id) {
            // Shift records left
            for (int j = i; j < count - 1; j++) {
                students[j] = students[j + 1];
            }
            count--;
            printf("Record deleted successfully!\n");
            return;
        }
    }
    printf("Error: Record not found!\n");
}

// Main function
int main() {
    int choice;
    do {
        printf("\nStudent Record System\n");
        printf("1. Add Student\n");
        printf("2. Display Records\n");
        printf("3. Delete Student\n");
        printf("4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1: addStudent(); break;
            case 2: displayStudents(); break;
            case 3: deleteStudent(); break;
            case 4: printf("Exiting program...\n"); break;
            default: printf("Invalid choice!\n");
        }
    } while (choice != 4);
    
    return 0;
}
```

## Explanation:
1. **Adding a Student:**
   - The user inputs name, ID, and grade.
   - The program checks for duplicate ID before adding the record.
   - If the record list is full, an error message is displayed.

2. **Displaying Student Records:**
   - Lists all student records stored in the system.
   - If no records exist, it informs the user.

3. **Deleting a Student Record:**
   - The user inputs an ID to delete.
   - If the ID exists, the record is deleted, and the remaining records are shifted.
   - If the ID is not found, an error message is shown.

## Edge Cases Handled:
- Prevents adding duplicate records.
- Displays an alert when memory is full.
- Ensures records cannot be deleted if the list is empty.
- Prevents deletion of non-existing records.

---

This program provides a simple but effective way to manage student records using arrays and `scanf()` in C.
