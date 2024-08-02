This is like a contract in which both the client and the server agreed on. This contract dictates on what must the data looks like.

# Create DTO
To create a DTO, first create directory to store the DTOs. Next, create a new RECORD then name it what you want.

```csharp
// Remember to edit the namespace
namespace Tutorial.Dtos;

public record class CreateGameDto(
string Name,
string Genre,
decimal Price,
DateOnly ReleaseDate);
```

Then you can import this into your main file.
