- Use "\n" instead of std::endl;
- std::cerr when debugging
- Initialize variable with value if you can
- Avoid using unsigned types

- Use compile-time constant
- Avoid the use of the `inline` keyword unless you have a specific, compelling reason to do so (e.g. you’re defining those functions or variables in a header file).

- Do not pass `std::string` by value, as it makes an expensive copy.
- Initializing and copying `std::string` is expensive, so avoid this as much as possible.

- Avoid using equality comparison in float numbers.
- Prefer pass by value for objects that are cheap to copy, and pass by const reference for objects that are expensive to copy. If you’re not sure whether an object is cheap or expensive to copy, favor pass by const reference.
- prefer to pass arguments by const reference instead of by non-const reference whenever possible.
- Prefer passing strings using `std::string_view` (by value) instead of `const std::string&`, unless your function calls other functions that require C-style strings or `std::string` parameters.
- Prefer pass by reference to pass by address unless you have a specific reason to use pass by address.
- Return a `std::optional` (instead of a sentinel value) for functions that may fail, unless your function needs to return additional information about why it failed.

- Try to make the member function in class as `const`.