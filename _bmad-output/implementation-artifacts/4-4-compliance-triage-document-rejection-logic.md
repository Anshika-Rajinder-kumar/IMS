# Story 4.4: Compliance Triage & Document Rejection Logic

Status: ready-for-dev

## Story

As an HR Executive,
I want to approve/reject specific documents and provide canned or custom reasons (e.g., "Blurry scan"),
so that students know exactly how to fix their submission.

## Acceptance Criteria

- [ ] Menu with common rejection reasons (Blurry, Incorrect ID, Missing Signature)
- [ ] Custom note option for rejection
- [ ] Saving rejection updates compliance status to 'Action Required'
- [ ] Immutable audit log entry for rejection type and reviewer

## Tasks / Subtasks

- [ ] Rejection Dialog UI <!-- id: 4.4.1 -->
    - [ ] Popover or modal with reasons and text area
- [ ] Compliance Status Logic <!-- id: 4.4.2 -->
    - [ ] Service to calculate overall student status based on document approvals
- [ ] Audit Integration <!-- id: 4.4.3 -->
    - [ ] Log the specific reason string and reviewer ID

## Dev Notes

- **UX**: Use a "Triage" pattern for speed. High-quality rejection reasons reduce re-submissions.

### References

- [PRD: Document Approval FRs](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr15-hr-executives-can-view-approve-or-reject)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
