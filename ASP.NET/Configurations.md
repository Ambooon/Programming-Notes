Add your configurations in the `appsettings.json`. NOTE!!! if you need to store some credentials and secrets you must use the `User Secrets` in the configuration.

# Example
To avoid hard coded connection path, add this into the `ConnectionStrings`.
```json
"ConnectionStrings": {
	"GameStore": "Data Source=GameStore.db"
}
```

How to use
```csharp
var connString = builder.Configuration.GetConnectionString("GameStore");
```
