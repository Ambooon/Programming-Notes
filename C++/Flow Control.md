
# if/ else if/ else

```c++
int var = 5;

if (var > 0) {
	std::cout << "Var is positive\n";
} else if (var < 0) {
	std::cout << "Var is negative\n";
} else {
	std::cout << "Var is 0\n";
}
```


# Switch

Expression in switch must be integral or enum type. Cannot be string type.
```c++
int value = 1;

switch (value) {
	case 1: {
		std::cout << "The value is 1\n";
	}
	break;
	case 2: {
		std::cout << "The value is 2\n";
	}
	break;
	default: {
		std::count << "No match found\n";
	}
	break;
}
```

## Nested Switch
```c++
int value = 1;

switch (value) {
	case 1: 
	case 2: {
		std::cout << "The value is 1 or 2\n"; // This code will run if case 1 or 2
	}
	break;
	default: {
		std::count << "No match found\n";
	}
	break;
}
```

## Sequential
```cpp
bool isVowel(char c)
{
    switch (c)
    {
    case 'a': // if c is 'a'
    case 'e': // or if c is 'e'
    case 'i': // or if c is 'i'
    case 'o': // or if c is 'o'
    case 'u': // or if c is 'u'
    case 'A': // or if c is 'A'
    case 'E': // or if c is 'E'
    case 'I': // or if c is 'I'
    case 'O': // or if c is 'O'
    case 'U': // or if c is 'U'
        return true;
    default:
        return false;
    }
}

# Ternary operator
//Ternary initialization
bool isFast = true;
int speed = isFast ? 100 : 50; // If isFast speed is 100 else speed is 50

bool max;
int num1 = 1;
int num2 = 2;

max = (a > b) ? a : b; // max is equals to which is larger number

// Use auto if you want to use different type of data
auto max = isFast ? 100 : 50.5f; // max can be int or float
```


# Goto Statements
```cpp
#include <iostream>
#include <cmath> // for sqrt() function

int main()
{
    double x{};
tryAgain: // this is a statement label
    std::cout << "Enter a non-negative number: ";
    std::cin >> x;

    if (x < 0.0)
        goto tryAgain; // this is the goto statement

    std::cout << "The square root of " << x << " is " << std::sqrt(x) << '\n';
    return 0;
}
```