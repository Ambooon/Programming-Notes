
# For loops

size_t - is not a type, but a type alias for some **unsigned int** representation. Can be use to represent size of things like count, speed, etc. The size of this is 8 bytes.

```c++
for(unsigned int i{}; i < 10; ++i) { // This will print Hello 10 times
	std::cout << "Hello" << std::endl; 
}

for(size_t i{}; i < 10; ++i) { // using size_t
	std::cout << "Hello" << std::endl; 
}

size_t i{}; // declared outside
for( ; i < 10; ++i) { // You can skip iterator declaration like this
	std::cout << "Hello" << std::endl; 
}
```


# While loops
```c++
const size_t LIMIT{10};
size_t i{0};

while (i < LIMIT){
	std::cout << "Hello" << std::endl;
	++i; // Don't forget the incrementation to avoid infinite loop
}
```


# Do while loops
This loop runs the body first before checking the condition. 

```c++
const size_t LIMIT{10};
size_t i{0};

do{
	std::cout << "Hello" << std::endl;
	++i; // Increment here
}while (i < LIMIT);
```


# Range based for loop
```c++
int scores[] {1, 2, 3, 4 ,5};

for (auto value : scores){ // This is like a for each item in array
	std::cout << value << std::endl; 
}
```