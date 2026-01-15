---
stepsCompleted: [step-01-validate-prerequisites, step-02-design-epics]
inputDocuments: 
  - "c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/prd.md"
  - "c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/architecture.md"
  - "c:/Users/Admin/Documents/intern-management-system/_bmad-output/planning-artifacts/ux-design-specification.md"
---

# Intern Management System - Epic Breakdown

## Overview

This document provides the complete epic and story breakdown for Intern Management System, decomposing the requirements from the PRD, UX Design if it exists, and Architecture requirements into implementable stories.

## Requirements Inventory

### Functional Requirements

FR1: Users can authenticate via email and password with session management.
FR2: The system can enforce Role-Based Access Control (RBAC) levels (HR Admin, HR Exec, College Coordinator, Student).
FR3: HR Admins can manage internal and external user accounts.
FR4: HR Admins can create and manage College/University partner profiles.
FR5: College Coordinators can modify their own institutional contact information.
FR6: The system can track and display student enrollment statistics per college.
FR7: College Coordinators can upload candidate shortlists via CSV.
FR8: The system can perform structural and data-type validation on CSV uploads.
FR9: The system can detect and flag duplicate candidate entries across batches.
FR10: College Coordinators can view and correct errors in rejected CSV uploads.
FR11: HR Executives can move candidates through a fixed 4-step pipeline (Shortlisted → Interviewed → Docs Submitted → Offer Released).
FR12: HR Executives can perform batch status transitions for groups of selected candidates.
FR13: The system can record an immutable timestamped audit trail for every status transition.
FR14: Students can securely upload PDF/Image files (Transcripts, IDs) via a dedicated portal.
FR15: HR Executives can view, approve, or reject submitted documents.
FR16: The system can allow HR to provide specific reasons for document rejection (e.g., "Blurry scan").
FR17: The system can track the "Compliance Status" of each candidate based on document approval.
FR18: HR Executives can track the state of individual offers (Ready, Sent, Accepted).
FR19: HR Admins can export "Ready for Offer" candidate lists to CSV for external processing.
FR20: The system can lock candidate records once an offer is marked as "Accepted."
FR21: The system can trigger automated email alerts to students when documents are rejected.
FR22: The system can notify College Coordinators when their batch processing is complete.
FR23: The system can send automated invitations to newly uploaded students.

### NonFunctional Requirements

NFR1: Main dashboard loads and filtering actions complete within < 1.5 seconds for batches up to 500 candidates.
NFR2: Validation and feedback for a 100-row CSV must be provided within < 10 seconds.
NFR3: The system must support at least 50 concurrent HR users and 200 concurrent students without performance degradation.
NFR4: All data must be encrypted in transit (TLS 1.2+) and at rest (AES-256).
NFR5: Student PII must be logically isolated by College/Tenant to prevent cross-account data leakage.
NFR6: Audit logs for status changes must be immutable and retained for 3 years.
NFR7: The system must maintain 99.9% uptime during active recruitment peak months.
NFR8: Automated daily backups with a Recovery Point Objective (RPO) of < 4 hours.
NFR9: Graceful recovery from database connection timeouts with user-friendly error messaging.
NFR10: A first-time College Coordinator must be able to complete their first CSV upload without manual training.
NFR11: The student portal must conform to WCAG 2.1 Level AA standards.

### Additional Requirements

- **Backend Architecture**: Spring Boot 4.x / Java 21 with Spring Security (JWT) and Flyway migrations.
- **Frontend Architecture**: React 19.x / Vite / TS with Shadcn UI + Tailwind and TanStack Query/Table.
- **Multi-Tenancy**: Schema-per-tenant isolation for maximum PII security.
- **Deployment**: Local-first with Docker Compose.
- **UX - Verification Split-View**: Side-by-side review of candidate data and transcripts for HR.
- **UX - Inline CSV Error Editor**: Spreadsheet-style error correction for Coordinators.
- **UX - Mobile-First Student Portal**: Focused on document submission and status tracking.
- **Compliance**: AES-256 encryption at rest for PII and transcripts.
- **Starter Template**: Architecture specifies Spring Boot + React (Vite) as the foundation.

### FR Coverage Map

FR1: Epic 1 - Identity & Multi-Tenant Foundation
FR2: Epic 1 - Identity & Multi-Tenant Foundation
FR3: Epic 1 - Identity & Multi-Tenant Foundation
FR4: Epic 1 - Identity & Multi-Tenant Foundation
FR5: Epic 1 - Identity & Multi-Tenant Foundation
FR6: Epic 2 - Coordinator Command: Batch Intake & Validation
FR7: Epic 2 - Coordinator Command: Batch Intake & Validation
FR8: Epic 2 - Coordinator Command: Batch Intake & Validation
FR9: Epic 2 - Coordinator Command: Batch Intake & Validation
FR10: Epic 2 - Coordinator Command: Batch Intake & Validation
FR11: Epic 4 - HR Accelerator: Funnel Management & Triage
FR12: Epic 4 - HR Accelerator: Funnel Management & Triage
FR13: Epic 4 - HR Accelerator: Funnel Management & Triage
FR14: Epic 3 - Student Portal: Document Compliance Hub
FR15: Epic 4 - HR Accelerator: Funnel Management & Triage
FR16: Epic 4 - HR Accelerator: Funnel Management & Triage
FR17: Epic 4 - HR Accelerator: Funnel Management & Triage
FR18: Epic 5 - Final Selection & Offer Management
FR19: Epic 5 - Final Selection & Offer Management
FR20: Epic 5 - Final Selection & Offer Management
FR21: Epic 4 / 6 - Automated Student Alerts
FR22: Epic 2 / 6 - Coordinator Completion Alerts
FR23: Epic 3 / 6 - Student Invitation System

## Epic List

### Epic 1: Core Identity & Multi-Tenant Foundation
Establish the secure, multi-tenant baseline for all users. Admin can onboard colleges, and all users can log in securely to their specific schemas.
**FRs covered:** FR1, FR2, FR3, FR4, FR5.

### Epic 2: Coordinator Command: Batch Intake & Validation
Empower College Coordinators to submit their candidates. Mr. Sharma can upload CSVs and fix data errors inline.

#### Story 2.1: CSV Structural Parser & Multi-Dialect Support

As a College Coordinator,
I want to drag and drop CSV shortlists,
So that the system handles various spreadsheet formats (Excel CSV, Google Sheets CSV) automatically.

**Acceptance Criteria:**

**Given** I am on the Coordinator Dashboard
**When** I drag and drop a `.csv` file into the upload zone
**Then** the system parses the file structure and displays the detected columns
**And** it correctly identifies 'Name', 'Email', and 'GPA' headers regardless of case or common variations
**And** it stores the raw data in a temporary staging area for validation.

#### Story 2.2: Live CSV Data Validation Engine

As a College Coordinator,
I want instant feedback on duplicate names, missing emails, or invalid GPA formats during the upload,
So that I catch errors before they reach HR.

**Acceptance Criteria:**

**Given** data has been uploaded to the staging area
**When** the validation engine runs
**Then** it flags rows with empty 'Email' or 'Name' fields
**And** it identifies duplicate emails within the current batch or against existing student records
**And** it highlights GPA values outside the 0.0-10.0 or 0.0-4.0 range
**And** a summary of "Valid vs Rejected" rows is displayed.

#### Story 2.3: Inline "Spreadsheet" Error Editor

As a College Coordinator,
I want a grid view to fix specific rejected rows directly in the browser,
So that I don't have to keep re-uploading the whole file.

**Acceptance Criteria:**

**Given** a batch has rows with validation errors
**When** I open the 'Error Editor'
**Then** a tabular grid shows ONLY the rows with errors, highlighting specific invalid cells in red
**And** I can edit the cell values directly in the grid
**And** rows are re-validated instantly after editing
**And** fixed rows move from the 'Error' list to the 'Ready' list.

#### Story 2.4: Batch Submission Tracking & Status Alerts

As a College Coordinator,
I want to see a status log of all my previous uploads and get an automated "Processing Complete" notification,
So that I know exactly when HR has received my batch.

**Acceptance Criteria:**

**Given** I have successfully submitted a batch of candidates
**When** I navigate to the 'Submission History' tab
**Then** I see the list of my submissions with 'Batch ID', 'Date', 'Success Count', and 'Current Status' (Processing/Received)
**And** I receive a notification (in-app or email) once the background processing for a large batch is complete.

### Epic 3: Student Portal: Document Compliance Hub
Provide students a mobile-first experience to submit their credentials. Siddharth can securely upload transcripts and IDs from his phone.

#### Story 3.1: Mobile-First Student Login & Invitation Retrieval

As a Student,
I want to login to a mobile-friendly portal using the credentials sent to my email,
So that I can start my document submission process.

**Acceptance Criteria:**

**Given** a student has been invited to the system
**When** I visit the login URL on a mobile browser and enter my temporary credentials
**Then** the portal displays a mobile-optimized welcome screen
**And** I am prompted to set a permanent password
**And** I am shown a checklist of required documents (e.g., Semester 6 Transcript, National ID).

#### Story 3.2: Multi-Document Secure Upload Hub

As a Student,
I want to securely upload photos or PDFs of my transcripts and IDs,
So that Wissen HR can verify my eligibility.

**Acceptance Criteria:**

**Given** I am logged into the student portal
**When** I tap on a document requirement (e.g., 'National ID')
**Then** the system opens the mobile camera or file picker
**And** I can upload a clear image or PDF file
**And** the file is encrypted at rest (AES-256)
**And** I receive a "Upload Successful" confirmation.

#### Story 3.3: Real-Time Verification Status Tracking

As a Student,
I want to see the real-time approval status of each document,
So that I know if I need to re-upload anything.

**Acceptance Criteria:**

**Given** I have uploaded documents for review
**When** I log into the portal
**Then** each document shows a status badge: 'Pending', 'Approved', or 'Rejected'
**And** if 'Rejected', the rejection reason (e.g., "Blurry scan") is displayed prominently
**And** I have a direct option to 'Re-upload' for rejected items.

### Epic 4: HR Accelerator: Funnel Management & Triage
The core "Command Center" where HR manages the recruitment pipeline. Ananya can batch-process candidates through the 4-step tunnel using the Split-View triage.

#### Story 4.1: Unified HR Command Center (Candidate List & Filters)

As an HR Executive,
I want a high-density dashboard with powerful filters for college, status, and compliance,
So that I can identify priority candidates in seconds.

**Acceptance Criteria:**

**Given** I am logged in as an HR Executive
**When** I access the 'Main Dashboard'
**Then** I see a high-density table of all candidates across all colleges I have access to
**And** I can filter by 'College Name', 'Current Funnel Stage', and 'Compliance Status'
**And** the table loads and filters in < 1.5 seconds even for 500+ records
**And** I can search for a candidate by name or email.

#### Story 4.2: High-Speed Verification Split-View

As an HR Executive,
I want a side-by-side view to inspect student data and transcript PDFs without switching tabs,
So that I can verify records at light speed.

**Acceptance Criteria:**

**Given** I am in the candidate list
**When** I click on a candidate's 'Verify' action
**Then** a split-view pane opens showing student details on the left and the scrollable transcript PDF on the right
**And** I can navigate to the next/previous candidate using keyboard shortcuts (`j`/`k`)
**And** I can mark the document as 'Approved' or 'Rejected' without closing the preview.

#### Story 4.3: Batch Status Progression Engine

As an HR Executive,
I want to select multiple candidates and move them to the next stage (e.g., "Interviewed" → "Docs Submitted") in one click,
So that I can process hundreds of candidates daily.

**Acceptance Criteria:**

**Given** I have selected multiple candidates in the dashboard
**When** I click the 'Batch Advance' button and select a target stage
**Then** the system validates that the transition is allowed (must follow the Shortlisted → Interviewed → Docs Submitted → Offer Released sequence)
**And** all selected records are updated with a single timestamped transaction
**And** a success notification shows the count of updated records.

#### Story 4.4: Compliance Triage & Document Rejection Logic

As an HR Executive,
I want to approve/reject specific documents and provide canned or custom reasons (e.g., "Blurry scan"),
So that students know exactly how to fix their submission.

**Acceptance Criteria:**

**Given** I am reviewing a student's document in the Split-View
**When** I select 'Reject'
**Then** a menu appears with common rejection reasons (Blurry, Incorrect ID, Missing Signature)
**And** I can type a custom note if needed
**And** saving the rejection instantly updates the student's compliance status to 'Action Required'
**And** an immutable audit log entry records the rejection type and reviewer.

### Epic 5: Final Selection & Offer Management
Close the loop by moving candidates to the "Offer" stage. HR can track offer states and export "Ready for Offer" lists.

#### Story 5.1: "Ready for Offer" Selection & Validation

As an HR Executive,
I want the system to automatically flag candidates who have cleared both the interview and the doc compliance check,
So that I don't accidentally release an offer to an ineligible student.

**Acceptance Criteria:**

**Given** I am on the candidate dashboard
**When** a candidate reaches the 'Docs Submitted' stage AND all required documents are 'Approved'
**Then** the candidate is automatically flagged as 'Ready for Offer'
**And** I can use a specific 'Ready for Offer' quick-filter to see this list
**And** the system prevents moving a candidate to 'Offer Released' if compliance status is not 'Approved'.

#### Story 5.2: Offer State Transition Engine (Sent/Accepted)

As an HR Executive,
I want to track whether an offer has been sent or accepted,
So that I have an accurate headcount for the upcoming intern batch.

**Acceptance Criteria:**

**Given** a candidate is in the 'Ready for Offer' state
**When** I mark the offer as 'Sent'
**Then** the candidate's funnel status moves to 'Offer Released'
**And** I can subsequently update the state to 'Accepted' or 'Declined'
**And** when marked as 'Accepted', the candidate's record is locked from further status changes.

#### Story 5.3: Bulk Offer Export (CSV/Excel)

As an HR Admin,
I want to export the "Ready for Offer" list to a CSV formatted for our internal payroll/onboarding system,
So that I can trigger the physical offer letters outside the system.

**Acceptance Criteria:**

**Given** I am an HR Admin
**When** I select 'Export Offer Data' from the dashboard
**Then** the system generates a CSV file containing all 'Ready for Offer' candidates
**And** the file includes all necessary PII (Full Name, College, Address, PAN/ID) and verification stamps
**And** the export action is logged for security auditing.

### Epic 6: Communications & Auditability
Ensuring transparency and compliance across the board. Comprehensive audit logs and system-wide automated notifications.

#### Story 6.1: Immutable System-Wide Audit Logger

As an HR Admin,
I want a centralized, append-only log of every status change and user action,
So that we are fully compliant with Wissen's 3-year audit policy.

**Acceptance Criteria:**

**Given** any state-changing action is performed in the system (e.g., Status Update, Document Rejection, User Creation)
**When** the transaction is committed
**Then** an entry is automatically created in the `audit_logs` table
**And** the entry includes 'Timestamp', 'User ID', 'Action Type', 'Subject ID', 'Previous State', and 'New State'
**And** the audit logs are read-only and cannot be modified or deleted via the application UI.

#### Story 6.2: Automated Email/SMS Notification Relay

As a Student / Coordinator,
I want to receive instant alerts when my compliance status changes or a new batch is processed,
So that I don't have to keep checking the portal.

**Acceptance Criteria:**

**Given** a student's document is 'Rejected' or 'Approved' by HR
**When** the status change is saved
**Then** the system triggers an automated email alert to the student's registered address
**And** if 'Rejected', the email includes the specific reason provided by HR
**And** a similar notification is sent to College Coordinators when their CSV batch processing finishes.

#### Story 6.3: Multi-Account Management & Security Audit

As an HR Admin,
I want to review all active users and their login timestamps,
So that I can ensure only authorized personnel have access to our student schemas.

**Acceptance Criteria:**

**Given** I am logged in as an HR Admin
**When** I access the 'Security/Audit' dashboard
**Then** I see a list of all system users across all roles
**And** I can see their 'Last Login' timestamp and 'Account Status' (Active/Locked)
**And** I have the ability to deactivate any account instantly, which terminates all active sessions for that user.

## Epic 1: Core Identity & Multi-Tenant Foundation

Establish the secure, multi-tenant baseline for all users. Admin can onboard colleges, and all users can log in securely to their specific schemas.

### Story 1.1: Project Scaffolding & Local Environment Setup

As a Developer,
I want to initialize the Spring Boot and React project structures with Docker Compose,
So that I have a consistent development environment for all agents.

**Acceptance Criteria:**

**Given** the project architecture is defined
**When** I run the scaffolding scripts
**Then** a monorepo structure is created with `backend` (Spring Boot 4) and `frontend` (React 19/Vite) folders
**And** a `docker-compose.yml` is provided for running PostgreSQL 18
**And** the project builds successfully with `mvn clean install` and `npm install`.

### Story 1.2: Multi-Tenant Schema & Partner Onboarding (Backend-Only)

As an HR Admin,
I want to create university partner profiles that initialize their own PostgreSQL schemas,
So that student data is logically isolated from the very beginning.

**Acceptance Criteria:**

**Given** I am an authenticated HR Admin
**When** I call the 'Create Partner' API with a university name and slug
**Then** a new record is created in the master `partners` table
**And** a dedicated PostgreSQL schema is created for this partner
**And** the action is recorded in the system-wide audit log.
*(Note: Domain tables like `candidates` are created in later epics when first used)*

### Story 1.3: Multi-Tenant JWT Authentication Service

As a system user,
I want to log in and receive a secure token that identifies my college/tenant,
So that I can only access data belonging to my university.

**Acceptance Criteria:**

**Given** a valid user exists in the `users` table associated with a specific partner
**When** I provide correct credentials to the `/api/v1/auth/login` endpoint
**Then** the system returns a JWT token
**And** the token contains a `tenant_id` or `schema_name` claim
**And** subsequent requests with this token automatically use the correct schema context
**And** I am blocked from accessing data in other partner schemas.

### Story 1.4: User Management API (RBAC)

As an HR Admin,
I want to manage internal (HR) and external (Coordinator) accounts,
So that the system enforces tiered access across roles.

**Acceptance Criteria:**

**Given** I am an authenticated HR Admin
**When** I create a new user account with a specific role (HR_ADMIN, HR_EXEC, COLLEGE_COORDINATOR)
**Then** the user is correctly mapped to the target role in the IAM database
**And** a 'COLLEGE_COORDINATOR' user must be associated with a valid partner ID
**And** the new user can only login to features permitted by their specific role.

### Story 1.5: Multi-Tenant User Profile Portal (Frontend)

As a College Coordinator,
I want to view and modify my institutional contact details on a secure dashboard,
So that my profile information stays up to date.

**Acceptance Criteria:**

**Given** I am logged in as a College Coordinator
**When** I navigate to the 'Partner Profile' section of the dashboard
**Then** I see the institutional data for ONLY my college
**And** I can update the 'Primary Contact', 'Phone', and 'Office Address' fields
**And** clicking 'Save' persists the changes with a success notification.
