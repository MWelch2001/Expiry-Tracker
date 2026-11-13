# Expiry Tracker

A stock expiry tracker built with .NET, PostgreSQL and React. It helps small teams keep on top of use-by dates, so long-dated items don't get forgotten and waste is reduced.

> **Status:** work in progress.

## The problem

Tracking stock by use-by date is slow and error-prone, and items with long dates are easy to forget. This app records batches with their expiry dates, calculates new dates when items are opened, and shows what needs using first.

## Planned features

- Record batches with quantity and expiry date
- Opened-item rules (e.g. use within 3 days of opening)
- "Use first" view, sorted by soonest expiry
- Daily alerts for items expiring soon
- Waste log and reporting
- Phone-friendly web app

## Tech stack

- **Backend:** ASP.NET Core Web API, EF Core
- **Database:** PostgreSQL
- **Frontend:** React and TypeScript (planned)
- **Testing:** xUnit
- **Planned:** background worker and messaging, Docker, GitHub Actions CI/CD, Azure deployment

## Running locally

### Prerequisites

- .NET SDK (current LTS)
- PostgreSQL

### Setup

1. Create a PostgreSQL database named `expirytracker` and a user named `expiry`.
2. Store the connection string in user secrets:
   ```bash
   cd src/ExpiryTracker.Api
   dotnet user-secrets init
   dotnet user-secrets set "ConnectionStrings:Default" "Host=localhost;Port=5432;Database=expirytracker;Username=expiry;Password=YOUR_PASSWORD"
   ```
3. Run the API from the repo root:
   ```bash
   dotnet run --project src/ExpiryTracker.Api
   ```

### Tests

```bash
dotnet test
```

## Project structure

- `src/ExpiryTracker.Api`: web API
- `src/ExpiryTracker.Domain`: entities and business rules
- `src/ExpiryTracker.Infrastructure`: database access
- `tests/ExpiryTracker.Tests`: unit tests
