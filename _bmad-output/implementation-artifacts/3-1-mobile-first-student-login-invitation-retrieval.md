# Story 3.1: Mobile-First Student Login & Invitation Retrieval

Status: ready-for-dev

## Story

As a Student,
I want to login to a mobile-friendly portal using the credentials sent to my email,
so that I can start my document submission process.

## Acceptance Criteria

- [ ] Visit login URL on mobile browser and enter temporary credentials
- [ ] Portal displays mobile-optimized welcome screen
- [ ] Prompted to set a permanent password
- [ ] Shown a checklist of required documents

## Tasks / Subtasks

- [ ] Mobile-Responsive Login Page <!-- id: 3.1.1 -->
    - [ ] Create simple, fast-loading login UI with Shadcn components
- [ ] First-Time Password Change Flow <!-- id: 3.1.2 -->
    - [ ] Implementation of `POST /api/v1/auth/password-reset`
- [ ] Document Requirement Service <!-- id: 3.1.3 -->
    - [ ] Fetch required documents for the student's category/session

## Dev Notes

- **UX**: Design must be thumb-friendly and high-contrast.
- **Security**: Temporary passwords should expire after first use.

### References

- [UX: Student Portal Mobile First](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md#student-mobile-portal)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
