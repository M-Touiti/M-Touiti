<!-- Profile README for github.com/M-Touiti/M-Touiti. Rewritten 1 Nov 2026.
     Rules: every claim is backed by a repository or by the CV; no placeholders; no rates.
     When api-gateway-resilience-demo gets its load-test report and ADRs, replace the
     "In progress" line below with a second "Featured" entry (same shape as the first). -->

# Mohamed Touiti

**Senior Backend Engineer · Java, Spring Boot, Apache Kafka, Kubernetes · event-driven microservices**

Paris, France (CET) · Open to a fully remote Senior Backend / Tech Lead role in any time zone, and to freelance contracts
· [LinkedIn](https://www.linkedin.com/in/mohamed-touiti) · [hello@mtouiti.dev](mailto:hello@mtouiti.dev)

9+ years building event-driven, cloud-native systems for tier-one banks. At BNP Paribas I designed and delivered the
migration of a card-transaction monolith to Kubernetes microservices handling about 5 million Kafka events a day, in
production since January 2026 with zero incidents. I own work end to end: target architecture, governance reviews,
infrastructure, CI/CD, load testing and cut-over, and I write the team's engineering standards (service template,
Git workflow, code review). Remote or hybrid since 2020, including an English-speaking project.

---

## Featured: a Kafka microservice that was load-tested, fixed and documented

**[spring-kafka-microservice-demo](https://github.com/M-Touiti/spring-kafka-microservice-demo)** — card-subscription
service: Kafka consumer plus REST API, hexagonal architecture in five Maven modules (the domain module has zero
dependencies), Spring Boot 3, PostgreSQL, Resilience4j, Testcontainers.

What sets it apart from a typical demo:

- **Load-tested with k6, before and after.** The first run found nine defects: duplicate rows under concurrency, a
  malformed message stalling a partition, a database connection held across the external call, failures never retried,
  a hanging partner API blocking health checks, and more. All nine are fixed, re-measured and written up in the
  [load-test report](https://github.com/M-Touiti/spring-kafka-microservice-demo/blob/main/performance/README.md),
  with raw k6 output, charts and a one-command script to reproduce the suite.
- **Architecture Decision Records.** Five one-page ADRs (context, decision, consequences) in
  [docs/adr](https://github.com/M-Touiti/spring-kafka-microservice-demo/tree/main/docs/adr), each tied to the
  measurements that motivated or revised it.
- **Integration tests on real infrastructure.** Testcontainers for PostgreSQL and Kafka, WireMock for the partner
  API, run by GitHub Actions on every push and pull request.

| Measured on 1 → 3 replicas (2 CPUs, 1 GB each; stubbed 50 ms partner API) | Before | After |
|---|---|---|
| REST writes | 165 → 476 req/s | 418 → 1,271 req/s, no 5xx |
| Kafka consumption | 14.4 → 38.7 events/s | 64.9 → 175 events/s, one row per event across 72,000 events |
| 5 parallel POSTs for each of 200 cards | 991 rows | 200 rows |
| Rows left `FAILED` after a 40 s partner outage | 2,015, never retried | 0, retried within 5–7 minutes |
| Malformed Kafka message | partition stopped, log flood | routed to the dead-letter topic, next message processed |

The figures come from one laptop, so the ratios matter more than the absolute numbers. The report states the method,
every finding and the limits that remain.

**In progress:** the same load-test report and ADRs for `api-gateway-resilience-demo`.

---

## Open-source projects

Every repository below has GitHub Actions CI, automated unit and integration tests, and a README on architecture and
design decisions.

| Repository | What it shows | Stack |
|---|---|---|
| [card-subscription-service ](https://github.com/M-Touiti/spring-kafka-microservice-demo) | Event-driven service with retry and dead-letter topic, circuit breaker, idempotent writes; k6 load tests and ADRs | Java 21, Spring Boot 3, Kafka, PostgreSQL, Resilience4j, Testcontainers, k6 |
| [order-management-ddd](https://github.com/M-Touiti/order-management-ddd) | DDD tactical patterns (aggregates, value objects, domain events) and hexagonal architecture reference | Java 25, Spring Boot 4, PostgreSQL, Testcontainers |
| [api-gateway-resilience-demo](https://github.com/M-Touiti/api-gateway-resilience-demo) | Reactive gateway: Resilience4j circuit breaker and retry, Redis token-bucket rate limiting, JWT validation, Prometheus and a provisioned Grafana dashboard | Java 21, Spring Cloud Gateway, Redis, Prometheus, Grafana, WireMock |
| [notification-service](https://github.com/M-Touiti/notification-service) | Multi-channel notifications (email, SMS, push) driven by Kafka events, with retry and dead-letter topics | Spring Boot 3, Kafka, PostgreSQL, Testcontainers |
| [credit-scoring-api](https://github.com/M-Touiti/credit-scoring-api) | Credit-scoring ML API with model registry, batch prediction, audit trail and drift monitoring | Python, FastAPI, scikit-learn, MLflow, PostgreSQL |

Also on this profile: [payment-account-api](https://github.com/M-Touiti/payment-account-api) (Spring Security 6, JWT,
RFC 7807 errors), [batch-processing-demo](https://github.com/M-Touiti/batch-processing-demo) (Spring Batch 5, CSV and
Excel import with skip policy and restart), [financial-etl-pipeline](https://github.com/M-Touiti/financial-etl-pipeline)
(Kafka to PostgreSQL market-data ETL with OHLCV aggregation) and
[fastapi-finance-api](https://github.com/M-Touiti/fastapi-finance-api) (async FastAPI, SQLAlchemy 2.0, JWT).

---

## How I work

- **Decisions are written down.** ADRs record the context, the choice and what it costs, so the next engineer can
  disagree with evidence rather than guesswork.
- **Measure before claiming.** "Production-grade" means a load test, a failure-injection run and the raw data to back
  it, with limits stated as plainly as results.
- **The domain owes nothing to the framework.** Pure-Java domain modules, ports as plain interfaces, adapters at the
  edge; the same structure I use at work in the team's service template.
- **Design for failure.** Circuit breakers, bounded retries, dead-letter and replay topics, idempotent writes; failures
  are recorded and retried, not dropped.

---

## Background

- **BNP Paribas**, Senior Backend Engineer, Jun 2025 – present: monolith to Kubernetes microservices, Kafka at about
  5 million events a day, team engineering standards, on-call.
- **Société Générale** (via SAPIT), 2023 – 2025: sanctions-screening platform, Spring Boot, React, Python on AWS Lambda,
  English-speaking remote-first team.
- **EDF** (via SAPIT), 2022: DDD and hexagonal microservices on Spring WebFlux, Kafka, Elasticsearch, Spark and Airflow
  pipelines.
- **Crédit Agricole and CACEIS** (via VERMEG), 2019 – 2021: loan and trading back ends, fully remote from 2020.
- **AWS Certified Developer – Associate** (2025). Engineering degree in computer engineering (2018). English and French,
  fluent.

Contact: [hello@mtouiti.dev](mailto:hello@mtouiti.dev) · [linkedin.com/in/mohamed-touiti](https://www.linkedin.com/in/mohamed-touiti)
