# Passing value by reference

## int and other primitives

```cpp
#include <iostream>

void processData(int &value)
{
    value++;
}

int main()
{
    int magicNumber = 42;

    std::cout << "The magic number is: " << magicNumber << std::endl; // 42
    processData(magicNumber);
    std::cout << "The magic number after processing is: " << magicNumber << std::endl; // 43
}
```

## array

```cpp
#include <iostream>

void processData(int *array) // or: int array[]
{
    std::cout << array << std::endl; // array's address: 0x99d85ff930
    std::cout << *array << std::endl; // first element: 1
    std::cout << *array + 2 << std::endl; // third element: 3
}

int main()
{
    int magicArray[] = {1, 2, 3, 4, 5};

    processData(magicArray);
}
```

## string

```cpp
#include <iostream>

void processData(std::string &text) 
{
    // remember: string is inside the "std" namespace
    std::cout << text << std::endl;
}

int main()
{
    std::string magicText = "Greetings from the World"; 

    processData(magicText);
}
```

## array of chars - a C style string

```cpp
#include <iostream>

void processData(char *text) 
{
    std::cout << text << std::endl;
}

int main()
{
    // in C "strings" are represented by array of chars:
    char magicText[] = "Greetings from the Mars"; // here: char magicText[22]

    processData(magicText);
}
```

## object

```cpp
#include <iostream>

class Person {
    public:
    std::string firstName;
    std::string lastName;

    void sayHello() {
        std::cout << "Hello" << std::endl;
    }
};

void processData(Person &citizen) 
{
    std::cout << "Hello " << citizen.firstName << " " << citizen.lastName << std::endl;
    citizen.sayHello();
}

int main()
{
    Person person;
    person.firstName = "John";
    person.lastName = "Doe";

    processData(person);
}
```

## function

```cpp
#include <iostream>

int multiplyBy10(int value)
{
    return value * 10;
}

void processData(int (*functionPointer)(int))
{
    int result = functionPointer(2);
    std::cout << "This result is: " << result << std::endl;
}

int main()
{
    processData(multiplyBy10);
}
```