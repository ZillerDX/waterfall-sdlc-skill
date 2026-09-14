---
name: csharp-tooling
description: High-efficiency C# .NET 9 engineering standards for agentic coding. Enforces token-saving Minimal APIs, zero-overhead MSBuild error filtering, clean Windows port hygiene, and compact Entity Framework Core SQLite/in-memory patterns.
---

# C# .NET 9 Tooling & Lean Architecture

Standard Operating Procedure for developing C# .NET applications with autonomous AI agents. Designed for extreme token efficiency, zero build spam, clean process management, and rapid vertical slice delivery.

---

## 1. Zero-Spam MSBuild Diagnostics (Save 95% Tokens)

Raw `dotnet build` dumps hundreds of lines of MSBuild banners, target evaluations, and project outputs into context.

- **Mandatory Filtered Build**:
  ```powershell
  dotnet build --nologo -clp:ErrorsOnly
  ```
  *When clean, this outputs 0 lines (Exit Code 0). When broken, it prints ONLY the exact file, line number, column, and error code.*

- **Quiet Test Execution**:
  ```powershell
  dotnet test --nologo -v q
  ```

- **Restore & Add Package Quietly**:
  ```powershell
  dotnet add package <PackageName> -v q
  ```

---

## 2. Lean Architecture: Minimal APIs over Enterprise Sprawl

When building Rapid MVPs, Hackathon spikes, or Level 2.5 vertical slices, **NEVER** scaffold 15 separate files with traditional Controllers, Interfaces, Repositories, DTOs, and Services.

### The 1-to-2 File Vertical Slice Pattern

Place endpoints, entities, and database context directly in `Program.cs` (or a single `Models.cs` + `Program.cs`):

```csharp
using Microsoft.EntityFrameworkCore;

var builder = WebApplication.CreateBuilder(args);

// 1. Configure Services & SQLite / In-Memory DB
builder.Services.AddDbContext<AppDb>(opt => opt.UseSqlite("Data Source=app.db"));
builder.Services.AddCors(opt => opt.AddDefaultPolicy(p => p.AllowAnyOrigin().AllowAnyMethod().AllowAnyHeader()));

var app = builder.Build();
app.UseCors();

// Ensure DB schema is ready instantly without waiting for migration files
using (var scope = app.Services.CreateScope())
{
    var db = scope.ServiceProvider.GetRequiredService<AppDb>();
    db.Database.EnsureCreated();
}

// 2. Minimal Endpoints
app.MapGet("/api/items", async (AppDb db) => await db.Items.ToListAsync());

app.MapPost("/api/items", async (ItemDto dto, AppDb db) =>
{
    var item = new Item { Title = dto.Title, CreatedAt = DateTime.UtcNow };
    db.Items.Add(item);
    await db.SaveChangesAsync();
    return Results.Created($"/api/items/{item.Id}", item);
});

app.Run();

// 3. Compact Models & DbContext in same or adjacent slice
public class AppDb : DbContext
{
    public AppDb(DbContextOptions<AppDb> options) : base(options) { }
    public DbSet<Item> Items => Set<Item>();
}

public class Item
{
    public int Id { get; set; }
    public required string Title { get; set; }
    public DateTime CreatedAt { get; set; }
}

public record ItemDto(string Title);
```

### When to Upgrade:
Only transition from Minimal APIs to separate Controller/Service class libraries at **Level 3 (System-Track)** when entity count exceeds 10 or enterprise multi-tenant layering is explicitly required.

---

## 3. Windows Port Hygiene & Process Lifecycle

Never launch `dotnet run` without sanitizing the target port first. Stale ASP.NET Core processes lock TCP sockets and cause `IOException: address already in use`.

### The 1-Liner Clean Port Handshake:
```powershell
Get-NetTCPConnection -LocalPort 5000,5080,5120 -ErrorAction SilentlyContinue | ForEach-Object { Stop-Process -Id $_.OwningProcess -Force }
```

### Launching the Backend Process:
Always specify `--urls` explicitly to prevent random port assignments:
```powershell
dotnet run --project <PathToCsproj> --urls "http://localhost:5080"
```

---

## 4. Entity Framework Core Quick-Start
- Use `db.Database.EnsureCreated()` for rapid prototypes.
- For SQLite, use `Microsoft.EntityFrameworkCore.Sqlite`.
- When serializing entities with navigation properties, prevent cyclic references using `System.Text.Json.Serialization.ReferenceHandler.IgnoreCycles`.

---

## 5. Summary Checklist for AI Agents
1. Did you run `dotnet build --nologo -clp:ErrorsOnly` instead of raw `dotnet build`?
2. Did you use a clean Minimal API in `Program.cs` instead of creating 15 separate files?
3. Did you kill existing port listeners before launching `dotnet run`?
4. Is stdout kept to 0 lines when tests and builds succeed?
