In `Enpoints/GameEndpoints.cs`. Inject the `dbContext`, then create a game entity. Lastly, you should return a `DTO` and not an internal object.
```csharp
group.MapPost("/", (CreateGameDto newGame, GameStoreContext dbContext) =>
{
	Game game = new() {
		Name = newGame.Name,
		Genre = dbContext.Genres.Find(newGame.GenreId),
		GenreId = newGame.GenreId,
		Price = newGame.Price,
		ReleaseDate = newGame.ReleaseDate
	};
	
	dbContext.Games.Add(game);
	dbContext.SaveChanges();
	
	GameDto gameDto = new(
		game.Id,
		game.Name,
		game.Genre!.Name,
		game.Price,
		game.ReleaseDate
	);
	
	return Results.CreatedAtRoute(GetGame, new { id = game.Id }, gameDto);
});
```

NOTE!!! The GenreId in the CreateGameDto is changed.
```csharp
public record class CreateGameDto(
	[Required][StringLength(50)] string Name,
	int GenreId,
	[Required][Range(1, 100)] decimal Price,
	DateOnly ReleaseDate
);
```