# Story 1.1: Project Scaffolding & Local Environment Setup

Status: ready-for-dev

## Story

As a Developer,
I want to initialize the Spring Boot and React project structures with Docker Compose,
so that I have a consistent development environment for all agents.

## Acceptance Criteria

- [ ] Monorepo structure created with `backend` (Spring Boot 4) and `frontend` (React 19/Vite) folders
- [ ] `docker-compose.yml` provided for running PostgreSQL 18
- [ ] Project builds successfully with `mvn clean install` and `npm install`.

## Tasks / Subtasks

- [ ] Setup folder structure and root configuration <!-- id: 1.1.1 -->
    - [ ] Initialize git repository (if not already done)
    - [ ] Create `backend` directory
    - [ ] Create `frontend` directory
- [ ] Initialize Backend (Spring Boot 4.x) <!-- id: 1.1.2 -->
    - [ ] Use Java 21
    - [ ] Configure `pom.xml` with required dependencies (Spring Web, Security, JPA, Flyway, PostgreSQL)
- [ ] Initialize Frontend (React 19 / Vite / TS) <!-- id: 1.1.3 -->
    - [ ] Setup Vite project with TypeScript
    - [ ] Configure basic Tailwind CSS and Shadcn UI foundation
- [ ] Setup Docker Infrastructure <!-- id: 1.1.4 -->
    - [ ] Create `docker-compose.yml` with PostgreSQL 18 service
    - [ ] Configure database environment variables and health checks

## Dev Notes

- **Architecture Compliance**: Follow the monorepo pattern specified in [architecture.md](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md).
- **Tech Stack**: Spring Boot 4.x (Check latest milestone/RC if needed), React 19, Java 21, PostgreSQL 18.
- **Naming**: Use kebab-case for directories and standard Java package naming (e.g., `com.wissen.ims`).

### Project Structure Notes

- Root: `intern-management-system/`
  - `backend/`
  - `frontend/`
  - `docker_compose.yml`

### References

- [Architecture: Mono-repo Structure](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md#project-structure)
- [Architecture: Technology Stack](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md#technology-stack)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
