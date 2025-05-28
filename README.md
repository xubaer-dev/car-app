
# SDTL-CAR-QUOTATION-MONOLITH-GO-V1.4

**Prepared for:** Mr. Masudur Rahman
**Prepared by:** Strawberry Dhaka Tech Limited
**Confidentiality Level:** Client Confidential
**Version:** 1.4
**Location:** Dhaka, Bangladesh
**Date:** May 28, 2025

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Project Objectives & Success Metrics](#project-objectives--success-metrics)
3. [Scope of Work](#scope-of-work)
   - 3.1 [Inclusions](#inclusions)
4. [Technical Deliverables](#technical-deliverables)
5. [System Architecture & Technology Stack](#system-architecture--technology-stack)
   - 5.1 [Backend Architecture](#backend-architecture)
   - 5.2 [Frontend Architecture](#frontend-architecture)
   - 5.3 [Infrastructure Overview](#infrastructure-overview)
6. [Architecture Diagrams](#architecture-diagrams)
   - 6.1 [High-Level System Flow](#high-level-system-flow)
   - 6.2 [Component-Level Breakdown](#component-level-breakdown)
   - 6.3 [Sequence Diagram: Car Wash Booking](#sequence-diagram-car-wash-booking)
   - 6.4 [Design Principles & Architectural Considerations](#design-principles--architectural-considerations)
7. [Development Timeline](#development-timeline)
   - 7.1 [Gantt Chart Overview](#gantt-chart-overview)
   - 7.2 [Sprint Breakdown](#sprint-breakdown)
8. [Resource Allocation & Team Structure](#resource-allocation--team-structure)
9. [Cost Breakdown & Financial Model](#cost-breakdown--financial-model)
10. [Project Delivery Methodology](#project-delivery-methodology)
11. [Scalability & Performance Benchmarks](#scalability--performance-benchmarks)
12. [Quality Assurance & Testing Strategy](#quality-assurance--testing-strategy)
13. [Governance & Change Control Process](#governance--change-control-process)
14. [Key Assumptions & Dependencies](#key-assumptions--dependencies)
15. [Payment Terms & Milestone Schedule](#payment-terms--milestone-schedule)
16. [Maintenance & Support Plan](#maintenance--support-plan)
17. [Approval & Sign-off](#approval--sign-off)

---

## 1. Executive Summary

Strawberry Dhaka Tech Limited is pleased to present this revised quotation (V1.4) to Mr. Masudur Rahman for the development of the Car App, a multi-vendor automotive marketplace tailored for the Bangladeshi market. The platform connects users with service providers and sellers through a mobile application (Flutter) and a web platform (Next.js), encompassing four key phases: Car Wash, Vehicle Services, Parts Selling, and Advertisements. Built on a Go-based monolithic architecture, the solution prioritizes simplicity, performance, and cost efficiency, with infrastructure fully managed by Strawberry Dhaka Tech Limited on AWS Cloud. Key highlights include:

- Scalability: Supports 1–1.8 million users, 5 million annual transactions, and 10,000 concurrent users with 1,000 transactions per second (TPS).
- Performance: Achieves P99 latency <250ms under peak load.
- Localization: Features bilingual (Bangla/English) UI, BDT pricing, Dhaka-centric geospatial services, and bKash/Nagad payment integration.
- Technology Stack: Go (net/http), Flutter, Next.js, PostgreSQL with PostGIS, Redis, Amazon S3.
- Infrastructure: AWS Cloud with 99.9% uptime, managed by Strawberry Dhaka Tech Limited.
- Budget: Total labor cost of 2,749,000 BDT.
- Timeline: 7 months (May 28, 2025 – December 28, 2025, 30 weeks) delivered via Agile/Scrum with 2-week sprints.

This document outlines the technical, operational, and financial details to deliver a robust, scalable, and user-centric automotive marketplace aligned with Mr. Masudur Rahman’s vision.

---

## 2. Project Objectives & Success Metrics

| Objective         | Key Result (KR)                       | Measurement                     | Owner             |
|-------------------|---------------------------------------|---------------------------------|-------------------|
| Functional Delivery| Complete Car App with all four phases | User Acceptance Testing (UAT) sign-off | Project Manager |
| Performance       | P99 latency <250ms at 10,000 concurrent users | Locust load test reports | DevOps Engineer   |
| Scalability       | Handle 1,000 TPS with 99.9% uptime    | Grafana/Prometheus dashboards   | DevOps Engineer   |
| Localization      | Bilingual UI (Bangla/English), BDT pricing, Dhaka geo-search | QA validation report | QA Engineer     |
| Security          | JWT authentication, TLS 1.3, PCI-DSS, Bangladesh Digital Security Act 2018 | Penetration test report (OWASP Top 10) | Security Lead |
| Maintainability   | 80% test coverage, modular Go code, CI/CD pipeline | SonarQube metrics, Jenkins pipeline status | Backend Developer |
| User Experience   | Intuitive UI/UX with <3-second page loads | Usability testing (NPS >8) | Frontend Developer |

---

## 3. Scope of Work

### 3.1 Inclusions

**Core Features:**
- User Management: Registration/login via Email, Google OAuth, bKash/Nagad SSO.
- Service Listings: Filterable by vehicle type, location (Dhaka), and price (BDT).
- Booking System: Real-time availability for car wash and vehicle services using PostGIS geospatial matching.
- Parts Selling: E-commerce functionality for automotive parts with inventory management.
- Advertisements: Tools for sellers to create banners and sponsored listings.
- Payment Integration: bKash, Nagad, Stripe, PayPal (BDT transactions).
- Notifications: Email, SMS, and push notifications via Firebase and Twilio/SSL Wireless.
- Admin Panel: CRUD operations for users, services, products, ads, and analytics dashboard.

**Non-Functional Requirements:**
- Performance: Go monolith with Redis caching and PostgreSQL connection pooling.
- Security: JWT authentication, TLS 1.3, PCI-DSS compliance, adherence to Bangladesh Digital Security Act 2018.
- Localization: Bangla/English UI, BDT currency, GMT+6 timezone, Dhaka-focused geolocation.
- Monitoring: zerolog logging, Prometheus metrics, Grafana dashboards, AWS CloudWatch.

---

## 4. Technical Deliverables

| Category          | Deliverables                          | Format        | Tool/Platform         |
|-------------------|---------------------------------------|---------------|-----------------------|
| Backend           | Go monolith with RESTful APIs, PostgreSQL/PostGIS | Source code | GitHub Enterprise     |
| Mobile App        | Flutter app (iOS & Android), bilingual UI | APK/IPA       | Google Play Store, App Store |
| Web App           | Next.js app (SEO-optimized, responsive, TypeScript) | Deployed site | Vercel                |
| API Documentation | OpenAPI 3.0 specification             | api.yaml      | Swagger UI            |
| Architecture Diagrams | High-level, component-level, sequence diagrams | Mermaid/ASCII | Confluence            |
| Test Reports      | Unit, integration, load test results   | PDF/JUnit     | Jenkins, Locust       |
| User Manuals      | Admin/end-user guides (Bangla/English)| PDF           | Google Docs           |
| Deployment Scripts| CI/CD pipelines, Docker configurations| YAML          | Jenkins, Docker Hub   |

---

## 5. System Architecture & Technology Stack

### 5.1 Backend Architecture (Go Monolith)

- HTTP Server: net/http for lightweight RESTful APIs.
- Middleware:
  - Authentication: JWT (RS256) using golang-jwt/jwt/v5.
  - Rate Limiting: golang.org/x/time/rate (100 req/s/client).
  - Logging: zerolog for structured JSON logs.
  - CORS: Configured for Flutter and Next.js clients.
- Routing: Custom net/http router with tree-based structure (e.g., /api/users).
- Error Handling: Centralized ErrorResponse with bilingual (Bangla/English) messages.
- Dependency Injection: Manual DI for improved testability.
- Database: PostgreSQL v15 with PostGIS.
  - Connection Pooling: pgxpool for <100ms query latency.
  - Schema: Normalized tables (users, bookings, orders, products, ads).
- Caching: Redis v7 (go-redis/redis/v8) with 90% hit rate.
  - Keys: service:lat:lon (TTL: 10m), payment:tx_id (TTL: 5m).
- Resilience: Custom circuit breakers, go-retry with exponential backoff.
- Security: JWT (RS256), TLS 1.3, validator/v10 input sanitization.
- Logging: zerolog to AWS CloudWatch Logs.
- Monitoring: Prometheus metrics to AWS CloudWatch.

### 5.2 Frontend Architecture

- Mobile: Flutter (Dart) with Provider, Dio, and l10n for Bangla/English localization.
- Web: Next.js (TypeScript, Tailwind CSS, Server-Side Rendering, Vercel deployment).

### 5.3 Infrastructure Overview

- Cloud Provider: AWS Cloud, fully managed by Strawberry Dhaka Tech Limited.
- Compute: 5x EC2 instances (20 vCPU, 40GB RAM, Ubuntu 22.04) with Auto Scaling.
- Database: Amazon RDS PostgreSQL (High Availability, pgBouncer), ElastiCache Redis.
- Storage: Amazon S3 for images and metadata.
- Networking: VPC with private subnets, Route 53, AWS WAF for DDoS protection.
- Cloud Support: AWS provisioning and monitoring managed by Strawberry Dhaka Tech Limited.

---

## 6. Architecture Diagrams

### 6.1 High-Level System Flow

**Diagram:**
```
graph TD
    A[Client: Flutter Mobile App<br>Provider, Dio, l10n] -->|HTTPS (TLS 1.3, JSON)| B[AWS API Gateway<br>Rate Limiting, WAF]
    A2[Client: Next.js Web App<br>TypeScript, SSR, i18n] -->|HTTPS (TLS 1.3, JSON)| B
    B -->|REST (JWT RS256, JSON)| C[Go Monolith: net/http]

    subgraph Go Monolith [Go Monolith (Layered Architecture)]
        C -->|HTTP/REST| D[User Service<br>POST /api/users/register<br>POST /api/users/login]
        C -->|HTTP/REST| E[Booking Service<br>POST /api/bookings/create<br>GET /api/bookings/search]
        C -->|HTTP/REST| F[Order Service<br>POST /api/orders/create<br>GET /api/orders]
        C -->|HTTP/REST| G[Payment Service<br>POST /api/payments/initiate]
        C -->|HTTP/REST| H[Notification Service<br>POST /api/notifications/send]
        C -->|HTTP/REST| I[Review Service<br>POST /api/reviews/create]
        C -->|HTTP/REST| J[Advertisement Service<br>POST /api/ads/create]
        C -->|HTTP/REST| K[Admin Service<br>GET /api/admin/users]
        D -->|Dependency Injection| L[Repository Layer]
        E -->|Dependency Injection| L
        F -->|Dependency Injection| L
        G -->|Dependency Injection| L
        H -->|Dependency Injection| L
        I -->|Dependency Injection| L
        J -->|Dependency Injection| L
        K -->|Dependency Injection| L
    end

    L -->|SQL (pgxpool)| M[(Amazon RDS PostgreSQL v15<br>PostGIS, users, bookings, orders, ads)]
    L -->|Cache (TTL: 5-10m)| N[(Amazon ElastiCache Redis v7<br>90% Hit Rate)]
    L -->|Object Storage (S3)| O[(Amazon S3<br>Images, Metadata)]

    subgraph External Integrations
        G -->|HTTPS (JSON)| P[bKash/Nagad API]
        G -->|HTTPS (JSON)| Q[Stripe/PayPal API]
        H -->|HTTPS (FCM)| R[Firebase Cloud Messaging]
        H -->|HTTPS (JSON)| S[Twilio/SSL Wireless]
    end

    C -->|Metrics (Prometheus)| T[Amazon CloudWatch]
    C -->|Logs (zerolog)| U[AWS CloudWatch Logs]

    classDef client fill:#f9f,stroke:#333,stroke-width:2px;
    classDef monolith fill:#bbf,stroke:#333,stroke-width:2px;
    classDef storage fill:#bfb,stroke:#333,stroke-width:2px;
    classDef external fill:#fbf,stroke:#333,stroke-width:2px;
    class A,A2 client;
    class C monolith;
    class M,N,O storage;
    class P,Q,R,S external;
```

**Description:** Clients (Flutter mobile app and Next.js web app) connect via HTTPS to AWS API Gateway, which applies rate limiting and WAF protection before forwarding requests to the Go monolith. The monolith employs a layered architecture (Controller, Service, Repository) to interact with Amazon RDS PostgreSQL (with PostGIS for geospatial queries), ElastiCache Redis for caching, and Amazon S3 for storage. External integrations include bKash, Nagad, Stripe, PayPal, Firebase, and Twilio/SSL Wireless for payments and notifications. Metrics and logs are streamed to AWS CloudWatch for observability.

### 6.2 Component-Level Breakdown

**Diagram:**
```
+-------------------------+       +-------------------------+
| Flutter Mobile App      |       | Next.js Web App         |
| (Provider, Dio, l10n)   |       | (TypeScript, SSR, i18n) |
| - Bangla/English UI     |       | - SEO-Optimized         |
| - BDT Formatting        |       | - Tailwind CSS          |
+-------------------------+       +-------------------------+
                |                       |
                v                       v
        +-------------------------------+
        | AWS API Gateway (WAF)         |
        | - Rate Limiting (100 req/s)   |
        | - TLS 1.3, JWT Validation    |
        +-------------------------------+
                        |
                        v
        +-------------------------------+
        | Go Monolith (net/http)        |
        | - Middleware (JWT, Rate Limit, Logging) |
        | - Controller Layer            |
        |   - REST Endpoints (/api/*)   |
        | - Service Layer              |
        |   - Business Logic            |
        | - Repository Layer           |
        |   - DB/Cache Access          |
        |                               |
        | +-----------+ +-----------+   |
        | | User      | | Booking   |   |
        | | - Register| | - Search  |   |
        | | - Login   | | - Create  |   |
        | +-----------+ +-----------+   |
        | +-----------+ +-----------+   |
        | | Order     | | Payment   |   |
        | | - Create  | | - Initiate|   |
        | | - List    | | - Status  |   |
        | +-----------+ +-----------+   |
        | +-----------+ +-----------+   |
        | | Notification| | Review   | |
        | | - Send Push| | - Create  |  |
        | | - Send SMS | | - List    |  |
        | +-----------+ +-----------+   |
        | +-----------+ +-----------+   |
        | | Ads       | | Admin     |   |
        | | - Create  | | - Manage   |   |
        | | - Track   | | - Analytics|   |
        | +-----------+ +-----------+   |
        +-------------------------------+
           |       |       |       |
           v       v       v       v
    +------+-------+-------+-------+------+
    |      |       |       |       |      |
+---+----+ +--+----+ +--+----+ +--+----+ +--+----+
|RDS      |  |Elasti-| |S3    | |External | |CloudWatch|
|PostgreSQL|  |Cache  | |      | |APIs    | |         |
|HA Cluster|  |Redis  | |Images| |(bKash, | | - TPS   |
| - users |  | - listings | |Metadata| |Nagad,  | | - Latency|
| - bookings | | - payments| |      | |Stripe, | | - Uptime|
| - orders |  | - ads    | |      | |Firebase,| +---------+
| - PostGIS|  |TTL: 5-10m| |      | |Twilio)  |
+----------+  +-------+ +-------+ +---------+
           +-------------------------------+
           | AWS CloudWatch Logs           |
           | - zerolog (JSON Logs)        |
           | - Log Aggregation, Search    |
           +-------------------------------+
```

**Description:** The Flutter mobile app and Next.js web app connect to the Go monolith via AWS API Gateway, which enforces rate limiting, TLS 1.3, and JWT validation. The monolith includes middleware for security and logging, with services (User, Booking, Order, Payment, Notification, Review, Ads, Admin) handling business logic. The Repository layer interfaces with PostgreSQL (users, bookings, orders, ads), Redis (caching listings and payments), and S3 (images and metadata). External APIs (bKash, Nagad, Stripe, Firebase, Twilio) are integrated for payments and notifications. Logs and metrics are sent to AWS CloudWatch for monitoring.

### 6.3 Sequence Diagram: Car Wash Booking

**Diagram:**
```
sequenceDiagram
    participant U as User (Flutter/Next.js)
    participant C as AWS API Gateway
    participant M as Go Monolith
    participant P as Amazon RDS PostgreSQL
    participant R as Amazon ElastiCache Redis
    participant B as bKash API
    participant F as Firebase

    U->>C: POST /api/bookings/create (JWT, JSON: {service_id, lat, lon})
    C->>M: Forward Request (Validate JWT, Rate Limit)
    M->>R: Check Cache (key: "service:lat:lon")
    R-->>M: Cache Miss
    M->>P: SELECT * FROM services WHERE ST_DWithin(location, :point, 5km)
    P-->>M: Service Details
    M->>R: Store Cache (key: "service:lat:lon", TTL: 10m)
    M->>P: INSERT INTO bookings (user_id, service_id, timestamp)
    P-->>M: Booking ID
    M->>B: POST /v1/payments (JSON: {amount, currency: BDT})
    B-->>M: Payment URL
    M-->>U: Return Booking ID, Payment URL
    U->>B: Complete Payment (Redirect)
    B-->>M: Webhook: Payment Success
    M->>P: UPDATE bookings SET status = 'confirmed'
    M->>F: Send Push Notification (Booking Confirmed)
    F-->>U: Push Notification
```

**Description:** The user initiates a car wash booking via the Flutter or Next.js client, sending a POST request to AWS API Gateway. The request is validated and forwarded to the Go monolith, which checks Redis for cached service data. On a cache miss, it queries PostgreSQL (PostGIS) for nearby services, caches the result, and creates a booking. The monolith initiates a payment via bKash, returning a payment URL to the user. Upon payment completion, a webhook updates the booking status, and a push notification is sent via Firebase.

### 6.4 Design Principles & Architectural Considerations

- Layered Architecture: Controller → Service → Repository for modularity and maintainability.
- Scalability: AWS Auto Scaling, Redis caching (90% hit rate), pgBouncer for connection pooling.
- Performance: P99 latency <250ms with GIST indexes for geospatial queries.
- Security: JWT (RS256), TLS 1.3, AWS WAF, and PCI-DSS compliance.
- Localization: Bilingual UI (Bangla/English), BDT currency formatting, Dhaka-centric geolocation.
- Resilience: Circuit breakers and retries for external API integrations.
- Observability: AWS CloudWatch for metrics and logs, ensuring 99.9% uptime.
- Trade-Offs: Monolithic architecture simplifies initial development; modular design supports future migration to microservices if needed.

---

## 7. Development Timeline

The project spans 7 months (May 28, 2025 – December 28, 2025, 30 weeks), delivered through 15 two-week sprints using Agile/Scrum, with parallel development and testing.

### 7.1 Gantt Chart Overview

| Phase                                | Duration | Start Week | End Week | Key Milestones                      | Deliverables                              |
|--------------------------------------|----------|------------|----------|-------------------------------------|-------------------------------------------|
| Sprint 1-4: Core Platform & Car Wash | 8 Weeks  | Week 1     | Week 8   | Week 1: Requirements sign-off; Week 4: User/Booking APIs; Week 8: Staging | Go APIs, Flutter/Next.js UIs, staging environment |
| Sprint 5-8: Vehicle Services & Parts | 8 Weeks  | Week 9     | Week 16  | Week 9: Service APIs; Week 12: Parts APIs; Week 16: Beta | Order/Review APIs, extended UIs, beta environment |
| Sprint 9-11: Ads & Admin Tools       | 6 Weeks  | Week 17    | Week 22  | Week 17: Ads APIs; Week 20: Admin dashboard; Week 22: Production prep | Ads/Analytics/Admin APIs, production-ready platform |
| Sprint 12-15: Testing & Launch       | 8 Weeks  | Week 23    | Week 30  | Week 23: End-to-end testing; Week 26: Beta launch; Week 30: Production launch | Fully tested platform, launched app/web, performance report |

### 7.2 Sprint Breakdown

- **Sprint 1 (Weeks 1–2): Planning & Setup**
  - Tasks: Requirements workshop, OpenAPI specification, Go monolith setup, Jenkins CI/CD, Flutter/Next.js scaffolding.
  - Acceptance Criteria: OpenAPI approved, /health endpoint live, UI with Bangla/English toggle.
  - Effort: 10 person-days.

- **Sprint 2 (Weeks 3–4): User Management**
  - Tasks: User APIs (register/login), PostgreSQL schema, pgBouncer setup, login UI, unit tests (80% coverage).
  - Acceptance Criteria: Users can register/login, schema supports geospatial queries, UI displays BDT.
  - Effort: 11 person-days.

- **Sprint 3 (Weeks 5–6): Car Wash Booking**
  - Tasks: Booking APIs, Redis caching, booking UI, integration tests.
  - Acceptance Criteria: Booking API with PostGIS, UI supports service search.
  - Effort: 11 person-days.

- **Sprint 4 (Weeks 7–8): Payments & Staging**
  - Tasks: Payment APIs, bKash/Nagad mock integration, payment UI, staging deployment.
  - Acceptance Criteria: Payment redirects functional, staging environment live.
  - Effort: 11 person-days.

- **Sprint 5 (Weeks 9–10): Vehicle Services**
  - Tasks: Service APIs, Order APIs, service UI, integration tests.
  - Acceptance Criteria: Service APIs functional, UI supports vehicle services.
  - Effort: 10 person-days.

- **Sprint 6 (Weeks 11–12): Vehicle Services Completion**
  - Tasks: Complete service APIs, order UI, circuit breakers, load testing (5,000 users).
  - Acceptance Criteria: Full service functionality, P99 latency <250ms.
  - Effort: 10 person-days.

- **Sprint 7 (Weeks 13–14): Parts Selling**
  - Tasks: Parts catalog APIs, inventory management, parts UI, integration tests.
  - Acceptance Criteria: Parts APIs functional, UI supports browsing.
  - Effort: 10 person-days.

- **Sprint 8 (Weeks 15–16): Parts Selling Completion**
  - Tasks: Review APIs, review UI, optimize PostgreSQL, beta release.
  - Acceptance Criteria: Parts selling complete, beta deployed.
  - Effort: 10 person-days.

- **Sprint 9 (Weeks 17–18): Advertisements**
  - Tasks: Ads APIs, ads UI, analytics integration, Redis tuning.
  - Acceptance Criteria: Ads functional, analytics dashboard live.
  - Effort: 10 person-days.

- **Sprint 10 (Weeks 19–20): Admin Tools**
  - Tasks: Admin APIs, dashboard UI, integration tests.
  - Acceptance Criteria: Admin dashboard functional.
  - Effort: 10 person-days.

- **Sprint 11 (Weeks 21–22): Ads & Admin Completion**
  - Tasks: Finalize ads/admin UI, performance tuning, production preparation.
  - Acceptance Criteria: Ads/admin tools complete, production-ready.
  - Effort: 10 person-days.

- **Sprint 12 (Weeks 23–24): Testing**
  - Tasks: End-to-end testing, security testing (OWASP ZAP), UAT with Mr. Masudur Rahman.
  - Acceptance Criteria: UAT sign-off, no critical vulnerabilities.
  - Effort: 9 person-days.

- **Sprint 13 (Weeks 25–26): Beta & Bug Fixes**
  - Tasks: Beta release, bug fixes, UI polish.
  - Acceptance Criteria: Beta feedback resolved, UI meets NPS >8.
  - Effort: 9 person-days.

- **Sprint 14 (Weeks 27–28): Launch Prep**
  - Tasks: Production deployment, notification integration, load testing (10,000 users).
  - Acceptance Criteria: Production environment live, performance benchmarks met.
  - Effort: 9 person-days.

- **Sprint 15 (Weeks 29–30): Launch & Support**
  - Tasks: Final launch, 2-week support, handover report.
  - Acceptance Criteria: Production live, handover complete.
  - Effort: 10 person-days.

---

## 8. Resource Allocation & Team Structure

| Role                        | Count | Monthly Cost (BDT) | Duration                 | Total Cost (BDT) | Key Responsibilities                     |
|-----------------------------|-------|--------------------|--------------------------|------------------|-----------------------------------------|
| Project Manager             | 1     | 100,000            | 7 months (May 28, 2025 – Dec 28, 2025) | 700,000          | Sprint planning, stakeholder communication |
| Go Backend Developer (Senior)| 1     | 75,000             | 7 months (May 28, 2025 – Dec 28, 2025) | 525,000          | System design, architecture, mentoring  |
| Go Backend Developer (Mid)   | 1     | 45,000             | 7 months (May 28, 2025 – Dec 28, 2025) | 315,000          | API implementation, module development  |
| Flutter Developer            | 1     | 62,000             | 7 months (May 28, 2025 – Dec 28, 2025) | 434,000          | iOS/Android app development            |
| Next.js Developer (PT)       | 1     | 30,000             | 7 months (May 28, 2025 – Dec 28, 2025) | 210,000          | Web app frontend, SEO optimization     |
| DevOps Engineer (PT)         | 1     | 35,000             | 7 months (May 28, 2025 – Dec 28, 2025) | 245,000          | CI/CD, AWS deployment, monitoring      |
| QA Engineer                  | 1     | 35,000             | 7 months (May 28, 2025 – Dec 28, 2025) | 245,000          | Testing (unit, integration, UAT)       |
| UI/UX Designer               | 1     | 50,000             | 1.5 months (May 28, 2025 – Jul 12, 2025) | 75,000       | Wireframes, UX flows, app/web design   |
|-----------------------------|-------|--------------------|--------------------------|------------------|-----------------------------------------|
| Total                       |       |                    |                          | 2,749,000        |                                         |

**Note:** The budget reflects updated monthly costs and timeline (May 28, 2025 – December 28, 2025). No buffer is included, and costs have been adjusted to achieve a total labor cost of 2,749,000 BDT.

---

## 9. Cost Breakdown & Financial Model

| Category       | Cost (BDT)  |
|----------------|-------------|
| Labor Costs    | 2,749,000   |
| Total          | 2,749,000   |

**Notes:** Infrastructure costs are fully managed by Strawberry Dhaka Tech Limited via AWS Cloud and are not included in the labor budget. All costs are in Bangladeshi Taka (BDT).

---

## 10. Project Delivery Methodology

- **Methodology:** Agile/Scrum with 2-week sprints.
- **Ceremonies:** Daily stand-ups, sprint planning, reviews, and retrospectives.
- **Tools:** Jira (task management), Confluence (documentation), Slack (communication).
- **CI/CD:** Jenkins pipelines, Docker containers, AWS ECS deployment.
- **Release Strategy:** Bi-weekly staging releases, culminating in a final production rollout.

---

## 11. Scalability & Performance Benchmarks

| Aspect        | Benchmark                                  |
|---------------|-------------------------------------------|
| Scalability   | AWS Auto Scaling, Redis caching (90% hit rate), pgBouncer for connection pooling |
| Performance   | P99 latency <250ms at 10,000 concurrent users |
| Transactions  | 1,000 TPS with <1% error rate             |
| Uptime        | 99.9% (monitored via AWS CloudWatch)      |

---

## 12. Quality Assurance & Testing Strategy

| Test Type           | Method                            | Tools             |
|---------------------|-----------------------------------|-------------------|
| Unit Testing        | Go testing package, 80% coverage  | SonarQube         |
| Integration Testing | Postman for APIs, Cypress for E2E | Jenkins           |
| Load Testing        | Locust for 10,000 users           | Locust            |
| Security Testing    | OWASP ZAP, PCI-DSS compliance     | OWASP ZAP         |
| Localization Testing| Manual QA for Bangla/English UI, BDT format | Manual QA |

**Automation:** 70% of test cases automated via Jenkins pipelines.

---

## 13. Governance & Change Control Process

- **Governance:** Weekly status meetings with Mr. Masudur Rahman, CTO, and Project Manager.
- **Change Control:**
  - Change requests submitted via Jira.
  - Impact analysis completed within 48 hours.
  - Approval required from Mr. Masudur Rahman and CTO.
- **Escalation Path:** Issues unresolved within 24 hours escalate to the CTO.

---

## 14. Key Assumptions & Dependencies

**Assumptions:**
- AWS infrastructure provisioned by Week 1.
- Payment gateway APIs (bKash, Nagad, Stripe, PayPal) available by Sprint 3.
- Timely feedback from Mr. Masudur Rahman during UAT.

**Dependencies:**
- AWS services (EC2, RDS, ElastiCache, S3).
- PostGIS-compatible PostgreSQL.
- Third-party API documentation and access.

---

## 15. Payment Terms & Milestone Schedule

**Total Cost:** 2,749,000 BDT

| Milestone                     | Amount (BDT) | Timeline         |
|-------------------------------|--------------|------------------|
| Upfront (Project kickoff)     | 824,700      | Start of Week 1 (May 28, 2025) |
| Car Wash Staging              | 687,250      | End of Week 8   |
| Vehicle Services & Parts (Beta)| 687,250      | End of Week 16  |
| Ads & Admin Tools             | 412,350      | End of Week 22  |
| Production Launch             | 137,450      | End of Week 30 (Dec 28, 2025) |

**Payment Terms:**
- Payments are due within 7 business days of milestone completion.
- Invoices will be issued in BDT via email.
- Bank transfer details to be provided by Strawberry Dhaka Tech Limited.

---

## 16. Maintenance & Support Plan

**Post-Launch Support:**
- **Duration:** 3 months free, provided by Strawberry Dhaka Tech Limited.
- **Scope:** Bug fixes (critical: 24 hours; non-critical: 72 hours), minor updates, support via email/Slack, tracked in Jira.
- **Deliverables:** Monthly support reports, updated manuals (Bangla/English).

**Ongoing Maintenance:**
- **Duration & Cost:** 6 months at 50,000 BDT/month (300,000 BDT total), renewable.
- **Scope:**
  - **Security:** Monthly patches, AWS Inspector scans, PCI-DSS compliance.
  - **Performance:** CloudWatch monitoring, PostgreSQL/Redis optimization, EC2 auto-scaling.
  - **Enhancements:** Analytics dashboard (AWS QuickSight), dynamic pricing, feedback system, multi-region expansion (e.g., Chittagong, Sylhet).
  - **Support:** Monthly reviews, bi-monthly training, quarterly disaster recovery drills, dedicated support manager.
- **SLAs:**
  - **Uptime:** 99.9% (monitored via CloudWatch).
  - **Incident Response:** Critical bugs (24 hours), non-critical (72 hours).
  - **Performance:** P99 latency <250ms, >90% Redis hit rate.

---

## 17. Approval & Sign-off

**Approved by:**
- **Name:** Mr. Masudur Rahman
- **Signature:** ________________________
- **Date:** ________________________

**Prepared by:**
- **Name:** ________________________
- **Designation:** Solutions Architect
- **Signature:** ________________________
- **Date:** May 28, 2025
