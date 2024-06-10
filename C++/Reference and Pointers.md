
# Reference
```cpp
#include <iostream>

int main()
{
    int x { 5 }; // normal integer variable
    int& ref { x }; // ref is now an alias for variable x

    std::cout << x << ref << '\n'; // print 55

    x = 6; // x now has value 6

    std::cout << x << ref << '\n'; // prints 66

    ref = 7; // the object being referenced (x) now has value 7

    std::cout << x << ref << '\n'; // prints 77

    return 0;
}
```

## lvalue reference to const
```cpp
#include <iostream>

int main()
{
    int x { 5 };          // x is a modifiable lvalue
    const int& ref { x }; // okay: we can bind a const reference to a modifiable lvalue

    std::cout << ref << '\n'; // okay: we can access the object through our const reference
    ref = 7;                  // error: we can not modify an object through a const reference

    x = 6;                // okay: x is a modifiable lvalue, we can still modify it through the original identifier

    return 0;
}
```

## Function pass by reference
```cpp
#include <iostream>

void addOne(int& y) // y is bound to the actual object x
{
    ++y; // this modifies the actual object x
}

int main()
{
    int x { 5 };

    std::cout << "value = " << x << '\n';

    addOne(x);

    std::cout << "value = " << x << '\n'; // x has been modified

    return 0;
}
```

Note: Prefer using std::string_view instead of std::string&

# Pointers
Pointer is a special type of variable that stores the memory address of some variable.
All pointer have the same size.

```c++
// Initialize
// position of * can be anywhere between int and var_name
// Empty value means it initialize with nullptr
int* pointerVar {}; // Can only store address of the variable with the same type 

//Explicit with nullptr
int* pointerVar {nullptr};

// DECLARATION
int number = 2;
pointerVar{&number};
// using & operator give the memory address of that variable


// DEREFERENCING POINTER
// It means reading the value in that memory address
int* pointerVar = nullptr;
int number = 2;
pointerVar{&number};

std::cout << *pointerVar << std::endl; // This will print 2
```


# Character Pointers

```c++
// Pointer will point to the first character in the string literal
// Also this is const and cannot be modified
const char *message {"Hello World!"};
std::cout << *message; // This will print H
```


# ! Rules in pointer
```c++
// Don't try to write in uninitialized pointer through dereference
// This contains garbage data or it points to another memory that's not yours
// Must use nullptr when do this
int *pointer; // This may contain junk or memory from another program
*pointer = 55;

// Don't try to write with null pointer through dereferencing
// nullptr points to nothing
int *pointer {nullptr};
*pointer = 55; // This try to write 55 into nothing
```

## Pointer and Const
```cpp
int main()
{
    int v{ 5 };
    
	// points to an "int" but is not const itself, so this is a normal pointer.
    int* ptr0 { &v };  
         
    // points to a "const int" but is not const itself, so this is a pointer to a const value.      
    const int* ptr1 { &v };  
    
    // points to an "int" and is const itself, so this is a const pointer (to a non-const value).     
    int* const ptr2 { &v };     

	// points to a "const int" and is const itself, so this is a const pointer to a const value.
    const int* const ptr3 { &v }; 

    // if the const is on the left side of the *, the const belongs to the value
    // if the const is on the right side of the *, the const belongs to the pointer

    return 0;
}
```

# Dynamic Memory Allocation
## Stack and Heap
![[Pasted image 20240528151959.png]]

![[Pasted image 20240528152555.png]]

## Stack
In stack memory this is where all the variables live. 
```c++
// Stack lifetime
int main (){
	{
			int var = 2;// This live in this scope
	}
	// int var is killed here after the closing braces
}
```

## Heap
In heap memory, the programmer has the control to create or to release the variable memory. After releasing the heap memory it will be given back to the OS.
```c++
int *pointer {nullptr};
// This allocate 4 bytes of memory on the heap. This memory is ours now to use. The OS can't use this memory for something else, until we return it. This is now a valid memory. The size of the memory depends on the type pointed by the pointer.
pointer = new int;
pointer = new int {2}; // with value

*pointer = 5; // Writing in the dynamically allocated memory
```

```c++
// To initialize use the word new
int *pointer {nullptr};
pointer = new int; // This go in the heap memory

// ---------------------------------------------------------------------------
// Heap lifetime
int main (){
	{
			int var = 2;// This live in this scope
			int *var2 = new int; 
	}
	// int var is killed here after the closing braces
	// int var2 is not killed and it still can be use

	// DELETE HEAP use delete keyword
	// after deleting the memory will be given back to the OS
	// !!! BAD: Don't delete the pointer twice
	delete var2; 
	var2 = nullptr; // ALWAYS assign nullptr to the deleted var2

	// reuse pointer
	// after var2 becomes nullptr, we can now add new heap memory to it
	var2 = new int {2};
}


```


# Difference
There are some other differences between pointers and references worth mentioning:

- References must be initialized, pointers are not required to be initialized (but should be).
- References are not objects, pointers are.
- References can not be reseated (changed to reference something else), pointers can change what they are pointing at.
- References must always be bound to an object, pointers can point to nothing (we’ll see an example of this in the next lesson).
- References are “safe” (outside of dangling references), pointers are inherently dangerous (we’ll also discuss this in the next lesson).

# std::optional
It is use for the function that either return a value or null.
```cpp
#include <iostream>
#include <optional> // for std::optional (C++17)

// Our function now optionally returns an int value
std::optional<int> doIntDivision(int x, int y)
{
    if (y == 0)
        return {}; // or return std::nullopt
    return x / y;
}

int main()
{
    std::optional<int> result1 { doIntDivision(20, 5) };
    if (result1) // if the function returned a value
        std::cout << "Result 1: " << *result1 << '\n'; // get the value
    else
        std::cout << "Result 1: failed\n";

    std::optional<int> result2 { doIntDivision(5, 0) };

    if (result2)
        std::cout << "Result 2: " << *result2 << '\n';
    else
        std::cout << "Result 2: failed\n";

    return 0;
}
```

## For optional parameter
```cpp
#include <iostream>
#include <optional>

void printIDNumber(std::optional<const int> id = std::nullopt)
{
    if (id)
        std::cout << "Your ID number is " << *id << ".\n";
    else
        std::cout << "Your ID number is not known.\n";
}

int main()
{
    printIDNumber(); // we don't know the user's ID yet

    int userid { 34 };
    printIDNumber(userid); // we know the user's ID now

    printIDNumber(62); // we can also pass an rvalue

    return 0;
}
```

Best practice

Prefer `std::optional` for optional return types.

Prefer function overloading for optional function parameters (when possible). Otherwise, use `std::optional<T>` for optional arguments when `T` would normally be passed by value. Favor `const T*` when `T` is expensive to copy.
