Use `std::cerr` when trying to debug


# Using preprocessor
```c++
#include <iostream>

#define ENABLE_DEBUG // comment out to disable debugging

int getUserInput()
{
#ifdef ENABLE_DEBUG
std::cerr << "getUserInput() called\n";
#endif
	std::cout << "Enter a number: ";
	int x{};
	std::cin >> x;
	return x;
}
```


# Using a logger
You need to install plog
```cpp
#include <plog/Log.h> // Step 1: include the logger headers
#include <plog/Initializers/RollingFileInitializer.h>
#include <iostream>

int getUserInput()
{
	PLOGD << "getUserInput() called"; // PLOGD is defined by the plog library

	std::cout << "Enter a number: ";
	int x{};
	std::cin >> x;
	return x;
}

int main()
{
	plog::init(plog::debug, "Logfile.txt"); // Step 2: initialize the logger

	PLOGD << "main() called"; // Step 3: Output to the log as if you were writing to the console

	int x{ getUserInput() };
	std::cout << "You entered: " << x << '\n';

	return 0;
}
```


# Using IDE debugger 

## Stepping
**For VSCode**
To set up debugging, press _Ctrl+Shift+P_ and select “C/C++: Add Debug Configuration”, followed by “C/C++: g++ build and debug active file”. This should create and open the `launch.json` configuration file. Change the “stopAtEntry” to true:  
`"stopAtEntry": true,`

Then open _main.cpp_ and start debugging by pressing _F5_ or by pressing _Ctrl+Shift+P_ and selecting “Debug: Start Debugging and Stop on Entry”.

std::cout is buffered, in debugging it is recommended to flush the std::cout
```cpp
#ifdef DEBUG
std::cout << std::unitbuf; // enable automatic flushing for std::cout (for debugging)
#endif
```


## Run to cursor
**For VS Code users**
In VS Code, the _run to cursor_ command can be accessed while already debugging a program by right clicking a statement in your code and choosing _Run to Cursor_ from the context menu.

## Breakpoints