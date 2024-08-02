
# Requirements
- Code editor 
- Compiler

Install both the code editor of your choice and the compiler. Compiler are different based on the operating system. It's good to have all the compiler installed to test your code if it works in different compilers.

# How to run C++ code
1. First is to compile your code into an .exe (for Windows) using a compiler.
2. After .exe is created, now you can run your code.

## Build configuration
1. Build for debugging. Files are more large and slow. This is because it contains debugging information which help the programmer to easily debug the code.
2. Build for release. Files are small and fast. It is optimized. Great for releasing the program to the users.

**For VS Code users**
When you first ran your program, a new file called _tasks.json_ was created under the _.vscode_ folder in the explorer pane. Open the _tasks.json_ file, find _“args”_, and then locate the line _“${file}”_ within that section.

Above the _“${file}”_ line, add a new line containing the following command (one per line) when debugging:  
`"-ggdb",`

Above the _“${file}”_ line, add new lines containing the following commands (one per line) for release builds:  
`"-O2",`  
`"-DNDEBUG",`

## Compiler Extensions
**Best practice**
Disable compiler extensions to ensure your programs (and coding practices) remain compliant with C++ standards and will work on any system.

**For VS Code users**
- Open the tasks.json file, find `"args"`, and then locate the line `"${file}"` within that section.
- Above the `"${file}"` line, add a new line containing the following commands:
`"-pedantic-errors",`

As of the time of writing, VS Code does not automatically add a newline to the end of code files that are missing it (something that is pedantically required by the C++ standard). Fortunately, we can tell VS Code to do so:
- Open VS Code and go to _File (Code if using a Mac) > Preferences > Settings_. This will open a settings dialog.
- Enter `insert final newline` into the search bar.
- In both the _Workspace Settings_ and _User Settings_ tabs, ensure the checkbox labeled _Files: Insert Final Newline_ is checked.

## Increasing warning levels
This is to help in learning process. To easily identify warnings and bad code.

**For VS Code users**
Open the tasks.json file, find “args”, and then locate the line _“${file}”_ within that section.
Above the _“${file}”_ line, add new lines containing the following commands (one per line):
"-Wall",
"-Weffc++",
"-Wextra",
"-Wconversion",
"-Wsign-conversion",

## Treat warnings as error
The compiler will stop if it finds a warning in the code.

**For VS Code users**
In the `tasks.json` file, add the following flags before “${file}”, one per line:

"-Werror",

## Compile multiple cpp files
You have two options here:
- If you wish to be explicit about what files get compiled, replace `"${file}",` with the name of each file you wish to compile, one per line, like this:
`"main.cpp",`  
`"add.cpp",`

- Reader “geo” reports that you can have VS Code automatically compile all .cpp files in the directory by replacing `"${file}",` with `"${fileDirname}\\**.cpp"` (on Windows).
- Reader “Orb” reports that `"${fileDirname}/**.cpp"` works on Unix.
# Input and Output
```c++
std::cout << "Hello World!";
std::cerr << "Error Message";
std::clog << "Log Message";

int age;
std::cin >> age;

int a;
int b;
std::cin >> a >> b; // input are space seperated
// for getting data with spaces
std::string name;
std::getLine(std::cin, name);
```

# Comments 
Tips
- At the library, program, or function level, use comments to describe _what_.
- Inside the library, program, or function, use comments to describe _how_.
- At the statement level, use comments to describe _why_.
