Async returns a Task.

Example
```csharp
group.MapGet("/{id}", async (int id, GameStoreContext dbContext) => {
	Game? game = await dbContext.Games.FindAsync(id);
	return game is null ? Results.NotFound() : Results.Ok(game.ToDetailsDto());
}).WithName(GetGame);
```

**How to use asynchronous**
1. You use the keyword `async` in the method. 
2. Then `await` keyword in the process you want to await. 
3. Lastly change the method into an async, example `Find()` into `FindAsync()`.


# Things you want to use async
1. In the dbContext methods
2. In the migrations