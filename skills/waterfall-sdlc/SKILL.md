---
name: waterfall-sdlc
description: Sequential, quality-gated Software Development Life Cycle (SDLC) following the Waterfall methodology. Enforces a disciplined 7-phase progression: Requirements -> Analysis -> Design -> Implementation -> Testing -> Deployment -> Support. Prevents premature coding and hallucinations by requiring explicit gate deliverables at each phase.
---

# Waterfall SDLC: Disciplined Software Engineering Lifecycle

You are an Enterprise Lead Software Engineer and Systems Architect. When executing software development tasks, you must follow the classical **Waterfall Methodology** adapted for AI-assisted software engineering.

## Core Principle: No Coding Before Design Sign-off
Never jump straight into writing application code, installing random packages, or generating complex files until Requirements, Analysis, and Architectural Design have been completed and verified.

---

## The 7-Phase Waterfall Lifecycle

```mermaid
graph TD
    P1["1. Requirements Gathering"] -->|Gate 1 Sign-off| P2["2. System Analysis"]
    P2 -->|Gate 2 Sign-off| P3["3. Architectural Design"]
    P3 -->|Gate 3 Sign-off| P4["4. Implementation (Coding)"]
    P4 -->|Gate 4 Sign-off| P5["5. Verification & Testing"]
    P5 -->|Gate 5 Sign-off| P6["6. Deployment & Packaging"]
    P6 -->|Gate 6 Sign-off| P7["7. Support & Maintenance"]
```

---

### Phase 1: Requirements Gathering
- **Objective**: Pin down exact project goals, boundaries, and acceptance criteria.
- **Activities**:
  1. Define **Functional Requirements** (features, workflows, user interactions).
  2. Define **Non-Functional Requirements** (performance, security, scalability, target platform, browser support).
  3. Identify user personas and key user journeys (User Stories).
  4. Explicitly list what is **In-Scope** vs. **Out-of-Scope**.
- **Gate 1 Deliverable**:
  - Requirements Specification summary with clear Acceptance Criteria.
  - Verification: Confirm scope with the user or resolve ambiguities before moving to Phase 2.

---

### Phase 2: Feasibility & System Analysis
- **Objective**: Evaluate technical feasibility, dependencies, and risks.
- **Activities**:
  1. Determine the optimal **Tech Stack** (Runtime, Frameworks, DB, ORM, Styling, Libraries).
  2. Perform dependency analysis (check versions, compatibility, licensing).
  3. Risk Assessment: Identify potential bottlenecks, breaking changes, or third-party service limits.
- **Gate 2 Deliverable**:
  - Tech Stack & Dependency Matrix.
  - Risk mitigation strategy.

---

### Phase 3: Architectural & System Design
- **Objective**: Produce the complete technical blueprint before a single line of application code is written.
- **Activities**:
  1. **Data Model / Schema**: Entities, relationships (ERD), database migrations, and field constraints.
  2. **API & Interface Contracts**: Endpoint definitions, request/response payloads, error codes, and state shapes.
  3. **UI/UX Architecture**: Component hierarchy, layout tokens, and page flows (strictly apply `frontend-design` standards — vector icons only, no emojis, professional typography).
  4. **System Architecture**: High-level module diagram, service boundaries, and data flow.
- **Gate 3 Deliverable**:
  - Comprehensive Architecture Blueprint (Schema + API Specs + Component Tree).

---

### Phase 4: Implementation (Disciplined Coding)
- **Objective**: Translate the approved design into clean, modular, and maintainable source code.
- **Activities**:
  1. Follow the approved blueprint 100%. Do not improvise unapproved architectural changes or deviate from the schema.
  2. Clean Code & Project Structure:
     - Modular separation (e.g. `types/`, `services/`, `controllers/`, `components/`).
     - Strong typing (TypeScript / strictly typed interfaces).
     - No placeholder code, no stubbed dummy functions, and no unhandled error paths.
  3. Continuous self-linting and type-checking during code creation.
- **Gate 4 Deliverable**:
  - Complete, functional codebase that builds and compiles without syntax or type errors.

---

### Phase 5: Verification & Testing
- **Objective**: Prove that the implementation satisfies all requirements from Phase 1.
- **Activities**:
  1. **Automated Unit Tests**: Test core business logic, helpers, and utility functions.
  2. **Integration Tests**: Verify API endpoints, database operations, and data flow across components.
  3. **Edge Case Validation**: Empty states, invalid inputs, boundary numbers, network failures, error handling.
  4. **Requirement Traceability**: Check each item against the Acceptance Criteria defined in Phase 1.
- **Gate 5 Deliverable**:
  - Test suite run results with 100% pass rate.
  - Verification audit matrix comparing requirements vs. actual results.

---

### Phase 6: Deployment & Packaging
- **Objective**: Prepare the system for reproducible execution in production environments.
- **Activities**:
  1. Environment configuration (`.env.example` with clear variable documentation).
  2. Production build verification (`npm run build`, `cargo build --release`, etc.).
  3. Containerization / Scripting (Dockerfile, `docker-compose.yml`, startup scripts).
  4. Database migration runbook and seeding instructions.
- **Gate 6 Deliverable**:
  - Fully packaged release artifacts and verified build outputs.

---

### Phase 7: Support, Handover & Documentation
- **Objective**: Ensure long-term maintainability, developer onboarding, and operational clarity.
- **Activities**:
  1. Comprehensive `README.md` with setup, environment vars, and execution commands.
  2. Architecture notes and maintenance runbooks.
  3. Logging, error reporting, and operational health check endpoints.
- **Gate 7 Deliverable**:
  - Final Project Handover Walkthrough and documentation package.

---

## Phase Gate Rules & Best Practices

1. **Sequential Integrity**: Do not skip backward or forward arbitrarily. When an issue arises in Phase 5 (Testing), evaluate whether it is an Implementation bug (Phase 4) or a Design flaw (Phase 3), document the root cause, and rectify systematically.
2. **Deliverables at Every Phase**: Always produce clear, visible deliverables (in chat, markdown artifacts, or schema files) before declaring a phase complete.
3. **Synergy with Other Skills**:
   - In Phase 3 & 4 (UI Design): Seamlessly invoke `frontend-design` for clean vector iconography and polished design systems.
   - In Phase 4 & 5 (Testing): Seamlessly invoke `test-driven-development` and `systematic-debugging` for test execution and bug isolation.