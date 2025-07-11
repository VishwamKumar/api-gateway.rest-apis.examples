
# ApiGatewayApps

## Description

This repository demonstrates how to build API Gateways using two different .NET technologies:

- **`ApiGateway.Ocelot.RestApi`** – Implements a gateway using [Ocelot](https://github.com/ThreeMammals/Ocelot), a lightweight API gateway library for .NET.
- **`ApiGateway.Yarp.RestApi`** – Implements a gateway using [YARP (Yet Another Reverse Proxy)](https://github.com/microsoft/reverse-proxy), a modern, high-performance reverse proxy from Microsoft.

Both projects show how to route multiple REST APIs through a single gateway endpoint and support multiple downstream services.

---

# Author

## Vishwa Kumar

- **Email:** vishwa@vishwa.me
- **GitHub:** [Vishwam](https://github.com/vishwamkumar)
- **LinkedIn:** [Vishwa Kumar](https://www.linkedin.com/in/vishwamohan)

Vishwa is the primary developer and architect of this example app, responsible for the architecture and implementation of these features.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### ✅ Features

- Centralized routing for multiple REST APIs
- Aggregated Swagger UI (in YARP)
- Easily extendable to support more downstream services
- Minimal configuration required to onboard new APIs

---

## Ocelot Gateway

Ocelot is configured via `ocelot.json` and uses route-based forwarding to downstream services. Swagger endpoints are aggregated using the `SwaggerKey` and `SwaggerEndPoints` config.

- Example upstream routes:
  - `/apiaudit/api/{everything}` → `https://restaudit.azurewebsites.net/api/{everything}`
  - `/hourtracker/api/{everything}` → `https://hourtrackerrest.azurewebsites.net/api/{everything}`

---

## YARP Gateway

YARP is configured via `appsettings.json` and uses a declarative model for routes and clusters. Swagger UI is hosted centrally in the gateway and proxies each downstream's Swagger JSON.

- Swagger UI available at: `https://localhost:7153/swagger/index.html`
- Example upstream routes:
  - `/apiaudit/api/{*}` → `https://restaudit.azurewebsites.net/api/{*}`
  - `/hourtracker/api/{*}` → `https://hourtrackerrest.azurewebsites.net/api/{*}`
- Aggregated Swagger JSONs:
  - `/apiaudit/swagger/v1/swagger.json`
  - `/hourtracker/swagger/v1/swagger.json`

---

## Getting Started

### Prerequisites

- .NET SDK 9.0 or later
- Visual Studio or VS Code
- Two backend REST APIs (or mock endpoints)

### Run Ocelot Gateway

```bash
dotnet run --project ApiGateway.Ocelot.RestApi

```

---


