# Alexey Sharunov

Software Engineer in Test. I design and evolve test infrastructure for distributed
backend systems: microservices, asynchronous pipelines, and cross-team contracts.

- Telegram: https://t.me/AlexeySharunov0
- LinkedIn: https://www.linkedin.com/in/sharunovalexey/
- Email: alexeysharunov0@gmail.com
- Location: Serbia (remote)

---

## About

I work in test automation with a focus on test architecture rather than individual
checks. My main work is building frameworks that survive service growth: they scale
with the number of tests, give predictable feedback in CI, and don't turn into a
dumping ground of hardcoded values.

I started with manual testing and gradually moved into engineering. Most of my time
now goes into designing validation layers, contracts, and test observability. Manual
testing hasn't gone away - exploratory API and integration testing remains part of
the job, especially when a problem needs to be localized quickly at the boundary
between services.

---

## Test Architecture

### Testing Layers

I build the pyramid deliberately: unit and component tests cover logic, integration
tests cover service interaction, E2E covers critical user and business scenarios.
I don't try to make E2E exhaustive - it's expensive to maintain and slow in CI.

- **Unit / component** - fast logic checks, isolation via mocks and fixtures.
- **Integration** - real brokers, databases, and caches; serialization and delivery
  semantics validation.
- **Contract** - Pact between teams to catch breaking changes before merge.
- **E2E** - only end-to-end scenarios that actually break silently.
- **Performance** - load runs with automated gates at the PR stage.

### Framework Design

I build frameworks around reusable layers, not around a set of tests:

- **Client layer** - wrappers over REST, gRPC, WebSocket, and Kafka with a unified
  interface, retries, and timeouts.
- **Data layer** - factories and fixtures, test data generation, state isolation
  between tests.
- **Validation layer** - schema-first checks via Pydantic and JSON Schema, unified
  rules for all endpoints.
- **Reporting layer** - Allure, Prometheus metrics, run history in TestOps.
- **Infrastructure layer** - parallelization, environment configuration, CI/CD
  integration.

This approach allows new services to be added without rewriting the test base and
keeps maintenance cost under control.

### Parallelization and CI Performance

Regression is a bottleneck if left unmanaged. I parallelized 1200+ integration tests
via `pytest-xdist` across 8 CI nodes, cutting regression time from 45 to 12 minutes.
Separately, I dealt with flaky tests: a quarantine based on Allure TestOps and
Prometheus reduced CI noise from 15% to 2.5%, so the team could trust a red build.

### Contracts and Compatibility

Contract testing via Pact covered the interaction of 8 cross-team services. This
resulted in an 87% reduction in integration incidents - primarily in trust & safety
policy engines and content moderation workflows, where a breaking change is expensive.

### Test Observability

Tests are a system too, and they need to be observed. I integrated coverage metrics
and run results into Prometheus and Grafana, and centralized the history of 1500+ runs
in TestOps. Error localization is done through logs in ELK and Loki, not through
"let's try rerunning it."

### Performance Gates

Load runs on Locust with automated gates in CI - 3 performance regressions were
blocked at the PR stage, before reaching the main branch.

---

## Stack

**Languages and frameworks:** Python, Java, Go, pytest, pytest-asyncio, pytest-xdist,
pytest-rerunfailures, FastAPI, asyncio, Flask, unittest, Celery

**API testing:** requests, httpx, WebSockets, REST, GraphQL, OpenAPI (Swagger),
Postman/Newman

**Databases:** PostgreSQL (psycopg2, asyncpg), MySQL, Redis, SQLite, MongoDB, Alembic

**Monitoring and reporting:** Prometheus client, Allure, Grafana, ELK Stack, Loki

**Data processing:** pandas, numpy, openpyxl, BeautifulSoup, lxml, XML/JSON, PySpark

**Infrastructure:** Docker, Docker Compose, CI/CD (GitHub Actions / GitLab CI / Jenkins),
Vault (hvac), python-dotenv, Ansible, Terraform, Kubernetes, Makefile

**Tools:** faker, pydantic, jsonschema, pre-commit, mypy, ruff, Linux, Git, Bash

---

## Working Principles

- Tests are code. The same requirements apply: readability, maintainability, review.
- Automate what gives predictable feedback, not what's trendy.
- A red CI should mean a real problem, otherwise people stop using it.
- Contracts and schemas catch errors earlier than E2E and are cheaper to maintain.
- Test observability matters no less than production observability.

---

## Education

Presidential Academy - Information Systems and Programming
September 2022 - June 2026

---

## Contacts

- Telegram: https://t.me/AlexeySharunov0
- LinkedIn: https://www.linkedin.com/in/sharunovalexey/
- Email: alexeysharunov0@gmail.com
