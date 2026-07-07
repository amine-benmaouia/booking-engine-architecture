# System Architecture

## High-Level Overview

```text
Client Applications
        |
        v
Booking REST API
        |
        v
Booking Service Layer
        |
        +--> Provider Adapter A --> REST API
        +--> Provider Adapter B --> XML API
        +--> Provider Adapter C --> SOAP/XML API
        |
        v
Internal Domain Model
        |
        +--> PostgreSQL
        +--> Redis
```

## Layers

### API Layer

Receives HTTP requests, validates inputs, authenticates users, and forwards requests to the service layer.

### Service Layer

Coordinates business workflows such as search, pricing, booking, payment, ticket generation, recall booking, and cancellation.

### Provider Adapter Layer

Contains provider-specific logic. Each adapter converts internal requests into provider-specific payloads and normalizes provider responses.

### Domain Layer

Defines core entities such as Route, Sailing, Passenger, Vehicle, Accommodation, Price, Reservation, Payment, and Ticket.

### Persistence Layer

Stores reservations, payment status, booking history, provider references, users, agencies, and logs.

## Why This Architecture

The main goal is to prevent provider-specific logic from leaking into the application. The booking service should call the same internal interface regardless of whether the provider uses REST, XML, or SOAP.

## Trade-Offs

This architecture requires more upfront design because each provider needs an adapter. However, it improves maintainability and makes future integrations easier.
