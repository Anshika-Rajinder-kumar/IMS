# Story 4.3: Batch Status Progression Engine

Status: ready-for-dev

## Story

As an HR Executive,
I want to select multiple candidates and move them to the next stage (e.g., "Interviewed" → "Docs Submitted") in one click,
so that I can process hundreds of candidates daily.

## Acceptance Criteria

- [ ] Select multiple candidates and apply 'Batch Advance'
- [ ] Validates transition sequence (Shortlisted → Interviewed → Docs Submitted → Offer Released)
- [ ] Updates with a single timestamped transaction
- [ ] Success notification with update count

## Tasks / Subtasks

- [ ] Multi-Select UI Logic <!-- id: 4.3.1 -->
    - [ ] Checkbox selection and bulk action toolbar
- [ ] Funnel State Machine <!-- id: 4.3.2 -->
    - [ ] Service to enforce allowed status transitions
- [ ] Batch Update API <!-- id: 4.3.3 -->
    - [ ] `PATCH /api/v1/candidates/batch`

## Dev Notes

- **Data Integrity**: Use transactions to ensure all-or-nothing updates for a batch.
- **Audit**: Every candidate updated in the batch must have an individual audit entry.

### References

- [PRD: Funnel Stages](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr11-hr-executives-can-move-candidates)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
