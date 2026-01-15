---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7]
lastStep: 7
inputDocuments:
  - "c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md"
  - "c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md"
  - "c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/product-brief-intern-management-system-2026-01-14.md"
workflowType: 'architecture'
project_name: 'Intern Management System'
user_name: 'Admin'
date: '2026-01-15'
lastStep: 2
---

# Architecture Decision Document

_This document builds collaboratively through step-by-step discovery. Sections are appended as we work through each architectural decision together._

## Project Context Analysis

### Requirements Overview

**Functional Requirements:**
The system is built around a structured 4-step recruitment funnel (Shortlisted → Interviewed → Docs Submitted → Offer Released). Architecturally, this requires a robust state machine or workflow engine to track candidate transitions and enforce data integrity. The core modules (IAM, Partner Management, CSV Intake, Funnel Management, Document Hub) suggest a modular backend architecture to handle discrete domain logic.

**Non-Functional Requirements:**
- **Performance:** Sub-1.5s response times for high-density dashboards will drive data fetching and caching strategies (e.g., optimized queries, pagination).
- **Security:** Multi-tenant data isolation is non-negotiable, requiring a data access layer that enforces tenant boundaries at the query level.
- **Auditability:** Immutable audit logs require a dedicated logging strategy (event sourcing or append-only audit tables).
- **Concurrency:** Support for 200+ concurrent students and 50+ HR users suggests a scalable stateless backend.

**Scale & Complexity:**
The project is a "Problem-Solving MVP" focused on replacing manual fragmentation. While the feature set is focused, the multi-tenancy and document handling elevate the complexity.

- Primary domain: Full-stack Web (SaaS B2B)
- Complexity level: Medium-High
- Estimated architectural components: 6-8 (Auth, Tenant Manager, Candidate/Funnel Engine, Document Service, CSV Processor, Notification Hub)

### Technical Constraints & Dependencies

- **Data Privacy:** PII must be encrypted at rest (AES-256).
- **CSV Dialects:** The validation engine must handle varied spreadsheet formats gracefully.
- **Legacy Integration:** Export functionality must support external processing systems.

## Starter Template Evaluation

### Primary Technology Domain
**B2B SaaS Web Application (Spring Boot + React)** based on project requirements and technical preferences.

### Stack Components

| Layer | Technology | Rationale |
| :--- | :--- | :--- |
| **Backend** | **Spring Boot 3.4+ / Java 21** | Industry standard for B2B. Provides robust security (Spring Security), native multi-tenancy (Hibernate 6), and high concurrency with Virtual Threads. |
| **Frontend** | **React / Vite** | Flexibility for high-density UI components. Vite offers faster development cycles than CRA. |
| **Database** | **PostgreSQL** | Native support for JSONB, indexing, and mature multi-tenancy (schemas/RLS). |
| **UI Library** | **Shadcn UI + Tailwind** | Sleek, "Pro" aesthetics with highly accessible components. |
| **Table Engine** | **TanStack Table/Virtual** | Essential for the "Offer Accelerator" dashboards with 100+ candidates. |

### Architectural Foundations Provided by Stack

- **Multi-Tenancy:** We will implement the **Discriminant Column** pattern using Hibernate 6's `@TenantId` for high scale, or **Schema-per-tenant** for stricter isolation. Initial recommendation: Discriminant Column with strict Spring Data JPA filters.
- **Security:** Spring Security with JWT (Stateless) for Auth, supporting future SSO integration.
- **Asynchronous Processing:** Spring `@Async` and `ApplicationEventPublisher` for CSV processing and notification triggers.
- **Document Management:** Secure storage in AWS S3 or a local file system (outside webroot) with strict MIME-type validation.

### Initialization Plan

1. **Backend:** Initialize via [Spring Initializr](https://start.spring.io/) with:
   - Dependencies: `Spring Web`, `Spring Data JPA`, `Spring Security`, `Flyway/Liquibase`, `Lombok`, `Validation`.
2. **Frontend:** Initialize via `npm create vite@latest` with `React + TypeScript`.
3. **Integration:** Configure CORS and API Response wrappers for consistent error handling.

## Core Architectural Decisions

### Decision Priority Analysis

**Critical Decisions (Block Implementation):**
- **Full Stack:** Spring Boot 4.x + React 19.x (Vite).
- **Multi-Tenancy:** Schema-per-tenant isolation for PII security.
- **Authentication:** Stateless JWT with RBAC (4 roles).
- **Deployment:** Local-first with Docker Compose.

**Important Decisions (Shape Architecture):**
- **State Management:** Zustand + TanStack Query.
- **API Standard:** RESTful with OpenAPI 3.1 (Contract-first).
- **UI System:** Shadcn UI + Tailwind CSS (React 19 Compiler).

**Deferred Decisions (Post-MVP):**
- **Cloud Hosting:** Deferred (User requested local deployment for now).
- **Advanced Monitoring:** OTLP/Grafana (Local setup only for now).

### Data Architecture
- **Database:** PostgreSQL 18.x (managed via Docker Compose).
- **Isolation:** **Schema-per-tenant**. Each college/partner gets a logical schema for maximum data safety.
- **Migrations:** Flyway for managed schema evolutions.

### Authentication & Security
- **Auth Model:** Stateless JWT (Spring Security 6.x / Spring Boot 4).
- **Authorization:** Method-level security (`@PreAuthorize`) for RBAC.
- **Data Protection:** AES-256 for PII at rest (as required by PRD).

### API & Communication Patterns
- **API Style:** RESTful.
- **Documentation:** `springdoc-openapi` (OpenAPI 3.1).
- **Error Handling:** Standardized JSON error response wrapper.

### Frontend Architecture
- **State:** **Zustand** for client-side UI state.
- **Data Fetching:** **TanStack Query** for server-side state/caching.
- **Performance:** React Virtual for high-density student lists (>100 candidates).

### Infrastructure & Deployment
- **Model:** **Local Deployment**.
- **Orchestration:** **Docker Compose** for running Backend, Frontend, and PostgreSQL as a cohesive unit.
- **File Storage:** Local filesystem (mounted volume) with directory-per-tenant isolation.
- **CI/CD:** GitHub Actions (Local build & Docker push).

### Decision Impact Analysis
1. **Implementation Sequence:** 
    - 1. Project Scaffolding (Monorepo/Docker).
    - 2. IAM/Auth Backend.
    - 3. Multi-tenant Data Layer.
    - 4. Student Funnel Core Logic.
## Implementation Patterns & Consistency Rules

### Pattern Categories Defined

**Critical Conflict Points Identified:** 5 areas where AI agents could make different choices (Database, API, Code, Structure, State).

### Naming Patterns

**Database Naming Conventions:**
- Tables: `snake_case`, plural (e.g., `student_profiles`).
- Columns: `snake_case` (e.g., `college_id`).
- Primary Keys: `id` (UUID recommended for distributed safety).

**API Naming Conventions:**
- Style: RESTful, `camelCase` for JSON fields.
- Versioning: `/api/v1/...`
- Endpoint naming: `/api/v1/partners`, `/api/v1/students`.

**Code Naming Conventions:**
- React Components: PascalCase (`FileListItem.tsx`).
- React Hooks: camelCase starting with `use` (`useCandidates.ts`).
- Java Classes: PascalCase (`StudentService.java`).
- Java Variables/Methods: camelCase (`processIntake()`).

### Structure Patterns

**Project Organization:**
- **Frontend:** Feature-based organization within `src/features/`. Each feature contains components, hooks, types, and logic.
- **Backend:** Domain-driven structure (`com.wissen.intern.domain.[domain]`).

**File Structure Patterns:**
- Tests: Co-located with components (`*.test.tsx`) in frontend; `src/test/java` in backend.
- Styles: Tailwind CSS (utility-first).

### Format Patterns

**API Response Formats:**
- Success: Direct object or list for simple cases; `{ "data": ... }` for complex pagination.
- Error: `{ "code": "STRING_ERROR_CODE", "message": "User-friendly message", "timestamp": "ISO-8601" }`.

**Data Exchange Formats:**
- Booleans: `true`/`false`.
- Dates: ISO-8601 strings.

### State Management Patterns
- **Zustand:** Used for global UI state (sidebar toggle, current tenant/college).
- **React Query:** Source of truth for all server-side data. Cache keys must be feature-specific (e.g., `['candidates', collegeId]`).

### Error Handling Patterns
- **Backend:** `@ControllerAdvice` for global exception mapping.
- **Frontend:** Global `ErrorBoundary` around feature containers; Toast notifications for transient errors.

### Enforcement Guidelines
**All AI Agents MUST:**
- Use the provided OpenAPI spec or generate one before implementing new endpoints.
- Ensure every database query is filtered by the `college_id` schema/tenant resolver.
## Project Structure & Boundaries

### Complete Project Directory Structure
```
intern-management-system/
├── docker-compose.yml       # Orchestrates local PostgreSQL, Backend, and Frontend
├── .gitignore
├── README.md
├── backend/                 # Spring Boot 4.x / Java 21
│   ├── src/main/java/com/wissen/intern/
│   │   ├── domain/
│   │   │   ├── iam/         # Identity & Access Management (RBAC)
│   │   │   ├── student/     # Student profiles & Funnel Flow
│   │   │   ├── partner/     # Partner (College) management
│   │   │   └── csv/         # CSV Intake & Validation Engine
│   │   ├── config/          # Security, Database, Multi-tenancy config
│   │   └── shared/          # Common utils and DTOs
│   ├── src/main/resources/
│   │   ├── db/migration/    # Flyway schema scripts
│   │   └── application.yml
│   └── pom.xml
├── frontend/                # React 19.x / Vite / TS
│   ├── src/
│   │   ├── features/
│   │   │   ├── auth/        # Login, MFA, Password reset
│   │   │   ├── dashboard/   # Unified Command Center
│   │   │   ├── funnel/      # Talent Funnel management
│   │   │   └── settings/    # Tenant-specific configurations
│   │   ├── components/      # UI components (Shadcn)
│   │   ├── store/           # Zustand state management
│   │   ├── api/             # TanStack Query hooks & Base API client
│   │   └── types/           # Type definitions (from OpenAPI)
│   ├── public/              # Static assets
│   ├── package.json
│   ├── vite.config.ts
│   └── tailwind.config.ts
└── docs/
    ├── api/                 # OpenAPI 3.1 Specification (YAML)
    └── architecture/        # High-level architecture diagrams
```

### Architectural Boundaries

**API Boundaries:**
- **External:** Exposed via REST at `/api/v1/`. Strict authentication required for all except login.
- **Contract:** OpenAPI 3.1 serves as the source of truth for all communication.

**Component Boundaries:**
- **Frontend:** Feature-based isolation. No direct imports allowed between logic in different features; use shared services.
- **Backend:** Domain-driven. Cross-domain communication MUST happen through services, not direct repository access.

**Data Boundaries:**
- **Isolation:** Managed at the database level via **PostgreSQL Schemas**.
- **Access:** Bound by the `college_id` resolution in the multi-tenancy filter.

### Requirements to Structure Mapping

- **CSV Intake:** Lives in `backend/domain/csv/` and `frontend/features/dashboard/`.
- **RBAC:** Managed in `backend/domain/iam/` and applied via Spring Security.
- **Student Funnel:** Orchestrated in `backend/domain/student/` with state management in `frontend/features/funnel/`.

### Development Workflow Integration
- **Local Dev:** Run `docker-compose up` to start PostgreSQL. Run backend and frontend locally for hot-reloading.
- **Build:** Maven (Backend) and NPM (Frontend) within Docker multi-stage builds.
