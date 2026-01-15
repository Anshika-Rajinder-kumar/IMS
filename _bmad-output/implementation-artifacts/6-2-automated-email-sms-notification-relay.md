# Story 6.2: Automated Email/SMS Notification Relay

Status: ready-for-dev

## Story

As a Student / Coordinator,
I want to receive instant alerts when my compliance status changes or a new batch is processed,
so that I don't have to keep checking the portal.

## Acceptance Criteria

- [ ] Trigger email alert when student's document is 'Rejected' or 'Approved'
- [ ] email includes specific reason for rejection
- [ ] Notification sent to College Coordinators when CSV batch processing finishes

## Tasks / Subtasks

- [ ] Notification Service Foundation <!-- id: 6.2.1 -->
    - [ ] Integration with Spring Mail (SMTP/SendGrid/SES)
- [ ] Event-Driven Notification logic <!-- id: 6.2.2 -->
    - [ ] Publish internal Spring Events for status changes
- [ ] Template Engine <!-- id: 6.2.3 -->
    - [ ] Create simple HTML/Text templates for alerts

## Dev Notes

- **NFRs**: Trigger notifications asynchronously to avoid slowing down the main UI thread.

### References

- [PRD: Automated Student Alerts](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md#fr21-system-can-trigger-automated-email-alerts)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
