# Story 5.3: Bulk Offer Export (CSV/Excel)

Status: ready-for-dev

## Story

As an HR Admin,
I want to export the "Ready for Offer" list to a CSV formatted for our internal payroll/onboarding system,
so that I can trigger the physical offer letters outside the system.

## Acceptance Criteria

- [ ] Generate CSV with all 'Ready for Offer' candidates
- [ ] Include PII (Name, College, Address, PAN/ID) and verification stamps
- [ ] Action logged for security auditing

## Tasks / Subtasks

- [ ] Export Service Implementation <!-- id: 5.3.1 -->
    - [ ] Generator for CSV with specific required headers
- [ ] PII Access Control <!-- id: 5.3.2 -->
    - [ ] Ensure only HR Admins can perform this export
- [ ] Audit Logging <!-- id: 5.3.3 -->
    - [ ] Record "OFFER_DATA_EXPORTED" in `audit_logs`

## Dev Notes

- **Security**: Exporting PII is a high-risk action. Ensure audit log captures the user and the timestamp.

### References

- [PRD: Export Requirements](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr19-hr-admins-can-export-ready-for-offer)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
