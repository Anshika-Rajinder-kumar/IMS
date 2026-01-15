# Story 1.4: User Management API (RBAC)

Status: ready-for-dev

## Story

As an HR Admin,
I want to manage internal (HR) and external (Coordinator) accounts,
so that the system enforces tiered access across roles.

## Acceptance Criteria

- [ ] Create new user account with role (HR_ADMIN, HR_EXEC, COLLEGE_COORDINATOR)
- [ ] User correctly mapped to target role in IAM database
- [ ] 'COLLEGE_COORDINATOR' user must be associated with valid partner ID
- [ ] User can only login to features permitted by their specific role

## Tasks / Subtasks

- [ ] Define RBAC Roles <!-- id: 1.4.1 -->
    - [ ] Setup `Role` and `Authority` structure in Spring Security
- [ ] User Management Service <!-- id: 1.4.2 -->
    - [ ] POST `/api/v1/users` (HR Admin only)
    - [ ] Validation: Coordinators MUST have a partner ID
- [ ] Security Enforcement <!-- id: 1.4.3 -->
    - [ ] Apply `@PreAuthorize` or similar filters to existing and future endpoints

## Dev Notes

- **Roles**: `HR_ADMIN`, `HR_EXEC`, `COLLEGE_COORDINATOR`, `STUDENT`.
- **RBAC**: Use Spring Security's Method Security.

### References

- [PRD: Role-Based Access Control](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#user-roles)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
