# Story 6.1: Immutable System-Wide Audit Logger

Status: ready-for-dev

## Story

As an HR Admin,
I want a centralized, append-only log of every status change and user action,
so that we are fully compliant with Wissen's 3-year audit policy.

## Acceptance Criteria

- [ ] Automatically created `audit_logs` entry for any state change
- [ ] Includes 'Timestamp', 'User ID', 'Action Type', 'Subject ID', 'Previous State', 'New State'
- [ ] Logs are read-only and cannot be modified/deleted via UI

## Tasks / Subtasks

- [ ] Audit Entity & Repository <!-- id: 6.1.1 -->
    - [ ] Flyway Migration for `audit_logs` in `public` schema
- [ ] Interceptor / Aspect Implementation <!-- id: 6.1.2 -->
    - [ ] Implementation of `@AuditAction` annotation or Hibernate listeners
- [ ] Admin Audit Viewer <!-- id: 6.1.3 -->
    - [ ] Simple UI for HR Admins to search and filter logs

## Dev Notes

- **Immutability**: Database user used by application should not have `DELETE` or `UPDATE` permissions on the `audit_logs` table (if possible at DB level).
- **Compliance**: NFR6 mandates 3-year retention.

### References

- [Architecture: Audit Patterns](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md#audit-trail)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
