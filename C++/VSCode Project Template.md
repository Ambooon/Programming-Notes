
# c_cpp_properties.json
```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            "windowsSdkVersion": "10.0.22621.0",
            "compilerPath": "cl.exe",
            "cStandard": "c17",
            "cppStandard": "c++20",
            "intelliSenseMode": "windows-msvc-x64"
        }
    ],
    "version": 4
}
```

# settings.json
```json
{
  "files.associations": {
    "ostream": "cpp"
  }
}
```


# tasks.json
```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "cppbuild",
      "label": "Build with GCC 14.1.0 (Debug)",
      "command": "C:\\mingw64\\bin\\g++.exe",
      "args": [
        "-fdiagnostics-color=always",
        "-g",
        "-std=c++20",
        "-ggdb",
        "-pedantic-errors",
        "-Wall",
        "-Weffc++",
        "-Wextra",
        "-Wconversion",
        "-Wsign-conversion",
        "-Werror",
        "${file}",
        "-o",
        "${fileDirname}\\rooster.exe"
      ],
      "options": {
        "cwd": "${fileDirname}"
      },
      "problemMatcher": ["$gcc"],
      "group": "build",
      "detail": "compiler: C:\\mingw64\\bin\\g++.exe"
    },
    {
      "type": "cppbuild",
      "label": "Build with GCC 14.1.0 (Release)",
      "command": "C:\\mingw64\\bin\\g++.exe",
      "args": [
        "-fdiagnostics-color=always",
        "-g",
        "-std=c++20",
        "-O2",
        "-DNDEBUG",
        "${file}",
        "-o",
        "${fileDirname}\\rooster.exe"
      ],
      "options": {
        "cwd": "${fileDirname}"
      },
      "problemMatcher": ["$gcc"],
      "group": "build",
      "detail": "compiler: C:\\mingw64\\bin\\g++.exe"
    },
    {
      "type": "cppbuild",
      "label": "Build with cl.exe",
      "command": "cl.exe",
      "args": [
        "/Zi",
        "/EHsc",
        "/nologo",
        "/Fe${fileDirname}\\rooster.exe",
        "${file}"
      ],
      "options": {
        "cwd": "${fileDirname}"
      },
      "problemMatcher": ["$msCompile"],
      "group": "build",
      "detail": "compiler: cl.exe"
    }
  ]
}
```


# To check what language standard is my compiler using

```c++
// This program prints the C++ language standard your compiler is currently using

// Freely redistributable, courtesy of learncpp.com (https://www.learncpp.com/cpp-tutorial/what-language-standard-is-my-compiler-using/)

#include <iostream>
const int numStandards = 7;

// The C++26 stdCode is a placeholder since the exact code won't be determined until the standard is finalized
const long stdCode[numStandards] = { 199711L, 201103L, 201402L, 201703L, 202002L, 202302L, 202612L};

const char* stdName[numStandards] = { "Pre-C++11", "C++11", "C++14", "C++17", "C++20", "C++23", "C++26" };
long getCPPStandard()

{
    // Visual Studio is non-conforming in support for __cplusplus (unless you set a specific compiler flag, which you probably haven't)

    // In Visual Studio 2015 or newer we can use _MSVC_LANG instead

    // See https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/

#if defined (_MSVC_LANG)

    return _MSVC_LANG;

#elif defined (_MSC_VER)

    // If we're using an older version of Visual Studio, bail out

    return -1;

#else

    // __cplusplus is the intended way to query the language standard code (as defined by the language standards)

    return __cplusplus;

#endif

}

int main()
{
    long standard = getCPPStandard();

    if (standard == -1)
    {

        std::cout << "Error: Unable to determine your language standard.  Sorry.\n";

        return 0;
    }
  
    for (int i = 0; i < numStandards; ++i)
    {

        // If the reported version is one of the finalized standard codes

        // then we know exactly what version the compiler is running

        if (standard == stdCode[i])
        {
            std::cout << "Your compiler is using " << stdName[i]
                << " (language standard code " << standard << "L)\n";
            break;
        }
        // If the reported version is between two finalized standard codes,

        // this must be a preview / experimental support for the next upcoming version.

        if (standard < stdCode[i])
        {
            std::cout << "Your compiler is using a preview/pre-release of " << stdName[i]
                << " (language standard code " << standard << "L)\n";
            break;
        }
    }
    return 0;
}
```