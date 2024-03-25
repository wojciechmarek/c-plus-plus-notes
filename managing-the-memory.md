# Managing the memory

## C style

Three main keywords: **malloc/calloc** and **free**.

- **malloc** - tries to allocate the memory, allocated memory is initialized by 0s, if cannot allocate returns NULL, returns generic pointer type: void* so developer has to cast into required type (eg. int*). Takes two arguments: amount of elements to allocate, size of single element.
- **calloc** - tries to allocate the memory, allocated memory is not initialized, if cannot allocate returns NULL, returns generic pointer type: void* so developer has to cast into required type (eg. int*). Takes one argument: total weight of bytes to allocate (or other words: items amount * weight of single item).

```cpp
#include <iostream>
#include <stdlib.h>

int main()
{
    // Memory allocating for single value:
    int *bestEmployee = (int *)calloc(1, sizeof(int));
    int *bestManager = (int *)malloc(sizeof(int));

    // Memory allocating for multiple value:
    int *employees = (int *)calloc(10, sizeof(int));
    int *managers = (int *)malloc(10 * sizeof(int));

    // NOTE: in the debugger visible is pointer address, not real values.

    // Assign values:
    *bestEmployee = 42;
    *bestManager = 420;

    for (int i = 0; i < 10; i++)
    {
        employees[i] = i; // or: *(employee + i) = i;
        managers[i] = i;  // or: *(managers + i) = i;
    };

    // Read values:
    std::cout << "Best employee value: " << *bestEmployee << std::endl; // 42
    std::cout << "Best manager value: " << *bestManager << std::endl;   // 420

    std::cout << "Sample employee value: " << *(employees + 3) << std::endl; // pointer style, returns: 3
    std::cout << "Employee value: " << managers[5] << std::endl;             // regular style, returns: 5

    // Cleaning the memory:
    free(bestEmployee);
    free(bestManager);
    free(employees);
    free(managers);
}
```

## C++ style

Two main keyword: **new** and **delete**.

```cpp
#include <iostream>

int main()
{
    // Memory allocating:
    int *boss = new int;            // only for 1 int
    int *employees = new int[1000]; // for 1000 integers

    // NOTE: in the debugger visible is pointer address, not real values.

    // Assign values:
    *boss = 42;

    for (int i = 0; i < 1000; i++)
    {
        employees[i] = i; // or: *(employee + i) = i;
    };

    // Read values:
    std::cout << "Boss value: " << *boss << std::endl; // 42

    std::cout << "Employee value: " << *(employees + 10) << std::endl; // pointer style, returns: 10
    std::cout << "Employee value: " << employees[20] << std::endl;     // regular style, returns: 20

    // Cleaning the memory:
    delete boss;
    delete[] employees;
}
```