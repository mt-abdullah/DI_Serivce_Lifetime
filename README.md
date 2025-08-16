# ASP.NET Core Dependency Injection Service Lifetimes Demo

![.NET Core](https://img.shields.io/badge/.NET-6.0-blue)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-6.0-blueviolet)

This project demonstrates the three service lifetimes in ASP.NET Core Dependency Injection:
- **Singleton**
- **Scoped**
- **Transient**

## Table of Contents
- [Project Structure](#project-structure)
- [Service Lifetimes Explained](#service-lifetimes-explained)
- [How to Run](#how-to-run)
- [Expected Output](#expected-output)
- [Key Observations](#key-observations)
- [Contributing](#contributing)

## Project Structure

```
DI_Service_Lifetime/
├── Controllers/
│   └── HomeController.cs        # Controller demonstrating service injection
├── Models/
│   ├── ErrorViewModel.cs        # Error view model
│   └── ServiceInfo.cs           # Model for service information display
├── Services/                    # Service implementations
│   ├── ScopedGuidService.cs
│   ├── SingletonGuidService.cs
│   └── TransientGuidService.cs
├── Views/                       # Views to display service information
│   └── Home/
│       ├── Index.cshtml
│       └── Privacy.cshtml
├── Program.cs                   # Service registration
└── README.md                    # This file
```

## Service Lifetimes Explained

| Lifetime  | Registration Method    | Behavior |
|-----------|-----------------------|----------|
| Singleton | `AddSingleton` | Created once per application. Same instance for all requests. |
| Scoped    | `AddScoped`    | Created once per HTTP request. Same instance within a request. |
| Transient | `AddTransient` | New instance created every time it's requested. |

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/mt-abdullah/DI_Service_Lifetime.git
   cd DI_Service_Lifetime
   ```

2. **Run the application**
   ```bash
   dotnet run
   ```

3. **Open in browser**
   ```
   https://localhost:5001
   ```

## Expected Output

When you visit the home page, you'll see GUIDs demonstrating the different lifetimes:

```
Singleton Services:
- Singleton 1: 8a1b3c4d-...
- Singleton 2: 8a1b3c4d-... (Same as Singleton 1)

Scoped Services:
- Scoped 1: 5e6f7g8h-...
- Scoped 2: 5e6f7g8h-... (Same as Scoped 1 within this request)

Transient Services:
- Transient 1: 1a2b3c4d-...
- Transient 2: 9z8y7x6w-... (Different from Transient 1)
```

## Key Observations

1. **Singleton** services maintain the same instance:
   - Same GUID across multiple requests
   - Same GUID for all consumers

2. **Scoped** services:
   - Same instance within a single HTTP request
   - Different instances across different requests

3. **Transient** services:
   - New instance created every time they're requested
   - Different GUIDs even for multiple injections in the same class

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature-branch`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature-branch`)
5. Open a Pull Request
