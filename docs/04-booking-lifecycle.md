# Booking Lifecycle

## Overview

A booking platform must handle the full lifecycle from search to post-booking operations.

```text
Search -> Availability -> Pricing -> Reservation -> Payment -> Ticket Generation -> Recall Booking -> Cancellation
```

## Search

The customer selects route, date, passengers, vehicles, and optional services.

## Availability

Provider adapters request available sailings, seats, cabins, vehicles, and onboard services. Responses are normalized into a common internal structure.

## Pricing

The pricing engine calculates the final customer price based on sailing, passengers, vehicle, accommodation, meals, services, taxes, and provider-specific rules.

## Reservation

The booking service creates a reservation with the provider and stores both internal reservation ID and provider booking reference.

## Payment

The payment workflow confirms whether the customer paid successfully and handles success, failure, expiration, retry, or cancellation flows.

## Ticket Generation

After payment, the system retrieves or generates ticket documents.

## Recall Booking

Recall booking retrieves the latest provider-side booking state and verifies consistency with internal data.

## Cancellation

Cancellation depends on provider rules. The system normalizes cancellation results and keeps an audit trail.
