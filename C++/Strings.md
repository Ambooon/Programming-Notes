
```c++
#include <string>

int main()
{
	std::string name{"Alex"};
	name = "Francis";
}
```


# std::getline
std::cin cut the string onto the first whitespace. getline allows as to input string with whitespaces
```c++
#include <iostream>
#include <string> // std::string, std::getine

int main()
{
	std::cout << "Enter your full name: ";
	std::string name{};
	std::getline(std::cin >> std::ws, name);
/*
If using `std::getline()` to read strings, use `std::cin >> std::ws` input manipulator to ignore leading whitespace. This needs to be done for each `std::getline()` call, as `std::ws` is not preserved across calls
*/
}
```


## String length
Also note that `std::string::length()` returns an unsigned integral value (most likely of type `size_t`). If you want to assign the length to an `int` variable, you should `static_cast` it to avoid compiler warnings about signed/unsigned conversions:
```cpp
#include <iostream>
#include <string>

int main()
{
    std::string name{ "Alex" };
    std::cout << name << " has " << name.length() << " characters\n";

    return 0;
}
```


## String literals
```cpp
#include <iostream>
#include <string> // for std::string

int main()
{
    using namespace std::string_literals; // easy access to the s suffix

    std::cout << "foo\n";   // no suffix is a C-style string literal
    std::cout << "goo\n"s;  // s suffix is a std::string literal

    return 0;
}
```


# std::string_view
std::string_view is a read-only.
Prefer `std::string_view` over `std::string` when you need a read-only string, especially for function parameters.

```cpp
#include <iostream>
#include <string_view> // C++17

// str provides read-only access to whatever argument is passed in
void printSV(std::string_view str) // now a std::string_view
{
    std::cout << str << '\n';
}

int main()
{
    std::string_view s{ "Hello, world!" }; // now a std::string_view
    printSV(s);

    return 0;
}
```


# std::string vs std::string_view

A quick guide on when to use `std::string` vs `std::string_view`
This guide is not meant to be comprehensive, but is intended to highlight the most common cases:

Use a `std::string` variable when:

- You need a string that you can modify.
- You need to store user-inputted text.
- You need to store the return value of a function that returns a `std::string`.

Use a `std::string_view` variable when:

- You need read-only access to part or all of a string that already exists elsewhere and will not be modified or destroyed before use of the `std::string_view` is complete.
- You need a symbolic constant for a C-style string.
- You need to continue viewing the return value of a function that returns a C-style string or a non-dangling `std::string_view`.

Use a `std::string` function parameter when:

- The function needs to modify the string passed in as an argument without affecting the caller. This is rare.
- You are using a language standard older than C++17.
- You meet the criteria of the pass-by-reference cases covered in lesson [12.5 -- Pass by lvalue reference](https://www.learncpp.com/cpp-tutorial/pass-by-lvalue-reference/).

Use a `std::string_view` function parameter when:

- The function needs a read-only string.

Use a `std::string` return type when:

- The return value is a `std::string` local variable.
- The return value is a function call or operator that returns a `std::string` by value.
- You meet the criteria of the return-by-reference cases covered in lesson [12.12 -- Return by reference and return by address](https://www.learncpp.com/cpp-tutorial/return-by-reference-and-return-by-address/).

Use a `std::string_view` return type when:

- The function returns a C-style string literal or local `std::string_view` that has been initialized with a C-style string literal.
- The function returns a `std::string_view` parameter.

Things to remember about `std::string`:

- Initializing and copying `std::string` is expensive, so avoid this as much as possible.
- Avoid passing `std::string` by value, as this makes a copy.
- If possible, avoid creating short-lived `std::string` objects.
- Modifying a `std::string` will invalidate any views to that string.

Things to remember about `std::string_view`:

- `std::string_view` is typically used for passing string function parameters and returning string literals.
- Because C-style string literals exist for the entire program, it is always okay to set a `std::string_view` to a C-style string literal.
- When a string is destroyed, all views to that string are invalidated.
- Using an invalidated view (other than using assignment to revalidate the view) will cause undefined behavior.
- A `std::string_view` may or may not be null-terminated.