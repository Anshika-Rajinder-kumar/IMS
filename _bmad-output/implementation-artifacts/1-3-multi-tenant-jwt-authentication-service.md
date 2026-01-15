# Story 1.3: Multi-Tenant JWT Authentication Service

Status: ready-for-dev

## Story

As a system user,
I want to log in and receive a secure token that identifies my college/tenant,
so that I can only access data belonging to my university.

## Acceptance Criteria

- [ ] Returns a JWT token upon valid login to `/api/v1/auth/login`
- [ ] Token contains a `tenant_id` or `schema_name` claim
- [ ] Subsequent requests with this token automatically use the correct schema context
- [ ] Blocked from accessing data in other partner schemas

## Tasks / Subtasks

- [ ] Setup Spring Security & JWT <!-- id: 1.3.1 -->
    - [ ] Configure JWT filter to extract tenant context from claims
    - [ ] Implement authentication manager for cross-schema users (or master user table)
- [ ] Implement Login API <!-- id: 1.3.2 -->
    - [ ] POST `/api/v1/auth/login` returning JWT with tenant info
- [ ] Contextual Schema Routing <!-- id: 1.3.3 -->
    - [ ] Integrate JWT tenant claim with Hibernate's `CurrentTenantIdentifierResolver`

## Dev Notes

- **Auth Strategy**: JWT with Tenant Claim.
- **Cross-Schema**: Users might reside in a master `users` table or be schema-specific. Architecture suggests a shared user base for management convenience but data isolation for candidates.

### References

- [Architecture: Security Patterns](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md#security)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
