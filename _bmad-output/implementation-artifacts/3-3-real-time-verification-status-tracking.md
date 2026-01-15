# Story 3.3: Real-Time Verification Status Tracking

Status: ready-for-dev

## Story

As a Student,
I want to see the real-time approval status of each document,
so that I know if I need to re-upload anything.

## Acceptance Criteria

- [ ] View status badges: 'Pending', 'Approved', or 'Rejected'
- [ ] See rejection reason prominently (if rejected)
- [ ] Direct option to 'Re-upload' for rejected items

## Tasks / Subtasks

- [ ] Status Dashboard UI <!-- id: 3.3.1 -->
    - [ ] Implementation of status tracker with progress bar
- [ ] Real-time Updates <!-- id: 3.3.2 -->
    - [ ] Use TanStack Query polling or WebSockets for live status
- [ ] Re-upload Logic <!-- id: 3.3.3 -->
    - [ ] Allow replacing document only if status is 'Rejected' or 'Action Required'

## Dev Notes

- **UX**: Visual clarity on "What to do next" is paramount.

### References

- [PRD: Student Portal FRs](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr14-students-can-securely-upload-pdfimage-files)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
