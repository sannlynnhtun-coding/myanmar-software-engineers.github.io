# Feature Specification: Fix dependency PR blockers

**Feature Branch**: `fix-dependency-prs`

**Created**: 2026-11-20

**Status**: Ready for planning

**Input**: Fix actionable blockers in the upstream pull request list.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Review dependency upgrades (Priority: P1)

A maintainer can review the updates proposed by #294, #291, and #287 against current main while retaining the content migration.

**Why this priority**: These proposals have reported merge conflicts or a failed build.

**Independent Test**: Install dependencies from a clean checkout and run the same site build used for review.

**Acceptance Scenarios**:

1. **Given** current main, **when** the proposed updates are applied, **then** dependency installation succeeds and the site builds.
2. **Given** the built site, **when** a visitor opens an existing profile and a book listing, **then** both pages still show their existing content.

### Edge Cases

- If the old build log has expired, reproduce the failure against current main before assigning a cause.
- If the registry cannot supply a proposed version, record that blocker and continue verifying independent changes.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: Apply the dependency updates requested by #294, #291, and #287 on top of current upstream main.
- **FR-002**: Resolve compatibility errors that prevent the clean build.
- **FR-003**: Preserve existing profile and book content in the generated site.
- **FR-004**: Record verification results for each actionable blocker.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: All three requested upgrades can be evaluated from one clean checkout with zero dependency-install or build errors.
- **SC-002**: At least one existing profile and one book listing are present with content in the build output.

## Assumptions

- Scope covers the three open proposals with confirmed conflicts or a reported build failure.
- Maintainers handle required PR approvals. Verification uses current upstream main and a local repair branch.
