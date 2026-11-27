# Database setup

Only the API connects to PostgreSQL. Store the connection string with .NET user secrets
or the `ConnectionStrings__BudgetDatabase` environment variable.

From the repository root:

```powershell
dotnet tool restore
dotnet user-secrets set "ConnectionStrings:BudgetDatabase" "Host=YOUR_HOST;Port=5432;Database=YOUR_DATABASE;Username=YOUR_USER;Password=YOUR_PASSWORD;SSL Mode=VerifyFull" --project src/Eelarveanaluutik.Api
dotnet ef database update --project src/Eelarveanaluutik.Api -- --environment Development
```

Use the connection details and TLS settings supplied by the database provider.
Migrations are applied explicitly. Running the update command again keeps existing data.
The API status endpoint can run without a database connection.

Amounts are stored as `numeric(18,2)` in EUR. Transaction dates use `yyyy-MM-dd`.
Budgets and reports store the first day of the month. Timestamps are UTC.
