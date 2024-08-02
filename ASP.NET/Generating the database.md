# Install
`dotnet tool install --global dotnet-ef --version 8.0.7`
`dotnet add package Microsoft.EntityFrameworkCore.Design --version 8.0.7`

# Migrations
`dotnet ef migrations add InitialCreate --output-dir Data/Migrations`

# Update
This command will actually create the database based from the migrations
`dotnet ef database update`

# Automatic migrations in start up
This will automatically run the migrations when running the app. So you don't need to type the command migrations and update.

In `./Data/DataExtensions.cs`
```csharp
using Microsoft.EntityFrameworkCore;
using Tutorial.Data;

namespace Tutorial;

public static class DataExtensions {
	public static void MigrateDb(this WebApplication app) {
	using var scope = app.Services.CreateScope();
	var dbContext = scope.ServiceProvider.GetRequiredService<GameStoreContext>();
	dbContext.Database.Migrate();
	}
}
```

in `Program.cs`
```csharp
app.MigrateDb();
```


# Seeding the data
This is when you want to populate your database at the start of creation.
```csharp
// Data/GameStoreContext.cs
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
	modelBuilder.Entity<Genre>().HasData(
		new {Id = 1, Name = "Fighting"},
		new {Id = 2, Name = "Racing"},
		new {Id = 3, Name = "Shooting"},
		new {Id = 4, Name = "Strategy"}
	);
}
```
After writing this code, you should do the migrate command again.