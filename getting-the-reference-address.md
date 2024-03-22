# Getting th reference address

## int or other primitives

```cpp
#include <iostream>

int main()
{
    int magicNumber = 42;

    // creating a pointer - it references a location in memory of magicNumber
    int *magicPointer = &magicNumber;

    // dereferencing - obtaining (again) a value stored in the location
    int againNumber = *magicPointer;

    std::cout << magicNumber << std::endl;  // 42
    std::cout << magicPointer << std::endl; // 0x3e7cfff9f0
    std::cout << againNumber << std::endl;  // 42
}
```

## array

```cpp
#include <iostream>

int main()
{
    int arr[] = {1, 2, 3, 4, 5};

    // arr - returns a location in memory
    // *arr - returns a value of first element, the same: arr[0]
    // *(arr+i) - returns a value of i+1 element, the same: arr[i]
    // *arr+i - returns a value of first element and add i, the same: tab[0]+i

    std::cout << arr << std::endl;        // 0x1abd3ff710
    std::cout << *arr << std::endl;       // 1
    std::cout << *(arr + 3) << std::endl; // 4
    std::cout << *arr + 3 << std::endl;   // 4, because 1+3=4
}
```

## object

```cpp
#include <iostream>

class Person
{
public:
    std::string firstName;
    std::string lastName;

    void sayHello()
    {
        std::cout << "Hello" << std::endl;
    }
};

int main()
{
    Person person;
    person.firstName = "John";
    person.lastName = "Doe";

    // creating a pointer - it points to the person's address
    Person *personPointer = &person;

    // accessing the object's values using pointer object:
    std::cout << personPointer->firstName << std::endl;  // John
    std::cout << (*personPointer).lastName << std::endl; // Doe (arrow syntax is better)

    personPointer->sayHello();

    // NOTE: -> syntax allows to dereference object's value
}
```