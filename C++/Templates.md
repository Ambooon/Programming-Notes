```cpp
template <typename T>
T max(T x, T y)
{
    return (x < y) ? y : x;
}

int main()
{
    // instantiates and calls function max<int>(int, int)
    std::cout << max<int>(1, 2) << '\n'; 

	// We can also do this.
	// Deduce the actual type that should be used from the argument types 
	// in the function call.
	std::cout << max<>(1, 2) << '\n';
	std::cout << max(1, 2) << '\n';
    return 0;
}
```

# Function templates with multiple template type parameters

```cpp
#include <iostream>

// We're using two template type parameters named T and U
template <typename T, typename U> 
auto max(T x, U y) // x can resolve to type T, and y can resolve to type U
{
	// uh oh, we have a narrowing conversion problem here
	// That's why we use type auto in return type
    return (x < y) ? y : x; 
}

int main()
{
    std::cout << max(2, 3.5) << '\n'; // resolves to max<int, double>

    return 0;
}
```

This is same as the above code.
```cpp
auto max(auto x, auto y)
{
    return (x < y) ? y : x;
}
```

In C++20, when the auto keyword is used as a parameter type in a normal function, the **compiler will automatically convert the function into a function template** with each auto parameter becoming an independent template type parameter. This method for creating a function template is called an **abbreviated function template**.


```cpp
template <typename T, typename U>
auto add(T x, U y)
{
	return x + y;
}
```