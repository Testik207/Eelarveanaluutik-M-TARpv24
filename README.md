# Eelarveanalüütik

A personal budget application for tracking income and expenses,
setting monthly budgets and analysing spending.

## Technologies

- C# / ASP.NET Core
- React / JavaScript
- PostgreSQL / Entity Framework Core

## Run

Requires .NET 10 SDK and Node.js 24. Run these commands from the repository root.

API:

```powershell
dotnet restore Eelarveanaluutik.sln
dotnet run --project src/Eelarveanaluutik.Api --launch-profile http
```

React, in a second terminal:

```powershell
cd web
npm.cmd ci
npm.cmd run dev
```

Open http://127.0.0.1:5173. The API status endpoint is http://localhost:5151/api/health.

Worker, in a separate terminal:

```powershell
dotnet run --project src/Eelarveanaluutik.Worker
```

## Database

See [database setup](docs/DATABASE.md) for connection and migration commands.

## Tests

```powershell
dotnet test Eelarveanaluutik.sln
```

Database integration tests run when `TEST_POSTGRES_CONNECTION` is set.
Use a separate test database with permission to create schemas.

```powershell
$env:TEST_POSTGRES_CONNECTION = "YOUR_POSTGRESQL_CONNECTION_STRING"
dotnet test Eelarveanaluutik.sln
Remove-Item Env:TEST_POSTGRES_CONNECTION
```
