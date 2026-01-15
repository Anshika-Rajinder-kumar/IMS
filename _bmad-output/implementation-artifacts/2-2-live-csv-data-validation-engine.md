# Story 2.2: Live CSV Data Validation Engine

Status: ready-for-dev

## Story

As a College Coordinator,
I want instant feedback on duplicate names, missing emails, or invalid GPA formats during the upload,
so that I catch errors before they reach HR.

## Acceptance Criteria

- [ ] Flags rows with empty 'Email' or 'Name' fields
- [ ] Identifies duplicate emails within the batch or against existing student records
- [ ] Highlights GPA values outside the 0.0-10.0 or 0.0-4.0 range
- [ ] Summary of "Valid vs Rejected" rows displayed

## Tasks / Subtasks

- [ ] Validation Logic Implementation <!-- id: 2.2.1 -->
    - [ ] Create validation service for schema-specific candidate rules
- [ ] Cross-Reference Check <!-- id: 2.2.2 -->
    - [ ] Query existing `candidates` table to detect duplicates
- [ ] UI Feedback <!-- id: 2.2.3 -->
    - [ ] Display real-time validation summary components

## Dev Notes

- **Validation Rules**:
  - Email: Required, Valid Format, Unique.
  - Name: Required.
  - GPA: 0.0 - 10.0 (or 4.0).

### References

- [PRD: Data Validation Requirements](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr8-system-can-perform-structural-and-data-type-validation)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
