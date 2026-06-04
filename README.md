<!-- Mohamed — GitHub Profile README -->
<!-- Create repo: github.com/M-Touiti/M-Touiti, add this as README.md -->

<h1 align="center">Mohamed</h1>

<p align="center">
  Senior Backend Engineer · Java / Spring Boot · Python / FastAPI<br/>
  8+ years · Fintech · Microservices · Event-Driven Architecture<br/>
  Based in Paris · Open to international freelance contracts
</p>

<p align="center">
  <a href="https://www.upwork.com/freelancers/YOUR_UPWORK_ID">
    <img src="https://img.shields.io/badge/Upwork-Available-14a800?logo=upwork&logoColor=white"/>
  </a>
  <a href="https://www.malt.fr/profile/YOUR_MALT_ID">
    <img src="https://img.shields.io/badge/Malt-500--550€/day-FF6B35"/>
  </a>
  <a href="mailto:hello@mtouiti.dev">
    <img src="https://img.shields.io/badge/Email-hello@mtouiti.dev-EA4335?logo=gmail&logoColor=white"/>
  </a>
  <a href="https://www.linkedin.com/in/YOUR_LINKEDIN">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?logo=linkedin&logoColor=white"/>
  </a>
</p>

---

## What I Build

| Domain | Capabilities |
|---|---|
| **Event-Driven Systems** | Kafka, Dead Letter Topics, DDD, at-least-once delivery, Hexagonal Architecture |
| **Resilient API Gateways** | Circuit breaker, rate limiting, retry, JWT validation, WebFlux, Resilience4j |
| **Fintech / Payments** | Stripe integration, idempotency, webhooks, JWT/RBAC, PSD2-aware APIs |
| **Data Pipelines** | Real-time ETL, OHLCV aggregation, Kafka + Pandas + PostgreSQL |
| **ML APIs** | scikit-learn, MLflow model registry, feature engineering, FastAPI serving |
| **SaaS Products** | Multi-tenant billing systems, multi-currency, Docker Compose deploy |

---

## Tech Stack

**Backend — Java / Spring**

![Java](https://img.shields.io/badge/Java-21%20%2F%2025-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x%20%2F%204.x-6DB33F?logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6%20%2F%207-6DB33F?logo=springsecurity&logoColor=white)
![Spring Cloud Gateway](https://img.shields.io/badge/Spring%20Cloud%20Gateway-4.x-6DB33F?logo=spring&logoColor=white)
![Spring Kafka](https://img.shields.io/badge/Spring%20Kafka-4.x-231F20?logo=apachekafka)
![Spring Batch](https://img.shields.io/badge/Spring%20Batch-5.x-6DB33F?logo=spring&logoColor=white)
![Resilience4j](https://img.shields.io/badge/Resilience4j-2.x-6DB33F)
![OpenAPI](https://img.shields.io/badge/OpenAPI-3-6BA539?logo=openapiinitiative&logoColor=white)

**Backend — Python**

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?logo=fastapi&logoColor=white)

**Data & Messaging**

![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-3.x-231F20?logo=apachekafka)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-4169E1?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-7-DC382D?logo=redis&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0-D71F00)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)

**Observability**

![Prometheus](https://img.shields.io/badge/Prometheus-2.x-E6522C?logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-10.x-F46800?logo=grafana&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-2.x-0194E2?logo=mlflow)

**Frontend**

![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-3-06B6D4?logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-6-646CFF?logo=vite&logoColor=white)

**DevOps & Testing**

![Docker](https://img.shields.io/badge/Docker%20Compose-2496ED?logo=docker&logoColor=white)
![Testcontainers](https://img.shields.io/badge/Testcontainers-PostgreSQL%20%2F%20Kafka-black)
![Stripe](https://img.shields.io/badge/Stripe-API-635BFF?logo=stripe&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-Certified%20Developer-FF9900?logo=amazonaws&logoColor=white)

---

## Featured Projects

### [spring-kafka-microservice-demo](https://github.com/M-Touiti/spring-kafka-microservice-demo)

Event-driven microservice built on **Hexagonal (Clean) Architecture** — demonstrating
how to design a Kafka consumer that is resilient to failure, testable without infrastructure
mocks, and completely decoupled from the framework at the domain layer.

**Architecture — 4-module Maven (strict dependency rule)**

```
exposition ──► infrastructure ──► application ──► domain
                                                  (pure Java · zero framework deps)
```

**Key design decisions**

| Pattern | Implementation |
|---|---|
| Retry + DLT | `@RetryableTopic` — 3 attempts, ×2 exponential backoff, automatic Dead Letter Topic routing |
| DDD | Aggregate roots, value objects, domain events — JPA entities never cross into the domain |
| Hexagonal Architecture | Domain has zero Spring/JPA imports — ports are plain Java interfaces |
| Integration testing | Testcontainers spins up real Kafka + PostgreSQL — no H2, no mocks for the DB layer |
| API docs | OpenAPI 3 generated from controllers, browsable at `/api/docs` |

`Java 21` `Spring Boot 3` `Apache Kafka` `DDD` `Hexagonal Architecture` `Clean Architecture`
`Testcontainers` `Docker Compose` `OpenAPI` `Event-Driven` `Dead Letter Topic`

---

### [api-gateway-resilience-demo](https://github.com/M-Touiti/api-gateway-resilience-demo)

Production-grade reactive API Gateway implementing the full resilience stack —
circuit breaker, rate limiting, retry, and JWT validation — with a pre-built
Prometheus + Grafana observability dashboard.

**Filter chain (every request passes through in order)**

```
Client
  │
  ▼  RequestLoggingFilter      — logs method, path, latency (global)
  │
  ▼  JwtAuthenticationFilter   — validates HS256 token · injects X-User-Email / X-User-Role
  │
  ▼  RedisRateLimiter           — token bucket per user (50 req/s) or per IP (20 req/s) · 429 on exceed
  │
  ▼  CircuitBreaker             — Resilience4j · CLOSED → OPEN at 30–50% failure rate · fallback 503
  │
  ▼  Retry                      — exponential backoff on 502/503/504 · POST /payments never retried
  │
  ▼  Downstream Service
```

**Key design decisions**

| Pattern | Implementation |
|---|---|
| Circuit Breaker | Stricter for payments (30% / 30 s open) than user service (50% / 10 s open) |
| Rate Limiting | Redis Lua script — atomic token bucket, works across multiple gateway instances |
| JWT propagation | `Authorization` header removed before forwarding; downstream trusts `X-User-*` headers only |
| POST idempotency | `POST /payments` is excluded from retry to prevent double-charges |
| Observability | Prometheus scrapes `/actuator/prometheus`; Grafana shows P50/P95/P99, CB states, 429 rate |

`Java 21` `Spring Cloud Gateway` `Resilience4j` `Circuit Breaker` `Rate Limiting` `Redis`
`JWT` `Prometheus` `Grafana` `Docker Compose` `OpenAPI` `Microservices` `Resilience Patterns`

---

## Open-Source Portfolio

### Java / Spring Boot

| Project | Description | Stack |
|---|---|---|
| [spring-kafka-microservice-demo](https://github.com/M-Touiti/spring-kafka-microservice-demo) | Event-driven microservice — Kafka retry, DLT, Hexagonal Architecture, Testcontainers | Spring Boot 3, Kafka, DDD |
| [api-gateway-resilience-demo](https://github.com/M-Touiti/api-gateway-resilience-demo) | Reactive API gateway — circuit breaker, rate limiting, JWT, Prometheus + Grafana | Spring Cloud, Resilience4j, Redis |
| [payment-account-api](https://github.com/M-Touiti/payment-account-api) | REST API with JWT, RBAC, RFC 7807 error handling, Testcontainers | Spring Security 6, PostgreSQL |
| [notification-service](https://github.com/M-Touiti/notification-service) | Multi-channel notifications (Email / SMS / Push) unified under one API | Twilio, Firebase FCM, Thymeleaf |
| [batch-processing-demo](https://github.com/M-Touiti/batch-processing-demo) | CSV / Excel import pipeline with skip policy and job restart | Spring Batch 5, Apache POI |

### Python / FastAPI

| Project | Description | Stack |
|--|---|---|
| financial-etl-pipeline | Real-time market data ETL with OHLCV aggregation | aiokafka, Pandas, PostgreSQL |
| credit-scoring-api | ML credit scoring API with model versioning and audit logging | scikit-learn, MLflow, FastAPI |
| payment-service | Payment microservice with Stripe + Redis idempotency layer | FastAPI, Stripe, Redis |
| fastapi-finance-api | Personal finance manager REST API — async, JWT, Alembic | FastAPI, SQLAlchemy 2.0, JWT |
| price-monitor | E-commerce price monitor with multi-spider scraping and alerts | Scrapy, Celery, Redis |

---

## Architecture Principles

```
exposition → infrastructure → application → domain
                                            (pure Java / Python · zero framework deps)
```

Every project applies the same set of principles:

- **Hexagonal / Clean Architecture** — domain layer has no Spring, JPA, or Kafka imports
- **Event-driven** — Kafka with @RetryableTopic + Dead Letter Topic for fault tolerance
- **Resilience patterns** — circuit breaker, rate limiting, retry with exponential backoff
- **RFC 7807 ProblemDetail** — structured error responses on all REST APIs
- **Testcontainers** — integration tests run against real PostgreSQL and Kafka, never H2
- **OpenAPI 3** — auto-generated interactive docs on every service
- **JWT + RBAC** — stateless auth, role-based access control, 30 min access / 7 day refresh tokens
- `Decimal` not `float` for all monetary values · UUID primary keys · PostgreSQL for all persistence

---

## GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=M-Touiti&show_icons=true&theme=default&hide_border=true&count_private=true&include_all_commits=true&cache_seconds=86400" height="150"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=M-Touiti&layout=compact&theme=default&hide_border=true&langs_count=8&cache_seconds=86400" height="150"/>
</p>

---

## Hire Me

I'm available for **part-time and full-time remote contracts** — fintech backends,
microservices, data pipelines, and API development.

| Platform | Rate | Profile |
|---|---|---|
| **Upwork** | 55–80 $/h | [View profile](https://www.upwork.com/freelancers/YOUR_UPWORK_ID) |
| **Malt** | 500–550 €/day | [View profile](https://www.malt.fr/profile/YOUR_MALT_ID) |

**Response time**: within 24 hours · **Timezone**: CET (Paris)

---

<p align="center">
  <i>Open to fintech, payments, microservices, and data engineering contracts.</i>
</p>
