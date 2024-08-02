
# Declaring and Initializing
```c++
// DECLARING ARRAY
// If no initial values, the values will be garbage data.
int scores[10]; // This array can store 10 integers

// DECLARING AND INITIALIZING
// The values in the array must be the same type.
double scores[5] {12.0, 4.1, 5.8, 24.5, 23.63};

// if you don't initialize all values, other values will be 0
int scores[5] {12, 4, 6}; // numbers2 = {12, 4, 6, 0, 0}

// OMIT SIZE DECLARATION
int scores[] {1, 2, 3, 4, 5}; // The size will depend on the initialize values.

// CONSTANT ARRAY
const scores[] {1, 2, 3}; // this can't be modified

// ASSIGNING VALUES
// !!! Be careful assigning in out of range 
scores[0] = 1;
scores[1] = 5;

// for each the array
int scores[] {1, 2, 3, 4 ,5};
for (auto value : scores){ // This is like a for each item in array
	std::cout << value << std::endl; 
}
```


# Size of an array
```c++
int numbers[] {1,2,3,4,5};

std::size(numbers); // This equals to 5

// or use range base for loop
for (auto value : numbers){ 
	std::cout << value << std::endl; 
}
```


# Character Arrays
```c++
// declaration
char message[5] {'H', 'e', 'l', 'l', 'o'}; // you can print this using loop

// If you want to print this in one line you must add null terminating character \0
// The \0 is telling that the word ends there.
char message[] {'H', 'e', 'l', 'l', 'o', '\0'};

// Automatic null terminate
// You add one extra index in the array
char message[6] {'H', 'e', 'l', 'l', 'o'};


// STRING LITERAL
// String is wrap in double quotes and it automatically chop the string into individual char and also reads white spaces.
char message[] {"Hello, World!"};
```

# Array bounds
- !!! Read beyond bounds: Will read garbage or crash your program
- !!! Write beyond bounds. The compiler allows it. But you don't own the memory at that index, so other programs may modify it and your program may read bogus data at a later time. Or you can even corrupt data used bu other parts of your program.