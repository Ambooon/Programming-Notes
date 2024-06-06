- Use "\n" instead of std::endl;
- std::cerr when debugging
- Initialize variable with value if you can
- Avoid using unsigned types

- Use compile-time constant
- Avoid the use of the `inline` keyword unless you have a specific, compelling reason to do so (e.g. you’re defining those functions or variables in a header file).

- Do not pass `std::string` by value, as it makes an expensive copy.
- Initializing and copying `std::string` is expensive, so avoid this as much as possible.

- Avoid using equality comparison in float numbers.