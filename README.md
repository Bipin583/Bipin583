# Bipin

**Software Engineering Student (B.Tech Computer Science '27) &bull; College of Engineering Munnar**  
Specializing in backend systems, database concurrency, automated testing, and software reliability.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/bipin-583)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/Bipin583)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white)](mailto:b64957853@gmail.com)

---

## Technical Focus

I build deterministic backend systems where concurrency, transactional boundaries, and data integrity are enforced at the database level rather than through fragile application-layer assumptions. My work centers on high-integrity web platforms and reliability-focused developer tooling.

* **Backend Architecture & APIs**: REST API design, transaction isolation, role-scoped multi-tenancy, rate limiting, and idempotent webhook handlers.
* **Database Engineering**: PostgreSQL, schema migrations with Flyway, pessimistic row locking (`SELECT ... FOR UPDATE`), partial unique indexes, and audit logging with secret redaction.
* **Testing & Verification**: Integration testing against containerized databases (Testcontainers), unit test isolation (JUnit 5, pytest), mutation testing, and CI gating.
* **Software Reliability & ML**: Confidence calibration, epistemic uncertainty estimation, selective prediction, and regression test selection (RTS).

---

## Featured Projects

### [HostelOps &mdash; Multi-Console Hostel Operations Platform](https://github.com/Bipin583/HostelHub-Hostel-Management-System)
*Java 17 &bull; Spring Boot 3.5 &bull; PostgreSQL 17 &bull; Next.js 16 &bull; TypeScript 5.9 &bull; Docker &bull; Testcontainers*

A full-lifecycle accommodation and finance management system for university campuses serving three discrete roles: students, wardens, and administrators.

* **Database-Enforced Concurrency**: Eliminates room over-allocation using pessimistic row locks (`SELECT ... FOR UPDATE`) and partial unique indexes (`uq_allocations_active_student`, `uq_applications_one_pending`).
* **Financial Integrity**: Money stored strictly as integer paise; payment settlement enforces two-phase row locking on attempt and invoice records with HMAC-SHA256 callback verification and idempotency keys (`uq_fee_payments_idempotency`).
* **Security & Multi-Tenancy**: Memory-only access tokens paired with `httpOnly`, `Secure`, `SameSite=Strict` refresh cookies. Dynamic query scoping (`AccessScope`) isolates warden access across hostels at the database level.
* **Rigorous Verification**: 232 unit tests and 127 integration test executions against real `postgres:17-alpine` instances managed via Testcontainers in GitHub Actions CI.

### [ConfTest &mdash; Confidence-Calibrated Regression Test Selection](https://github.com/Bipin583/Conftest)
*Python 3.11 &bull; FastAPI &bull; LightGBM &bull; Streamlit &bull; SQLite &bull; pytest &bull; GitHub Actions*

A research-grade regression test selection (RTS) engine for Python CI pipelines that ranks test cases by calibrated failure risk and abstains to the full suite when uncertain.

* **Uncertainty-Aware Decision Engine**: Combines a 5-seed LightGBM ensemble with post-hoc probability calibration (Isotonic Regression) to measure epistemic disagreement and expected calibration error (ECE lowered from 0.0390 to 0.0242).
* **Safe Fallback (`SAFE_FULL_SUITE`)**: Selects budget-constrained test subsets (`FAST_SELECTED`) only when the model is confident; automatically abstains and executes the entire suite on out-of-distribution diffs or high model variance.
* **Empirical Validation**: Evaluated across 183 held-out commits (86,469 commit-test instances): achieved 100% failure recall (0 escapes) with a 3.11% execution count reduction and 0.0% wall-clock reduction due to a conservative 97.81% abstention rate.
* **Developer Ecosystem**: Features a FastAPI service, Streamlit visual inspection dashboard, CLI tool, signed GitHub webhook handler, and automated CI reporting.

---

## Technical Proficiency

| Domain | Technologies & Frameworks |
|---|---|
| **Languages** | Java (17/21), Python (3.11+), TypeScript, JavaScript, SQL |
| **Backend & APIs** | Spring Boot 3, Spring Data JPA, Spring Security, FastAPI, REST, Pydantic |
| **Frontend** | React 19, Next.js 16 (App Router), Vanilla CSS, HTML5 |
| **Data & Persistence** | PostgreSQL, Flyway, SQLite (WAL mode), Hibernate, SQLAlchemy |
| **DevOps & Infrastructure** | Docker, Docker Compose, GitHub Actions CI/CD, Maven, Linux |
| **Testing & Quality** | JUnit 5, Testcontainers, AssertJ, pytest, pytest-cov, Ruff |
| **ML & Reliability** | LightGBM, Scikit-learn, Calibration (ECE / Brier score), NetworkX, AST analysis |

---

## Engineering Principles

1. **Database Guarantees Over Application Checks**: Race conditions live in the gap between a read and a write. Critical invariants belong in database locks and constraints.
2. **Honest Metrics Over Inflated Claims**: In machine learning and developer tooling, transparently reporting abstention rates, feature constancy, and wall-clock baselines is essential for engineering trust.
3. **Reproducible Test Environments**: Tests that pass only with mock databases hide transaction isolation and DDL bugs. Integration tests must run against real database instances in CI.
4. **Security by Default**: Zero hardcoded fallback secrets, parameterized queries, strict CORS origins, in-memory tokens, and proactive secret redaction in audit feeds.

---

<p align="center">
  <sub>Open to Software Engineering Internships and Graduate Roles (2027) &bull; Munnar / Kerala / Remote</sub>
</p>
