<!--
Sync Impact Report
- Version change: 0.0.0 → 1.0.0
- Modified principles: new constitution established for ContosoDashboard (no prior principle set to rename)
- Added sections: Core Principles, Additional Constraints, Development Workflow, Governance
- Removed sections: none
- Templates requiring updates:
  - .specify/memory/constitution.md: ✅ updated
  - .specify/templates/plan-template.md: ✅ no change required; Constitution Check remains a generic gate
  - .specify/templates/spec-template.md: ✅ no change required; user-story and requirements structure remains appropriate
  - .specify/templates/tasks-template.md: ✅ no change required; task grouping by user story remains aligned
- Follow-up TODOs: none
-->

# ContosoDashboard Constitution

## Core Principles

### I. Training-First Scope and Transparency
This project is a training application and MUST remain clearly scoped as a local, educational sample.
All features, examples, and security patterns MUST distinguish between training behavior and production requirements.
Documentation MUST state that the app is offline-first, intentionally simplified, and not a production-ready system.

The purpose of the project is to teach secure design and development practices without implying that the provided implementation is suitable for live deployment. Any feature that introduces production-grade dependencies or operational assumptions MUST be documented as a migration path, not as an implemented production guarantee.

### II. Offline-First Architecture with Explicit Boundaries
The application MUST favor a local-first architecture: SQLite-backed persistence, in-process services, and simple runtime dependencies that work without cloud access.
System boundaries MUST be explicit: UI, business logic, services, and persistence concerns MUST not be mixed in ways that blur responsibility or hide authorization behavior.

For any external dependency or infrastructure abstraction, the project MUST use interfaces or adapters so the app can be swapped to production services later without rewriting the core feature logic. This keeps the training value high while preserving a clear migration path.

### III. Security by Default
Authentication and authorization MUST be enforced at every entry point, including page access, service-layer validation, and data access boundaries.
The project MUST protect against unauthorized data access, enforce user isolation, and validate that a caller is allowed to perform each action before mutating or reading business data.

Mock authentication is allowed only for training and MUST be documented as such. Security controls such as cookie settings, role checks, and authorization policies must align with the intent of the application and must not be treated as a substitute for production identity systems.

### IV. Test-First User Journeys and Evidence
Every meaningful feature or security change MUST be driven by a user story, acceptance criteria, and validation flow before implementation.
Core tasks MUST be broken down by independent user journeys so the application remains demonstrably testable and can be delivered as viable increments.

When a change affects access control, data isolation, or user flows, the relevant tests MUST verify the expected behavior under both success and denial conditions. A feature is not complete if its primary user path has not been validated.

### V. Simplicity, Clarity, and Maintainability
The codebase MUST prefer straightforward structures, readable responsibilities, and small, understandable components over hidden abstractions or clever shortcuts.
Implementation choices MUST be justified by the learning objective, the maintainability of the code, and the project's training scope rather than by speculative production complexity.

The team MUST keep documentation, naming, and architecture aligned with the current implementation so future work remains understandable and safely improvable.

## Additional Constraints

The ContosoDashboard project MUST follow these operating constraints:

- Build and run with .NET 8 and ASP.NET Core 8.0 using Blazor Server.
- Use SQLite with Entity Framework Core for the default local data store.
- Keep the app self-contained and offline-friendly for classroom and lab use.
- Treat mock authentication as a training mechanism only, not as a production-grade identity provider.
- Require explicit authorization checks for protected pages, data operations, and business services.
- Prefer service-layer validation and user-scoped access controls to prevent IDOR and cross-user leakage.
- Keep security and data-handling guidance visible in README and related training materials.

## Development Workflow

All work MUST follow the project workflow that keeps specification, design, and implementation aligned:

- Start from a user story or feature requirement with clear acceptance criteria.
- Capture scope in the specification and planning artifacts before implementation.
- Validate the design against this constitution before moving to large implementation efforts.
- Write or update tests for behavior and security-sensitive flows before finalizing changes.
- Keep implementation increments small and independently reviewable.
- Update documentation when architecture, security assumptions, or operational behavior change.

When the project introduces a new feature or modifies existing behavior, the change MUST be traceable to the associated requirement and must remain consistent with the training goals, offline-first design, and security model.

## Governance

This constitution governs the repository and supersedes ad hoc local practices that conflict with it. Any change to architecture, security model, operational assumptions, or project scope MUST be reflected in the constitution and in the relevant project documentation.

Amendments MUST be documented, versioned, and reviewed before they are treated as the current standard. When a principle or a rule changes materially, the project MUST update governance metadata, the reason for the change, and any affected requirements or workflow documentation.

Compliance review is expected for all substantive changes: reviewers MUST confirm the work remains aligned with the project's training purpose, offline-first constraints, and security expectations. Complexity must be justified; shortcuts that weaken protections or blur responsibilities are not allowed without explicit approval and documentation.

**Version**: 1.0.0 | **Ratified**: 2026-10-31 | **Last Amended**: 2026-10-31
