# Preprocessor
```c++
#include <iostream>

#define MY_NAME "Alex"
#define COMPILE

int main() 
{
#ifdef COMPILE
	std::cout << MY_NAME; // this will get printed
#endif

#ifdef COMPILE2
	std::cout << MY_NAME; // This is not printed
#endif

	return 0;
}
```

# Header files
Contains all the forward declaration. To create a header file, create a file that has an extension of `.h`. The name of this file should be the same as the `.cpp` file. Header files you wrote are wrap in double quotes, while standard library are wrap in `< >`.
- Always include header guards (we’ll cover these next lesson).
- Do not define variables and functions in header files (for now).
- Give a header file the same name as the source file it’s associated with (e.g. `grades.h` is paired with `grades.cpp`).
- Each header file should have a specific job, and be as independent as possible. For example, you might put all your declarations related to functionality A in A.h and all your declarations related to functionality B in B.h. That way if you only care about A later, you can just include A.h and not get any of the stuff related to B.
- Be mindful of which headers you need to explicitly include for the functionality that you are using in your code files, to avoid inadvertent transitive includes.
- A header file should #include any other headers containing functionality it needs. Such a header should compile successfully when #included into a .cpp file by itself.
- Only #include what you need (don’t include everything just because you can).
- Do not #include .cpp files.
- Prefer putting documentation on what something does or how to use it in the header. It’s more likely to be seen there. Documentation describing how something works should remain in the source files.


main.cpp
```c++
/*
1. The paired header file
2. Other headers from your project
3. 3rd party library headers
4. Standard library headers
*/

#include "add.h"
#inclde <iostream>

int main()
{
	std::cout << add(2, 3);
	return 0;
}
```

add.cpp
```c++
#include "add.h"

int add(int x, int y)
{
	return x + y;
}
```

add.h
```c++
// Header guard

// Forward declarations here
int add(int x, int y);
```


# Header guards
Header guards are designed to ensure that the contents of a given header file are not copied more than once into any single file, in order to prevent duplicate definitions.

square.h
```c++
// you can use `#pragma once` here instead of this ifndef, define, endif.
#ifndef SQUARE_H
#define SQUARE_H

int getSquareSides();
int getSquarePerimeter(int sideLength);

#endif
```

square.cpp
```c++
#include "square.h"

int getSquareSides()
{
	return 4;
}

int getSquarePerimeter(int sideLength)
{
	return sideLength * getSquareSides();
}
```

main.cpp
```c++
#include "square.h"
#inclde <iostream>

int main()
{
	std::cout << getSquareSides() << std::endl;
	std::cout << getSquarePerimeter(4) << std::endl;
	return 0;
}
```