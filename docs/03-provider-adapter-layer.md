# Provider Adapter Layer

## Purpose

The provider adapter layer isolates third-party complexity from the rest of the application.

Each adapter is responsible for authentication, request mapping, response parsing, error normalization, provider-specific business rules, logging, and returning a unified internal response.

## Adapter Interface

```ts
interface BookingProvider {
  searchAvailability(request: AvailabilityRequest): Promise<AvailabilityResponse>;
  getPrice(request: PriceRequest): Promise<PriceResponse>;
  createReservation(request: ReservationRequest): Promise<ReservationResponse>;
  recallBooking(reference: string): Promise<BookingDetails>;
  cancelBooking(reference: string): Promise<CancellationResponse>;
}
```

## Example Flow

```text
Internal Price Request
        |
Provider Adapter
        |
Build REST/XML payload
Authenticate request
Send request to provider
Parse response
Normalize data
        |
Internal Price Response
```

## Benefits

- Provider complexity stays isolated
- Business logic remains stable
- New providers can be added without rewriting core services
- Errors are normalized consistently
- Testing becomes easier through mock adapters
