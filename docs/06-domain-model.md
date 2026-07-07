# Domain Model

## Overview

The domain model defines provider-independent business entities.

The booking engine should not expose provider-specific structures to the rest of the application.

## Main Entities

```text
User
Agency
Route
Sailing
Passenger
Vehicle
Accommodation
Service
Price
Reservation
Payment
Ticket
ProviderReference
```

## Reservation Model

```ts
type Reservation = {
  id: string;
  provider: string;
  providerReference: string;
  status: "option" | "confirmed" | "cancelled";
  passengers: Passenger[];
  vehicle?: Vehicle;
  outboundSailing: Sailing;
  returnSailing?: Sailing;
  price: PriceBreakdown;
  paymentStatus: "pending" | "paid" | "failed";
  createdAt: Date;
};
```

## Why a Domain Model Matters

A strong internal model allows the platform to support multiple providers without rewriting business logic. The frontend, reporting, payment workflow, and admin system consume the same internal structure regardless of provider.
