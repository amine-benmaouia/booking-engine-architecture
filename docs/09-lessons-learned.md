# Lessons Learned

## 1. Integrations Are Architecture Problems

API integration is not only about sending requests and reading responses. The real challenge is designing stable internal abstractions.

## 2. Normalize Early

Every provider should be converted into the internal domain model as early as possible.

## 3. Test Environments Are Not Always Reliable

Provider test environments may return incomplete prices, missing fields, or unrealistic booking states.

## 4. Logging Is Critical

Good logs should capture internal request ID, provider name, provider reference, request status, error code, and execution time. Sensitive data should be masked.

## 5. Caching Must Be Used Carefully

Caching improves performance but should not compromise booking accuracy. Final price and booking state should be revalidated before critical operations.

## 6. Good Adapters Make Platforms Scalable

A clean adapter layer makes it possible to add new providers without rewriting the entire application.
