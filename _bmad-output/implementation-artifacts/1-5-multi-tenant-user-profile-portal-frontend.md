# Story 1.5: Multi-Tenant User Profile Portal (Frontend)

Status: ready-for-dev

## Story

As a College Coordinator,
I want to view and modify my institutional contact details on a secure dashboard,
so that my profile information stays up to date.

## Acceptance Criteria

- [ ] Navigate to 'Partner Profile' section (Coordinator role only)
- [ ] See institutional data for ONLY my college
- [ ] Update 'Primary Contact', 'Phone', and 'Office Address' fields
- [ ] Clicking 'Save' persists changes with success notification

## Tasks / Subtasks

- [ ] Dashboard Layout & Navigation <!-- id: 1.5.1 -->
    - [ ] Setup React Router with role-based guards
    - [ ] Create sidebar/navigation for 'Partner Profile'
- [ ] Profile Form Implementation <!-- id: 1.5.2 -->
    - [ ] Create reactive form using TanStack Table/Query or standard React State
    - [ ] Integration with `PATCH /api/v1/partners/{id}`
- [ ] UI Components <!-- id: 1.5.3 -->
    - [ ] Use Shadcn UI for input fields, buttons, and toast notifications

## Dev Notes

- **Frontend Stack**: Vite / React 19 / TS / Shadcn UI.
- **Data Fetching**: Use TanStack Query for caching and invalidation.

### References

- [UX: Coordinator View](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md#coordinator-portal)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
