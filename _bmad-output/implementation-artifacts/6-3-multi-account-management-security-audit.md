# Story 6.3: Multi-Account Management & Security Audit

Status: ready-for-dev

## Story

As an HR Admin,
I want to review all active users and their login timestamps,
so that I can ensure only authorized personnel have access to our student schemas.

## Acceptance Criteria

- [ ] List all system users across all roles
- [ ] See 'Last Login' timestamp and 'Account Status' (Active/Locked)
- [ ] Ability to deactivate account instantly, terminating active sessions

## Tasks / Subtasks

- [ ] User Audit API <!-- id: 6.3.1 -->
    - [ ] GET `/api/v1/users/audit` (HR Admin Only)
- [ ] Session Management logic <!-- id: 6.3.2 -->
    - [ ] Integration with Spring Session (or JWT blacklisting) for instant eviction
- [ ] Security Dashboard UI <!-- id: 6.3.3 -->
    - [ ] Unified view for user access control

## Dev Notes

- **Security**: Termination of active sessions should be immediate (force token invalidation or session expiry).

### References

- [PRD: Security Audit Requirements](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#nfr6-audit-logs-for-status-changes)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
