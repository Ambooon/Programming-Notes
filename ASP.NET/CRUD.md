```csharp
public static class GameEndpoints {
const string GetGame = "GetGame";

private static readonly List<GameDto> games = [
	new (
		1,
		"Rocket League",
		"Sports",
		10.99M,
		new DateOnly(2010, 5, 24)
	),
	new (
		2,
		"DOTA 2",
		"MOBA",
		2.99M,
		new DateOnly(2002, 2, 14)
	),
	new (
		3,
		"Valorant",
		"Shooting",
		1.19M,
		new DateOnly(2018, 2, 20)
	)
];

public static RouteGroupBuilder MapGameEndpoints(this WebApplication app)
{
	// This is to avoid repeating the word 'games' for every endpoint
	var group = app.MapGroup("games");
	
	group.MapGet("/", () => games);
	  
	group.MapGet("/{id}", (int id) =>
	{
		GameDto? game = games.Find(game => game.Id == id);
		return game is null ? Results.NotFound() : Results.Ok(game);
		}).WithName(GetGame);
		
	group.MapPost("/", (CreateGameDto newGame) =>
	{
		GameDto game = new(
			games.Count + 1,
			newGame.Name,
			newGame.Genre,
			newGame.Price,
			newGame.ReleaseDate);
			games.Add(game);
		return Results.CreatedAtRoute(GetGame, new { id = game.Id }, game);
	});
	
	group.MapPut("/{id}", (int id, UpdateGameDto updateGame) =>
	{
		int index = games.FindIndex(game => game.Id == id);
		if (index == -1)
		{
		return Results.NotFound();
		}
		games[index] = new GameDto(
			id,
			updateGame.Name,
			updateGame.Genre,
			updateGame.Price,
			updateGame.ReleaseDate
			);
		return Results.NoContent();
	});
	
	group.MapDelete("/{id}", (int id) =>
	{
		games.RemoveAll(game => game.Id == id);
		return Results.NoContent();
	});
	
	return group;
	}
}
```


In Program.cs file
```csharp
app.MapGameEndpoints();
```