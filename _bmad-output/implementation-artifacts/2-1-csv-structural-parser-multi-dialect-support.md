# Story 2.1: CSV Structural Parser & Multi-Dialect Support

Status: ready-for-dev

## Story

As a College Coordinator,
I want to drag and drop CSV shortlists,
so that the system handles various spreadsheet formats (Excel CSV, Google Sheets CSV) automatically.

## Acceptance Criteria

- [ ] Drag and drop a `.csv` file into the upload zone
- [ ] Correctly identify 'Name', 'Email', and 'GPA' headers (case-insensitive, common variations)
- [ ] Store raw data in a temporary staging area for validation

## Tasks / Subtasks

- [ ] UI Component: CSV Dropzone <!-- id: 2.1.1 -->
    - [ ] Create drag-and-drop zone with file type validation
- [ ] Parser Implementation <!-- id: 2.1.2 -->
    - [ ] Setup PapaParse or similar library for robust CSV parsing
    - [ ] Logic to normalize headers (e.g., "Full Name" -> "Name")
- [ ] Staging Backend API <!-- id: 2.1.3 -->
    - [ ] POST `/api/v1/batches/staging` accepting parsed JSON/CSV data
    - [ ] Store in temporary database structure (or schema-specific staging table)

## Dev Notes

- **Libraries**: `PapaParse` (Frontend), `Apache Commons CSV` or `OpenCSV` (Backend if parsing happens there).
- **Architecture**: Keep staging data isolated per tenant.

### References

- [UX: CSV Upload Flow](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md#csv-upload-logic)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
