As you write your programs, consider how users will misuse your program, especially around text input. For each point of text input, consider:

- Could extraction fail?
- Could the user enter more input than expected?
- Could the user enter meaningless input?
- Could the user overflow an input?

You can use if statements and boolean logic to test whether input is expected and meaningful.

The following code will clear any extraneous input:

```cpp
#include <limits> // for std::numeric_limits

void ignoreLine()
{
    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
}
```


The following code will test for and fix failed extractions or overflow (and remove extraneous input):

```cpp
// returns true if extraction failed, false otherwise
bool clearFailedExtraction()
{
    // Check for failed extraction
    if (!std::cin) // If the previous extraction failed
    {
        if (std::cin.eof()) // If the stream was closed
        {
            exit(0); // Shut down the program now
        }

        // Let's handle the failure
        std::cin.clear(); // Put us back in 'normal' operation mode
        ignoreLine();     // And remove the bad input

        return true;
    }

    return false;
}
```


We can test to see if there is an unextracted input (other than a newline) as follows:

```cpp
// returns true if std::cin has unextracted input on the current line, false otherwise
bool hasUnextractedInput()
{
    return !std::cin.eof() && std::cin.peek() != '\n';
}
```

Finally, use loops to ask the user to re-enter input if the original input was invalid.