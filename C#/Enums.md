Enums are use to define a set of named constants.
```csharp
enum DaysOfWeek
{
	Monday,      // The default value of this is 0
	Tuesday,     // and it increment by one.
	Wednesday,   // You can set a value for each of them 
	Thursday,
	Friday,
	Saturday,
	Sunday
}
```

# Switch
```csharp
DaysOfWeek today = DaysOfWeek.Monday;

switch (today)
{
    case DaysOfWeek.Monday:
        Console.WriteLine("Start of the work week.");
        break;
    case DaysOfWeek.Friday:
        Console.WriteLine("Almost the weekend!");
        break;
    // Other cases...
}

```

# Convert int to enums value
```csharp
DaysOfWeek day = DaysOfWeek.Monday;
int dayAsInt = (int)day; // dayAsInt = 1
// We can maybe save this int into the database

// From int to daysofweek
int valueFromDB = 5;
DaysOfWeek intAsDay = (DaysOfWeek)valueFromDB; // intAsDay = Saturday

```

# Flags
Enums with the `[Flags]` attribute allow for bitwise operations, making them useful for representing a combination of options:
```csharp
[Flags]
enum FileAccess
{
    None = 0,
    Read = 1,
    Write = 2,
    Execute = 4,
    ReadWrite = Read | Write
}

// Usage
FileAccess access = FileAccess.Read | FileAccess.Write;

if ((access & FileAccess.Read) == FileAccess.Read)
{
    Console.WriteLine("Read access is set.");
}

```

# Defining states or modes
```csharp
enum OrderStatus
{
    Pending,
    Shipped,
    Delivered,
    Canceled
}

```

# Mapping external data
```csharp
enum ErrorCode
{
    Success = 0,
    NotFound = 1,
    AccessDenied = 2,
    InvalidOperation = 3
}

// Usage
ErrorCode code = ErrorCode.AccessDenied;

if (code == ErrorCode.AccessDenied)
{
    Console.WriteLine("You do not have permission to access this resource.");
}

```