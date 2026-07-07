# Business Problem

## Overview

Transportation booking platforms must often integrate multiple providers that expose different APIs for similar business operations.

Each provider can have different authentication, request formats, passenger models, vehicle models, pricing rules, reservation workflows, ticketing rules, and cancellation policies.

Without a unified architecture, the application becomes tightly coupled to every provider and difficult to maintain.

## Objective

Design a booking platform that exposes one consistent internal API while supporting multiple external transportation providers.

The platform should support multiple providers, keep business logic provider-independent, normalize provider-specific responses, handle booking workflows, and remain easy to extend.

## Main Engineering Challenges

### API Diversity

Some providers expose REST APIs, while others expose XML-based APIs. Each provider uses different naming conventions, schemas, authentication, and error handling.

### Data Normalization

The application must normalize passengers, vehicles, routes, cabins, seats, meals, prices, taxes, and booking references into one internal model.

### Reliability

External APIs can timeout, return inconsistent data, or behave differently between test and production environments.

### Performance

Availability and pricing calls can be slow. The platform must reduce latency while avoiding stale critical pricing data.

### Maintainability

Adding a new provider should not require changing the whole booking platform. Provider-specific complexity should stay isolated.
