# CS112 Lab Material

## Lab 01: User-Defined Data Types - I (struct, union and enum)

## Lab 02: User-Defined Data Types - II (nested struct)

## Lab 03: Pointers

### Objective:

To understand and implement the concepts of pointers in C++, including pointer arithmetic, dynamic memory allocation, and pointer functions.

---

### **Introduction to Pointers**

A pointer is a variable that stores the memory address of another variable. Pointers are essential for dynamic memory allocation, efficient array manipulation, and passing arguments by reference to functions.

#### **Pointer Declaration and Initialization**

In C++, a pointer is declared using an asterisk (`*`) before the variable name.

```cpp
int a = 10; // Normal integer variable
int *ptr;   // Pointer declaration
ptr = &a;   // Storing the address of 'a' in pointer
```

#### **Dereferencing a Pointer**

Dereferencing a pointer means accessing the value stored at the memory address it points to.

```cpp
cout << "Value of a: " << *ptr << endl; // Output: Value of a: 10
```

#### **Pointer Arithmetic**

Pointers allow arithmetic operations like increment (`++`), decrement (`--`), addition (`+`), and subtraction (`-`).

```cpp
int arr[] = {10, 20, 30};
int *p = arr; // Pointer to first element of array
cout << "First element: " << *p << endl;
p++;
cout << "Second element: " << *p << endl;
```

---

### **Lab Exercises**

#### **Exercise 1: Basic Pointer Operations**

**Task:** Declare an integer pointer, assign it the address of an integer variable, and print both the address and value using the pointer.

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 42;
    int *ptr = &num;
    cout << "Address of num: " << ptr << endl;
    cout << "Value at address: " << *ptr << endl;
    return 0;
}
```

#### **Exercise 2: Pointer Arithmetic**

**Task:** Use pointer arithmetic to access elements of an array.

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {5, 10, 15};
    int *ptr = arr;
    for (int i = 0; i < 3; i++) {
        cout << "Value at index " << i << " is: " << *(ptr + i) << endl;
    }
    return 0;
}
```

#### **Exercise 3: Dynamic Memory Allocation**

**Task:** Allocate memory dynamically for an integer and a float variable, assign values, and print them.

```cpp
#include <iostream>
using namespace std;

int main() {
    int *pInt = new int;   // Dynamically allocating memory for an integer
    float *pFloat = new float; // Dynamically allocating memory for a float
    *pInt = 25;
    *pFloat = 3.14;
    cout << "Dynamically allocated Integer: " << *pInt << endl;
    cout << "Dynamically allocated Float: " << *pFloat << endl;
    delete pInt;   // Freeing allocated memory
    delete pFloat;
    return 0;
}
```

#### **Exercise 4: Pointer to Function**

**Task:** Create a function and use a function pointer to call it.

```cpp
#include <iostream>
using namespace std;

void display() {
    cout << "Hello from function pointer!" << endl;
}

int main() {
    void (*funcPtr)(); // Function pointer declaration
    funcPtr = display; // Assigning function address to pointer
    funcPtr(); // Calling function using pointer
    return 0;
}
```

#### **Exercise 5: Pointer to Structure**

**Task:** Use a pointer to access structure members.

```cpp
#include <iostream>
using namespace std;

struct Student {
    string name;
    int age;
};

int main() {
    Student s1 = {"John", 20};
    Student *ptr = &s1;
    cout << "Student Name: " << ptr->name << endl;
    cout << "Student Age: " << ptr->age << endl;
    return 0;
}
```

---

### **Key Takeaways**

- **Pointers store addresses** of other variables.
- **Dereferencing a pointer** allows access to the stored value.
- **Pointer arithmetic** helps in navigating arrays efficiently.
- **Dynamic memory allocation** is achieved using `new` and deallocated using `delete`.
- **Function pointers** allow passing functions as parameters.
- **Pointers to structures** enable efficient access to structure members.
