# Managing the memory

## C style

Three main keywords: **malloc/calloc** and **free**.

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