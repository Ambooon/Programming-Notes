
# Basic Operations
- Addition 
- Subtraction
- Multiplication
- Division
- Modulus

# Precedence and Associativity
Precedence - which operation first
Associativity - which direction first

# Increment/Decrement

Types of increment/decrement:
- Regular - Can increment/decrement by any number.
- Postfix - this add (++) sign at the end of the variable. The increment happens after this is called. Can only increment/decrement by 1.
- Prefix - this add (++) sign at the start of the variable. The increment happens immediately. Can only increment/decrement by 1.

```c++
// Regulat increment/decrement
int value = 5;
value = value + 1; // value = 6

// Postfix increment/decrement 
int value = 5;
std::cout << value++ << std::endl; // This will print 5
std::cout << value << std::endl; // This will print 6

// Prefix increment/decrement
int value = 5;
std::cout << ++value << std::endl; // This will print 6
```


# Compound Assignment
```c++
// Simple
int value = 5;
value = value + 1; // value = 6

// Using compound assignment
int value = 5
value += 1; // value = 6
```

# Relational Operators
- <
- >
- <=
- >=
- ==
- !=
```c++
int num1 = 1;
int num2 = 2;

// Wrap the comparison inside parenthesis
std::cout << (num1 < num2) << std::endl; // This will print 1
```


# Logical Operators
- && 
- ||
- !

In order for _logical AND_ to return true, both operands must evaluate to true. If the left operand evaluates to false, _logical AND_ knows it must return false regardless of whether the right operand evaluates to true or false. In this case, the _logical AND_ operator will go ahead and return false immediately without even evaluating the right operand! This is known as **short circuit evaluation**, and it is done primarily for optimization purposes.
```c++
bool var1 = true;
bool var2 = true;

// Wrap the comparison inside parenthesis
std::cout << (var1 && var2) << std::endl; // This wil print 1
```


# Output Formatting
To format the data in the terminal
```c++
std::endl;
std::flush;
std::boolalpha;
std::setprecision(20);
std::uppercase;
....
```


# Numeric Limits
Show the limits or the range of a numeric data type
```c++
#include <limits>

std::cout << std::numeric_limits<short>::max() << std::endl; // This will print 32767
```


# Math Functions
Library full of math functions
```c++
#include <cmath>

std::cout << std::ceil(3.3) << std::endl; // This will print 4
```

# Integral Types
- char
- short int
You **can't perform basic arithmetic** with these types. Type 'int' is the smallest data type that support arithmetic.