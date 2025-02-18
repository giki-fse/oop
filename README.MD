# CS112 Lab Material

## Lab 01: User-Defined Data Types - I (struct, union and enum)

## Lab 02: User-Defined Data Types - II (nested struct)


## Lab 03: Pointers

### Objective:

To understand and implement the concepts of pointers in C++, including pointer arithmetic, dynamic memory allocation, and pointer functions.

---

### **Introduction to Pointers**

A pointer is a variable that stores the memory address of another variable. Pointers are essential for dynamic memory allocation, efficient array manipulation, and passing arguments by reference to functions.

### Basic Pointer Declaration and Dereferencing



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
#### **Aim:**
To declare a pointer, store the address of a variable, and access the value using the pointer.

#### **Code:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int *ptr = &a; // Pointer declaration and initialization
    
    cout << "Value of a: " << a << endl;
    cout << "Address of a: " << &a << endl;
    cout << "Pointer ptr holds address: " << ptr << endl;
    cout << "Value at ptr: " << *ptr << endl; // Dereferencing
    
    return 0;
}
```

#### **Expected Output:**
```
Value of a: 10
Address of a: 0x61ff08  (example address)
Pointer ptr holds address: 0x61ff08
Value at ptr: 10
```

---

### **Pointer Arithmetic**

#### **Aim:**
To demonstrate pointer arithmetic operations like increment and decrement.

#### **Code:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30, 40};
    int *ptr = arr;
    
    cout << "First element: " << *ptr << endl;
    ptr++;
    cout << "Second element: " << *ptr << endl;
    ptr++;
    cout << "Third element: " << *ptr << endl;
    
    return 0;
}
```

#### **Expected Output:**
```
First element: 10
Second element: 20
Third element: 30
```

---

### **Pointer to a Structure**

#### **Aim:**
To create a structure and access its members using pointers.

#### **Code:**
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

#### **Expected Output:**
```
Student Name: John
Student Age: 20
```

---

### **Dynamic Memory Allocation in C++**

#### **Introduction**
Memory management is a crucial aspect of programming, particularly in languages like C++ that provide both automatic and manual memory management options. While automatic memory allocation occurs on the stack, dynamic memory allocation allows programs to request memory from the heap at runtime. This feature is especially useful when the amount of memory required is not known at compile time.

#### **Understanding Memory Allocation**
In C++, memory is divided into different sections:
1. **Stack**: Used for local variables and function calls; managed automatically by the compiler.
2. **Heap**: Used for dynamically allocated memory; managed manually by the programmer.

Dynamic memory allocation enables efficient memory usage and flexibility in handling data structures like arrays, linked lists, and trees.

#### **Dynamic Memory Allocation Using `new` and `delete`**
C++ provides the `new` and `delete` operators to allocate and deallocate memory dynamically:
- `new`: Allocates memory on the heap and returns a pointer to the allocated memory.
- `delete`: Frees the allocated memory, preventing memory leaks.

##### **Example: Allocating Memory for a Single Variable**
```cpp
#include <iostream>
using namespace std;

int main() {
    int* ptr = new int; // Allocates memory for an integer
    *ptr = 10; // Assigns value
    cout << "Value: " << *ptr << endl;
    delete ptr; // Frees allocated memory
    return 0;
}
```

#### **Dynamic Allocation for Arrays**
To allocate memory for arrays dynamically, the syntax is:
```cpp
int* arr = new int[5]; // Allocates an array of 5 integers
```

After using the array, memory should be freed using:
```cpp
delete[] arr;
```
Example:
```cpp
#include <iostream>
using namespace std;

int main() {
    int* arr = new int[5];
    for (int i = 0; i < 5; i++) {
        arr[i] = i * 10;
    }
    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    delete[] arr; // Deallocating memory
    return 0;
}
```

### **Advantages of Dynamic Memory Allocation**
1. **Efficient Use of Memory**: Allocates only the required memory, reducing wastage.
2. **Flexibility**: Enables handling of variable-sized data structures.
3. **Prevents Stack Overflow**: Large objects can be stored in heap memory instead of consuming stack space.

### **Potential Issues and Solutions**
1. **Memory Leaks**: Occur when allocated memory is not deallocated properly. Always use `delete` or `delete[]` when memory is no longer needed.
2. **Dangling Pointers**: A pointer that still points to deallocated memory. Solution: Set pointers to `nullptr` after deletion.
3. **Fragmentation**: Multiple small allocations may lead to inefficient memory usage. Solution: Optimize allocation and deallocation patterns.

### **Conclusion**
Dynamic memory allocation in C++ is a powerful tool for managing memory efficiently. By using `new` and `delete`, programmers can allocate and deallocate memory as needed. However, proper memory management is essential to avoid issues such as memory leaks and dangling pointers. Understanding these concepts ensures efficient and error-free programming, making C++ a robust language for system and application development.

---

| **Keyword/Symbol** | **Description** | **Example** |
|--------------------|----------------|-------------|
| `*` (Asterisk) | Declares a pointer variable or dereferences a pointer | `int *ptr;` (Declaration), `int val = *ptr;` (Dereferencing) |
| `&` (Address-of) | Gets the memory address of a variable | `ptr = &var;` |
| `->` (Arrow Operator) | Accesses members of a struct/class through a pointer | `ptr->member;` |
| `nullptr` | Represents a null pointer (C++11 and later) | `int *ptr = nullptr;` |
| `new` | Allocates memory dynamically | `ptr = new int;` |
| `delete` | Deallocates dynamically allocated memory | `delete ptr;` |
| `new[]` | Allocates an array dynamically | `ptr = new int[10];` |
| `delete[]` | Deallocates a dynamically allocated array | `delete[] ptr;` |
| `const` | Prevents modification through a pointer | `const int *ptr;` (Pointer to constant), `int *const ptr;` (Constant pointer) |
| `void*` | Generic pointer type (can point to any type) | `void *ptr;` |

---

### **Key Takeaways**

- **Pointers store addresses** of other variables.
- **Dereferencing a pointer** allows access to the stored value.
- **Pointer arithmetic** helps in navigating arrays efficiently.
- **Dynamic memory allocation** is achieved using `new` and deallocated using `delete`.
- **Function pointers** allow passing functions as parameters.
- **Pointers to structures** enable efficient access to structure members.
