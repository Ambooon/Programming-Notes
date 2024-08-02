The purpose of this is to map the C# objects into your database tables. This helps you to translate your C# code into SQL commands and translate the query results into objects that C# can understand.


# Install
This is for sqlite
`dotnet add package Microsoft.EntityFrameworkCore.Sqlite`

# Create
To start create a directory that will hold the files. Ideally you should name it `Data`. After creating the directory, next is to create a class then name it into `{databasename}Context` example `GameStoreContext`. 

```csharp
using Microsoft.EntityFrameworkCore;
namespace Tutorial.Entities;

public class GameStoreContext(DbContextOptions<GameStoreContext> options) : DbContext(options)
{
	public DbSet<Game> Games => Set<Game>();
	public DbSet<Genre> Genres => Set<Genre>();
}
```