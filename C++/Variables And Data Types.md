# Number Systems
```c++
int number1 = 15; // Decimal
int number2 = 017; // Octal
int number3 = 0x0F; // Hexadecimal
int number4 = 0b00001111; // Binary
```

# Variable Initialization
In is recommended to use list initialization `{}`.
```c++
int var; // Without initial value
int variable0 {}; // Empty, this equals to 0
int variable1 {10}; // Brace
int variable2 (12); // Parenthesis
int variable3 = 13; // Equal
const int variable4 = 1; // use const if you don't want the value to change

// Not using the variable the compiler will throw a warning
// To avoid this we can add [[maybe_unused]]
[[maybe_unused]] int num{2};
```

# Integers
Integers by default holds 4 bytes of memory.
You can use `sizeof(int)` to check the size of memory.

## Integers Modifier
- **Signed** - number is signed, it can be negative. The max range of number is divided in half.
- **Unsigned** - number is unsigned, it can't store negative numbers.
- **Short** - size in the memory is 2 bytes
- **Long** - size in the memory can be 4 or 8 bytes
- **Long** **Long** - size in the memory is 8 bytes
```c++

signed num1 = 1; // signed is automatically int
signed int num2 = -2;
unsigned int num3 = 3

int num4 = 5;

short num5 = 2;
long num6 = 123456;
long long num7 = 123456789;
```

Best practice

- Prefer `int` when the size of the integer doesn’t matter (e.g. the number will always fit within the range of a 2-byte signed integer) and the variable is short-lived (e.g. destroyed at the end of the function). For example, if you’re asking the user to enter their age, or counting from 1 to 10, it doesn’t matter whether int is 16 or 32 bits (the numbers will fit either way). This will cover the vast majority of the cases you’re likely to run across.
- Prefer `std::int#_t` when storing a quantity that needs a guaranteed range.
- Prefer `std::uint#_t` when doing bit manipulation or where well-defined wrap-around behavior is required.

Avoid the following when possible:

- `short` and `long` integers -- use a fixed-width type instead.
- Unsigned types for holding quantities.
- The 8-bit fixed-width integer types.
- The fast and least fixed-width types.
- Any compiler-specific fixed-width integers -- for example, Visual Studio defines __int8, __int16, etc…

# Floating Numbers

Types of floating numbers:
- **Float** - size in the memory is 4 bytes. Precision is 7
- **Double** - size in the memory is 8 bytes. Precision is 15. This is the default
- **Long Double** -  size in the memory is 16 bytes. Precision is more than 15
The more bytes you have the more precision the floating number will be. The precision means the number of digits a number can store accurately.

In initializing a value of floating number. Suffix determine the type of the float number
- **Float** - this uses 'f' as a suffix `float num1 = 1.234f` 
- **Double** - this is the default so it uses nothing `double num1 = 1.234` 
- **Long double** - this uses 'L' as a suffix `long double num1 = 1.234l` 
```c++
float num1 = 1.234f;
double num2 = 1.234;
long double num3 = 1.2342423l;

// You can use scientific notation
double num4 = 3.14e+5 // num4 = 314000
double num5 {3.14e-5} // num5 = 0.0000314
```


# Boolean

Boolean value take up to 1 byte. If you try to print boolean values they will equal to numbers, true=1, false=0.

```c++
bool red_light {true};
bool green_light {false};

if (red_light == true) {
	std::cout << "The light is red" << std::endl;
} else {
	std::cout << "The light is NOT red" << std:endl;
}

// Use this to print True/False instead of 1/0
std::cout << std::boolalpha;
```


# Character

Char value take up to 1 byte. It can store one character only. If you put an integer into char, the value will be in ASCII, unless you specify to use the integer value itself.
```c++
// char are wrap in single quotes
char letter1 {'a'};
char letterA = 65;

std::cout << letter1 << std::endl; // a
std::cout << letterA << std::endl; // capital A is number 65 in ASCII
std::cout << static_cast<int>(letterA) << std::endl; // 65
```


# Auto

The auto keyword tries to guess the type base on the given value.
```c++
auto var1 {1}; // int
auto var2 {1.0}; //double
auto var3 {1.0f}; // float
auto var4 {1.0l}; // long double 
auto var5 {'a'}; // character

auto var6 {1.0u}; // unsigned
auto var7 {1.0ul}; // unsigned long
auto var7 {1.0ll}; // long long
```

