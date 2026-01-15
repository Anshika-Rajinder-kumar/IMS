# Story 5.1: "Ready for Offer" Selection & Validation

Status: ready-for-dev

## Story

As an HR Executive,
I want the system to automatically flag candidates who have cleared both the interview and the doc compliance check,
so that I don't accidentally release an offer to an ineligible student.

## Acceptance Criteria

- [ ] Candidate automatically flagged as 'Ready for Offer' when in 'Docs Submitted' stage AND all required documents are 'Approved'
- [ ] Use 'Ready for Offer' quick-filter to see this list
- [ ] System prevents moving a candidate to 'Offer Released' if compliance status is not 'Approved'

## Tasks / Subtasks

- [ ] Eligibility Calculation logic <!-- id: 5.1.1 -->
    - [ ] Create database view or calculated property for "Ready for Offer" status
- [ ] Dashboard Quick-Filters <!-- id: 5.1.2 -->
    - [ ] Add pre-defined filter for "Ready for Offer" to the HR Command Center
- [ ] Transition Guard <!-- id: 5.1.3 -->
    - [ ] Implement validator preventing transition to 'Offer Released' state without compliance approval

## Dev Notes

- **Logic**: `Ready for Offer` = (`funnel_stage` == `DOCS_SUBMITTED` && `compliance_status` == `APPROVED`).
- **Security**: This is a critical safety check to prevent legal/procedural errors.

### References

- [PRD: Final Selection FRs](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr18-hr-executives-can-track-the-state)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
