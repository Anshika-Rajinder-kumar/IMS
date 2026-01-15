# Story 5.2: Offer State Transition Engine (Sent/Accepted)

Status: ready-for-dev

## Story

As an HR Executive,
I want to track whether an offer has been sent or accepted,
so that I have an accurate headcount for the upcoming intern batch.

## Acceptance Criteria

- [ ] Mark offer as 'Sent' to move candidate to 'Offer Released' stage
- [ ] Update state to 'Accepted' or 'Declined'
- [ ] Candidate record locked from status changes when marked as 'Accepted'

## Tasks / Subtasks

- [ ] Offer Lifecycle Enum & States <!-- id: 5.2.1 -->
    - [ ] Define `OFFER_SENT`, `OFFER_ACCEPTED`, `OFFER_DECLINED` substates
- [ ] Record Locking Mechanism <!-- id: 5.2.2 -->
    - [ ] Implement field-level or record-level locks for 'Accepted' candidates
- [ ] Headcount Reporting <!-- id: 5.2.3 -->
    - [ ] Aggregation summary on the dashboard for accepted offers

## Dev Notes

- **Locking**: Once a candidate accepts, they should not be moved back through the funnel without explicit Admin override.

### References

- [PRD: Offer Management](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr20-the-system-can-lock-candidate-records)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
