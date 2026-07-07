# Pricing Engine

## Purpose

The pricing engine transforms provider-specific prices into one reliable internal pricing model.

Providers may split prices into base fare, passenger fare, accommodation, vehicle, meals, taxes, port fees, service fees, or discounts.

## Internal Price Model

```ts
type PriceBreakdown = {
  currency: string;
  baseAmount: number;
  taxes: number;
  fees: number;
  services: number;
  discount: number;
  totalAmount: number;
};
```

## Pricing Flow

```text
Provider Price Response
        |
Provider Mapper
        |
Internal Price Breakdown
        |
Validation
        |
Final Price Response
```

## Key Rules

- Never trust provider totals without validation
- Store provider raw price reference when needed
- Keep tax and net amount separated
- Avoid stale cache for final booking price
- Revalidate price before payment when possible

## Common Challenges

Some providers return tax separately while others include it in the total. Optional services and round trips may use different pricing structures. Provider test environments may return incomplete or unrealistic price data.
