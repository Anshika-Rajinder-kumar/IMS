# Story 4.2: High-Speed Verification Split-View

Status: ready-for-dev

## Story

As an HR Executive,
I want a side-by-side view to inspect student data and transcript PDFs without switching tabs,
so that I can verify records at light speed.

## Acceptance Criteria

- [ ] Split-view pane shows student details on left and transcript PDF on right
- [ ] Navigate next/previous candidates with keyboard shortcuts (`j`/`k`)
- [ ] Mark approved/rejected without closing preview

## Tasks / Subtasks

- [ ] Split-View Layout <!-- id: 4.2.1 -->
    - [ ] Implement resizable side panel using Shadcn or similar
- [ ] PDF Preview Component <!-- id: 4.2.2 -->
    - [ ] High-performance PDF viewer integration (react-pdf or native browser embed)
- [ ] Keyboard Navigation Hook <!-- id: 4.2.3 -->
    - [ ] Global listeners for `j`, `k`, and status keys (e.g., `a` for approve, `r` for reject)

## Dev Notes

- **UX**: The "Side-by-side" requirement is key to the workflow. Check UX Spec for exact layout directions.

### References

- [UX: Verification Split-View](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md#side-by-side-review)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
