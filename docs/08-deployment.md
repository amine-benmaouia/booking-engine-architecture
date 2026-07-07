# Deployment

## Overview

A production booking system needs reliable deployment, environment separation, monitoring, and safe release practices.

## Deployment Architecture

```text
Internet
   |
Nginx Reverse Proxy
   |
Dockerized Backend Services
   |
   +--> PostgreSQL
   +--> Redis
   +--> Provider APIs
```

## Environments

A healthy deployment separates development, test/QA, and production.

Each environment should have separate variables, provider credentials, database, Redis instance, and logs.

## Docker

Docker makes deployment predictable and repeatable.

```yaml
services:
  api:
    image: booking-api
  postgres:
    image: postgres
  redis:
    image: redis
  nginx:
    image: nginx
```

## Release Principles

- Keep environment variables outside the codebase
- Use CI/CD for repeatable deployments
- Test provider integrations before production release
- Log provider requests and responses safely
- Never commit credentials
- Keep rollback strategy simple
