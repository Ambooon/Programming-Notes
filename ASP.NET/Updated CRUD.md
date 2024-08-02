In `GameEndpoints.cs`
```csharp
using Microsoft.EntityFrameworkCore;
using Tutorial.Data;
using Tutorial.Dtos;
using Tutorial.Entities;
using Tutorial.Mapping;

namespace Tutorial.Endpoints;

public static class GameEndpoints
{
	const string GetGame = "GetGame";
	
	public static RouteGroupBuilder MapGameEndpoints(this WebApplication app) {
	
	// This is to avoid repeating the word 'games' for every endpoint
	var group = app.MapGroup("games").WithParameterValidation();
	
	group.MapGet("/", (GameStoreContext dbContext) =>
		dbContext.Games.Include(game => game.Genre)
		.Select(game => game
		.ToSummaryDto())
		.AsNoTracking());
	
	group.MapGet("/{id}", (int id, GameStoreContext dbContext) => {
			Game? game = dbContext.Games.Find(id);
			return game is null ? Results.NotFound() : Results.Ok(game.ToDetailsDto());

		}).WithName(GetGame);
		
	group.MapPost("/", (CreateGameDto newGame, GameStoreContext dbContext) => {
		Game game = newGame.ToEntity();
		dbContext.Games.Add(game);
		dbContext.SaveChanges();
		return Results.CreatedAtRoute(GetGame, new { id = game.Id }, game.ToDetailsDto());
	});
	
	group.MapPut("/{id}", (int id, UpdateGameDto updatedGame, GameStoreContext dbContext) => {
	var existingGame = dbContext.Games.Find(id);
	if (existingGame is null) {
		return Results.NotFound();
	}
	
	dbContext.Entry(existingGame)
	.CurrentValues
	.SetValues(updatedGame.ToEntity(id));

	dbContext.SaveChanges();
	
	return Results.NoContent();
	});
	
	group.MapDelete("/{id}", (int id, GameStoreContext dbContext) =>
	{
	dbContext.Games.Where(game => game.Id == id).ExecuteDelete();
	return Results.NoContent();
	});
	
	return group;
	}
}
```

In `GameMapping.cs`
```csharp
using Tutorial.Dtos;
using Tutorial.Entities;

namespace Tutorial.Mapping;

public static class GameMapping {

public static Game ToEntity(this CreateGameDto game) {
	return new Game() {
		Name = game.Name,
		GenreId = game.GenreId,
		Price = game.Price,
		ReleaseDate = game.ReleaseDate
	};
}

public static Game ToEntity(this UpdateGameDto game, int id) {
	return new Game() {
		Id = id,
		Name = game.Name,
		GenreId = game.GenreId,
		Price = game.Price,
		ReleaseDate = game.ReleaseDate
	};
}

public static GameSummaryDto ToSummaryDto(this Game game) {
	return new(
		game.Id,
		game.Name,
		game.Genre!.Name,
		game.Price,
		game.ReleaseDate
	);
}

public static GameDetailsDto ToDetailsDto(this Game game) {
	return new(
		game.Id,
		game.Name,
		game.GenreId,
		game.Price,
		game.ReleaseDate
	);
}
}
```

Note!!! The DTOs are changed here. The GenreId and the Genre are different in some DTOs. Some are the string name value and some are the actual id. 