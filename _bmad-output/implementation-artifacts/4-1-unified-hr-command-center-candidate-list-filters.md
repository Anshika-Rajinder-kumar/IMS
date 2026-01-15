# Story 4.1: Unified HR Command Center (Candidate List & Filters)

Status: ready-for-dev

## Story

As an HR Executive,
I want a high-density dashboard with powerful filters for college, status, and compliance,
so that I can identify priority candidates in seconds.

## Acceptance Criteria

- [ ] High-density table of all candidates across authorized colleges
- [ ] Filter by 'College Name', 'Current Funnel Stage', and 'Compliance Status'
- [ ] Table loads and filters in < 1.5 seconds for 500+ records
- [ ] Search by name or email

## Tasks / Subtasks

- [ ] High-Performance Candidate API <!-- id: 4.1.1 -->
    - [ ] Optimized SQL queries for cross-schema (or aggregated) reporting
- [ ] Data Table Implementation (React) <!-- id: 4.1.2 -->
    - [ ] Use TanStack Table with virtualization support
- [ ] Advanced Filtering UI <!-- id: 4.1.3 -->
    - [ ] Faceted filters for roles, colleges, and statuses

## Dev Notes

- **Performance**: Virtualize rows if list exceeds 100 items. NFR1 mandates < 1.5s load time.
- **RBAC**: HR Execs only see candidates from their assigned domain.

### References

- [UX: HR Dashboard Strategy](file:///c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md#hr-command-center)

## Dev Agent Record

### Agent Model Used

### Debug Log References

### Completion Notes List

### File List
