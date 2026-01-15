# Story 1.2: Multi-Tenant Schema & Partner Onboarding (Backend-Only)

Status: ready-for-dev

## Story

As an HR Admin,
I want to create university partner profiles that initialize their own PostgreSQL schemas,
so that student data is logically isolated from the very beginning.

## Acceptance Criteria

- [ ] Call the 'Create Partner' API with a university name and slug
- [ ] New record created in the master `partners` table
- [ ] Dedicated PostgreSQL schema created for this partner
- [ ] Action recorded in the system-wide audit log

## Tasks / Subtasks

- [ ] Implement Master Schema foundation <!-- id: 1.2.1 -->
    - [ ] Create Flyway migration for `partners` and `audit_logs` tables in `public` schema
- [ ] Implement Multi-Tenant Schema logic <!-- id: 1.2.2 -->
    - [ ] Create service to programmatically create new schemas on partner onboarding
    - [ ] Implement `CurrentTenantIdentifierResolver` and `MultiTenantConnectionProvider` for Hibernate
- [ ] Create Partner Onboarding API <!-- id: 1.2.3 -->
    - [ ] Implementation of `POST /api/v1/partners`
    - [ ] Logic to trigger schema creation and initial table setup (Flyway per schema if required)
- [ ] Audit Logging Integration <!-- id: 1.2.4 -->
    - [ ] Record "PARTNER_CREATED" event upon successful onboarding

## Dev Notes

- **Multi-Tenancy**: Use "Schema-per-tenant" strategy.
- **Security**: Ensure only HR Admins can access this API.
- **Audit**: Every schema creation must be traceable.

### Project Structure Notes

- Backend: Spring Boot services should handle schema resolution dynamically.

### References

- [Architecture: Multi-Tenancy Strategy](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md#multi-tenancy)
- [PRD: Multi-Tenant Requirements](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#functional-requirements)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
