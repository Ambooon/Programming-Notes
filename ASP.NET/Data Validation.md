# Install the extension
`dotnet add package MinimalApis.Extensions --version 0.11.0`

# Add the constraint in the DTOs
```csharp
using System.ComponentModel.DataAnnotations;
namespace Tutorial.Dtos;

public record class UpdateGameDto(
	[Required][StringLength(50)] string Name,
	[Required][StringLength(20)] string Genre,
	[Required][Range(1, 100)] decimal Price,
	DateOnly ReleaseDate
);
```


# Use the validation in your routes
```csharp
var group = app.MapGroup("games").WithParameterValidation();
```