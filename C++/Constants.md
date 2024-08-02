
Using compile time constants allow the program to be optimized and small in size.

| Term                  | Definition                                                                                                                                                        |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Compile-time constant | An object whose value must be known at compile time (e.g. literals and constexpr variables).                                                                      |
| Constexpr             | Keyword that declares variables as compile-time constants (and functions that can be evaluated at compile-time). Informally, shorthand for “constant expression”. |
| Constant expression   | An expression that contains only compile-time constants and operators/functions that support compile-time evaluation.                                             |
| Runtime expression    | An expression that is not a constant expression.                                                                                                                  |
| Runtime constant      | An constant object that is not a compile-time constant.                                                                                                           |


# constexpr
used to create compile-time (symbolic) constants. Constexpr allow us to write that may be evaluated at compile-time.

## constexpr variable
```c++
constexpr int { 1 + 1 };
```


## constexpr function
```c++
constexpr int greater(int x, int y) // now a constexpr function
{
    return (x > y ? x : y);
}
```