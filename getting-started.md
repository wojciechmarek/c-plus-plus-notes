# Getting started

## function and arguments naming
```cpp
// function declaration (optional) - just saying the function with given name exists further in the code
// int, int - known as the formal arguments 
int multiply(int, int);

void main()
{
    // 4, 2 - known as actual arguments
    int result = multiply(4, 2);
}

// function definition - creation and code implementation
// int a, int b - known as the formal arguments
int multiply(int a, int b)
{
    return a * b;
}
```

## include

Including the library in the C programming language:

```c
#include <stdio.h>
// or
#include "stdio.h"
```

Including the library from the C programming language in  C++:

```cpp
#include <cstdio> // prefix c before the library name, without .h
```

Including the library in the C++ programming language:

```cpp
#include <iostream>
```

## main() arguments

The most basic main (no arguments version):

```cpp
int main() { } 
```

Version used usually when the program is run from the console:

```cpp
int main(int argc, char *argv[]) { }
// or
int main(int argc, char **argv) { }
```

Most advanced version aka the full-main version, used mainly in the programs working under the Linux control:

```cpp
int main(int argc, char *argv[], char *envp[]) { }
// or
int main(int argc, char **argv, char **envp) { }
```

Description:
- **argc** - amount of passed arguments, useful in the for loop,
- **argv** - list of passed arguments,
- **argc** - list of environment variables.