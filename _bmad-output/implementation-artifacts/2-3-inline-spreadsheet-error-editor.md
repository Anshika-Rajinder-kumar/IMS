# Story 2.3: Inline "Spreadsheet" Error Editor

Status: ready-for-dev

## Story

As a College Coordinator,
I want a grid view to fix specific rejected rows directly in the browser,
so that I don't have to keep re-uploading the whole file.

## Acceptance Criteria

- [ ] Tabular grid showing ONLY rows with errors
- [ ] Highlight specific invalid cells in red
- [ ] Cell values editable directly in grid
- [ ] Instant re-validation after editing
- [ ] Fixed rows move from 'Error' to 'Ready' list

## Tasks / Subtasks

- [ ] Error Grid Component <!-- id: 2.3.1 -->
    - [ ] Implement editable data grid using TanStack Table
- [ ] Inline Re-validation Logic <!-- id: 2.3.2 -->
    - [ ] Trigger validation service on cell change
- [ ] Batch State Management <!-- id: 2.3.3 -->
    - [ ] Manage "Staging" state in frontend and persist to backend

## Dev Notes

- **Component Choice**: `TanStack Table` with `Shadcn UI` inputs for inline editing.
- **UX**: High responsiveness is critical for the "Instant" feel.

### References

- [Architecture: Inline CSV Error Editor](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md#ux-patterns)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
