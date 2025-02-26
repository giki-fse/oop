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

#### **Advantages of Dynamic Memory Allocation**
1. **Efficient Use of Memory**: Allocates only the required memory, reducing wastage.
2. **Flexibility**: Enables handling of variable-sized data structures.
3. **Prevents Stack Overflow**: Large objects can be stored in heap memory instead of consuming stack space.

#### **Potential Issues and Solutions**
1. **Memory Leaks**: Occur when allocated memory is not deallocated properly. Always use `delete` or `delete[]` when memory is no longer needed.
2. **Dangling Pointers**: A pointer that still points to deallocated memory. Solution: Set pointers to `nullptr` after deletion.
3. **Fragmentation**: Multiple small allocations may lead to inefficient memory usage. Solution: Optimize allocation and deallocation patterns.

#### **Conclusion**
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

## Lab 4: Pointers - II & Bitwise operators and Bit Fields

### Objectives

After completing this lab, you should be able to:
*   Understand and use the common bitwise operators: AND (`&`), OR (`|`), XOR (`^`), NOT (`~`), left shift (`<<`), and right shift (`>>`).
*   Apply bitwise operators to set, clear, toggle, and test individual bits.
*   Define and use bit fields within structures to optimize memory usage.
*   Combine bitwise operators and bit fields for efficient data representation and manipulation.
*   Understand the implications of bit field layout and portability.
*   Use bitwise operations for tasks like setting flags, manipulating masks, and working with binary data.
*   Declare and define pointer functions.
*   Pass pointer functions as arguments to other functions.
*   Return pointer functions from functions.
*   Use function pointers to invoke functions indirectly.

### Pointer Functions in C++

#### Introduction

Pointer functions are powerful tools that allow you to pass functions as arguments to other functions, return functions from functions, and store function addresses for later invocation.  This enhances code flexibility and modularity.

#### Background

A function pointer stores the memory address of a function.  This address can then be used to call the function indirectly.  The declaration of a function pointer must match the signature (return type and parameter types) of the function it will point to.


#### Exercise 1: Basic Function Pointer

1.  **Code:**
```cpp
#include <iostream>

int add(int a, int b) {
    return a + b;
}

int main() {
    int (*funcPtr)(int, int) = add; // Declare and initialize function pointer
    int result = funcPtr(5, 3);      // Call function through the pointer
    std::cout << "Result: " << result << std::endl; // Output: Result: 8
    return 0;
}
```

2.  **Explanation:**
    *   `int (*funcPtr)(int, int);` declares `funcPtr` as a pointer to a function that takes two integers and returns an integer.  The parentheses around `*funcPtr` are crucial.
    *   `int (*funcPtr)(int, int) = add;` initializes `funcPtr` to point to the `add` function.
    *   `int result = funcPtr(5, 3);` calls the `add` function indirectly through `funcPtr`.

#### Exercise 2: Passing Function Pointers as Arguments

1.  **Code:**

```cpp
#include <iostream>

int operate(int a, int b, int (*operation)(int, int)) {
    return operation(a, b);
}

int add(int a, int b) { return a + b; }
int multiply(int a, int b) { return a * b; }

int main() {
    int result1 = operate(5, 3, add);       // Pass 'add' function
    int result2 = operate(5, 3, multiply);  // Pass 'multiply' function
    std::cout << "Result 1: " << result1 << std::endl; // Output: Result 1: 8
    std::cout << "Result 2: " << result2 << std::endl; // Output: Result 2: 15
    return 0;
}
```

2.  **Explanation:**
    *   The `operate` function takes a function pointer as an argument.
    *   Different functions (`add`, `multiply`) can be passed to `operate` to perform different operations.

#### Exercise 3: Array of Function Pointers

1.  **Code:**

```cpp
#include <iostream>

int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }
int multiply(int a, int b) { return a * b; }

int main() {
    int (*operations[3])(int, int) = {add, subtract, multiply};
    for (int i = 0; i < 3; i++) {
      std::cout << operations[i](10, 5) << std::endl;
    }
    return 0;
}
```

2.  **Explanation:** An array of function pointers is created, allowing you to store and access multiple functions through the array.

#### Exercise 4: Returning Function Pointers (Advanced)

1.  **Code:**

```cpp
#include <iostream>

int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }

int (*getOperation(char op))(int, int) {
    if (op == '+') {
        return add;
    } else if (op == '-') {
        return subtract;
    } else {
        return nullptr; // Or handle the error appropriately
    }
}

int main() {
    int (*func)(int, int) = getOperation('+');
    if(func != nullptr){
        int result = func(7, 2);
        std::cout << "Result: " << result << std::endl; // Output: Result: 9
    }
    return 0;
}
```

2.  **Explanation:** The `getOperation` function returns a function pointer based on the input character.

#### Conclusion

Pointer functions provide a powerful mechanism for dynamic function invocation and code reuse.  Understanding and using them effectively is essential for writing flexible and modular C++ programs.

### Bitwise Operators and Bit Fields

#### Introduction

Bitwise operators allow you to manipulate individual bits within integral data types, while bit fields provide a way to define structure members that occupy a specific number of bits. These techniques are crucial for low-level programming, memory optimization, and hardware interaction.

#### Background

Bitwise operators work directly on the binary representation of data.  They are essential for tasks like manipulating hardware registers, implementing network protocols, and optimizing performance.  Bit fields allow you to control the precise number of bits used to store a member variable within a structure, which can be useful when memory is limited or when working with hardware that requires specific data layouts.

#### Exercise 1: Bitwise AND (`&`)

1.  **Code:**

```cpp
#include <iostream>

int main() {
    int x = 10; // Binary: 1010
    int y = 6;  // Binary: 0110
    int result = x & y; // Binary: 0010 (2 in decimal)
    std::cout << "Result: " << result << std::endl; // Output: Result: 2
    return 0;
}
```

2.  **Explanation:** The AND operator sets a bit in the result only if the corresponding bits in both operands are set.

#### Exercise 2: Bitwise OR (`|`)

1.  **Code:**
```cpp
#include <iostream>

int main() {
    int x = 10; // Binary: 1010
    int y = 6;  // Binary: 0110
    int result = x | y; // Binary: 1110 (14 in decimal)
    std::cout << "Result: " << result << std::endl; // Output: Result: 14
    return 0;
}
```

2.  **Explanation:** The OR operator sets a bit in the result if at least one of the corresponding bits in the operands is set.

#### Exercise 3: Bitwise XOR (`^`)

1.  **Code:**
```cpp
#include <iostream>

int main() {
    int x = 10; // Binary: 1010
    int y = 6;  // Binary: 0110
    int result = x ^ y; // Binary: 1100 (12 in decimal)
    std::cout << "Result: " << result << std::endl; // Output: Result: 12
    return 0;
}
```

2.  **Explanation:** The XOR operator sets a bit in the result if the corresponding bits in the operands are different.

#### Exercise 4: Bitwise NOT (`~`)

1.  **Code:**

```cpp
#include <iostream>

int main() {
    int x = 10; // Binary: 1010
    int result = ~x; // Binary: ...0101 (implementation-dependent, usually -11)
    std::cout << "Result: " << result << std::endl; // Output: Result: -11 (or similar)
    return 0;
}
```

2.  **Explanation:** The NOT operator inverts all the bits of the operand.  The result is implementation-dependent due to how negative numbers are represented.

#### Exercise 5: Left Shift (`<<`)

1.  **Code:**

```cpp
#include <iostream>

int main() {
    int x = 10; // Binary: 1010
    int result = x << 2; // Binary: 101000 (40 in decimal)
    std::cout << "Result: " << result << std::endl; // Output: Result: 40
    return 0;
}
```

2.  **Explanation:** The left shift operator shifts the bits of the operand to the left by the specified number of positions.  This effectively multiplies the value by 2 raised to the power of the shift amount.

#### Exercise 6: Right Shift (`>>`)

1.  **Code:**

```cpp
#include <iostream>

int main() {
    int x = 10; // Binary: 1010
    int result = x >> 2; // Binary: 0010 (2 in decimal)
    std::cout << "Result: " << result << std::endl; // Output: Result: 2
    return 0;
}
```

2.  **Explanation:** The right shift operator shifts the bits of the operand to the right by the specified number of positions.  This effectively divides the value by 2 raised to the power of the shift amount.  Be aware of the difference between arithmetic and logical right shifts (the behavior depends on whether the most significant bit is replicated or filled with 0s).

#### Exercise 7: Bit Fields

1.  **Code:**

```cpp
#include <iostream>

struct Flags {
    unsigned int isReady : 1;
    unsigned int isActive : 1;
    unsigned int errorCode : 4;
};

int main() {
    Flags flags;
    flags.isReady = 1;
    flags.isActive = 0;
    flags.errorCode = 5;
    std::cout << "Is Ready: " << flags.isReady << std::endl; // Output: Is Ready: 1
    std::cout << "Is Active: " << flags.isActive << std::endl; // Output: Is Active: 0
    std::cout << "Error Code: " << flags.errorCode << std::endl; // Output: Error Code: 5
    return 0;
}
```

2.  **Explanation:**  The `Flags` structure uses bit fields to define members with specific bit widths.  This allows you to pack multiple small values into a single storage unit.

`flags` uses only 6 bits in total, saving memory compared to using full int variables.

#### Conclusion

Bitwise operators and bit fields are essential tools for low-level programming and optimization.  Understanding how to use them effectively allows you to manipulate data at the bit level, which is crucial for many applications.

## Lab 5: Preprocessors

**Objective:** To understand and effectively use C++ preprocessors for code manipulation, conditional compilation, and macro definitions.

### Preprocessors Introduction:

The C++ preprocessor is a powerful tool that operates on your source code *before* it's compiled.  It's responsible for tasks like:

* Macro substitution: Replacing symbolic names with their values.
* File inclusion: Bringing in the contents of other files.
* Conditional compilation: Compiling specific code blocks based on conditions.

Preprocessor directives always start with a `#`.

### 1. Macro Definitions (#define):**

Macros are used to define constants, functions (though inline functions are often preferred now), or code snippets.

#### **Examples:**
```cpp
#include <iostream>

// Defining a constant macro
#define PI 3.14159

// Defining a function-like macro (use with caution, can have unexpected side effects)
#define SQUARE(x) ((x) * (x)) // Parentheses are crucial!

// Defining a multi-line macro
#define PRINT_HELLO_WORLD() \
    std::cout << "Hello, World!" << std::endl; \
    std::cout << "This is a test." << std::endl;

int main() {
    double radius = 5.0;
    double area = PI * SQUARE(radius);  // Macro substitution happens here

    std::cout << "Area: " << area << std::endl;

    PRINT_HELLO_WORLD();

    return 0;
}
```

**Explanation:**

* `#define PI 3.14159`:  Replaces all occurrences of `PI` with `3.14159` before compilation.
* `#define SQUARE(x) ((x) * (x))`: Defines a macro for squaring a number.  The extra parentheses are *extremely* important to avoid operator precedence issues.  `SQUARE(a+b)` would become `((a+b) * (a+b))` with the parentheses, but `(a+b * a+b)` without, leading to incorrect results.
* `#define PRINT_HELLO_WORLD()`:  A multi-line macro. The backslashes `\` at the end of each line are essential for indicating that the macro definition continues on the next line.

### **2. File Inclusion (#include):**

The `#include` directive is used to include the contents of other files, typically header files (`.h` or `.hpp`).

**Examples:**

```cpp
#include <iostream> // Standard input/output library
#include <string>   // String manipulation library
#include "my_header.h" // User-defined header file (in the same directory)
#include "include/another_header.h" // User-defined header file in a subdirectory

int main() {
    std::cout << "Hello from main!" << std::endl;
    // ... use functions/classes from included headers ...
    return 0;
}
```

**Explanation:**

* `#include <iostream>`: Includes the `iostream` header file from the standard library.  Angle brackets `<>` are used for standard library headers.
* `#include "my_header.h"`: Includes a user-defined header file. Double quotes `""` are used for user-defined headers.  The compiler searches for these in the current directory (or directories specified by compiler flags).

### **3. Conditional Compilation (#if, #elif, #else, #endif, #ifdef, #ifndef):**

Conditional compilation allows you to include or exclude code blocks based on certain conditions. This is useful for:

* Platform-specific code: Compiling different code for Windows, macOS, or Linux.
* Debugging: Including debugging code only when needed.
* Feature toggles: Enabling or disabling features at compile time.

**Examples:**

```cpp
#include <iostream>

#define DEBUG // Define DEBUG to enable debugging code

int main() {
    #ifdef DEBUG
        std::cout << "Debugging enabled." << std::endl;
        int x = 10;
        std::cout << "Value of x: " << x << std::endl;
    #endif

    #ifndef RELEASE // If RELEASE is NOT defined
        std::cout << "This is a development build." << std::endl;
    #else
        std::cout << "This is a release build." << std::endl;
    #endif

    #if defined(_WIN32) || defined(_WIN64) // Windows-specific code
        std::cout << "Running on Windows." << std::endl;
    #elif defined(__linux__) // Linux-specific code
        std::cout << "Running on Linux." << std::endl;
    #else
        std::cout << "Running on an unknown platform." << std::endl;
    #endif


    return 0;
}
```

**Explanation:**

* `#ifdef DEBUG`: Checks if the macro `DEBUG` is defined.  The code within the `#ifdef` and `#endif` block is only compiled if `DEBUG` is defined.
* `#ifndef RELEASE`: Checks if the macro `RELEASE` is *not* defined.
* `#if defined(_WIN32) || defined(_WIN64)`: Checks if either `_WIN32` or `_WIN64` is defined (these are often predefined by Windows compilers).  You can use logical operators (`&&`, `||`, `!`) in `#if` conditions.
* `#elif`:  Short for "else if," allows you to check multiple conditions.
* `#else`: Provides a default case if none of the preceding conditions are met.
* `#endif`: Marks the end of a conditional compilation block.

### **4. Other Preprocessor Directives:**

* `#undef`: Undefines a previously defined macro.  `#undef PI` would remove the definition of the `PI` macro.
* `#pragma`: Compiler-specific directives that can be used for various purposes (e.g., controlling warnings, optimizing code).  These are not standardized, so their behavior can vary between compilers.  Example: `#pragma once` (often used in header files to prevent multiple inclusions).
* `#error`:  Generates a compiler error message.  `#error "This feature is not yet implemented."`

**Best Practices:**

* Use meaningful names for macros.
* Parenthesize macro arguments to avoid unexpected behavior.
* Avoid overly complex macros; they can make code harder to read and debug.
* Prefer `const` for constant values and `inline` functions for simple functions when possible – they offer type safety and better integration with the compiler.
* Use conditional compilation judiciously.
* Document your macros and preprocessor directives clearly.

### **Exercises:**

1. Create a macro to calculate the volume of a cylinder.
2. Use conditional compilation to compile different code blocks for different operating systems (e.g., Windows, Linux, macOS).
3. Create a header file with macro definitions and include it in your main program.
4. Experiment with `#pragma once` to prevent multiple inclusions of a header file.
5. Use `#error` to halt compilation if a required condition is not met.

