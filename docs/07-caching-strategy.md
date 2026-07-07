# Caching Strategy

## Purpose

Provider APIs can be slow, rate-limited, or unstable. Caching improves performance and reduces unnecessary provider calls.

## What Can Be Cached

Good candidates for caching include routes, ports, passenger types, vehicle categories, static configuration, and short-lived availability responses.

Sensitive data that should be revalidated includes final prices, reservation status, payment status, and ticket status.

## Redis Usage

```text
Client Request
      |
Cache Lookup
      |
 HIT or MISS
      |
Return Data or Provider API
      |
Store in Redis
```

## TTL Strategy

| Data Type | Suggested TTL |
|---|---|
| Static configuration | 24h |
| Ports/routes | 24h |
| Availability | 5–15 min |
| Search results | 5–10 min |
| Final price | Revalidate before booking |

## Trade-Offs

Caching improves speed but can introduce stale data. For booking systems, final price and reservation state should be validated before critical operations.
