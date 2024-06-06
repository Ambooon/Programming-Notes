Pointer is a special type of variable that stores the memory address of some variable.
All pointer have the same size.

```c++
// Initialize
// position of * can be anywhere between int and var_name
// Empty value means it initialize with nullptr
int *pointerVar {}; // Can only store address of the variable with the same type 

//Explicit with nullptr
int *pointerVar {nullptr};

// DECLARATION
int number = 2;
pointerVar{&number};
// using & operator give the memory address of that variable


// DEREFERENCING POINTER
// It means reading the value in that memory address
int *pointerVar = nullptr;
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

