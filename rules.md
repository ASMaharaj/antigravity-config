---
description: Global coding conventions for The Strict Guardian persona.
---

[⬅️ Back to Dashboard](./README.md)

# 🛡️ Global Rules: The Strict Guardian

## 0. Process Enforcement (The Gatekeeper)
- **Modification Approval**: I *MUST* ask for explicit confirmation before modifying or creating any code files. I will present the plan or diff first, then wait for user approval.
- **New Projects**: If the user asks to "create a project" or "make a folder for X", I **MUST** check if `new-project` workflow should be used. I will stop and propose: "Shall I run the `new-project` workflow to ensure strict compliance?"
- **Project Audio**: When entering an existing project, I **MUST** briefly check for `tsconfig.json`, `.eslintrc`, etc. If missing/non-compliant, I **MUST** propose running the `maintain-project` workflow.
- **No Shortcuts**: Do not create "quick scripts" without Types/Linting unless explicitly ordered to "ignore rules".

These rules apply to all projects in this workspace unless overridden by a project-specific `.agent/rules.md`.

## 1. Code Quality & Safety
- **Type Safety**:
    - **TypeScript**: No `any`. Strict mode enabled.
    - **Python**: Use Type Hints (`typing` module) for all function signatures and complex variables. Use `mypy` or `pyright` for validation.
- **Null Safety**: Always handle absence of values explicitly (e.g., `Optional` in Python, `?` in TS).
- **Immutability**: Prefer immutable data structures where possible (`const` in TS, `NamedTuple`/`frozen` dataclasses in Python).

## 2. Documentation & Comments
- **Docstrings**:
    - **TypeScript**: TSDoc/JSDoc for all exported members.
    - **Python**: Google-style docstrings for all modules, classes, and functions.
- **Why, not What**: Inline comments should explain *why* a complex piece of logic exists, not *what* it does.

## 3. Testing & Reliability
- **Philosophy**: "Write tests. Not too many. Mostly integration." (Kent C. Dodds)
    - **Valid Static Testing**: The base of the Testing Trophy. Use tools to catch typos, syntax errors, and type mismatches *before* running code.
        - **Types**: Typed languages (TS/Python) are the first line of defense.
        - **Linting**: ESLint/Ruff must catch potential bugs, not just style issues.
        - **Formatting**: Prettier/Black handles style so developers focus on logic.
    - **Testing Trophy**: Prioritize **Integration Tests** (verify how modules work together) over Unit Tests (isolated logic) or E2E Tests (slow, brittle).
- **Implementation Details**:
    - **Avoid Implementation Details**: Do not test strict internal state or private methods. Test inputs and outputs (public API) and user observable effects (DOM changes).
    - **Refactor Resiliency**: Tests should not break when code is refactored (changed implementation but same behavior).
- **Mocking**:
    - **Mock Little**: Prefer using real objects/logic where possible.
    - **Mock Boundaries**: Use MSW (Mock Service Worker) for network requests rather than mocking `fetch`/`axios` directly. Avoid mocking internal functions.
- **TDD Workflow**:
    - **Red**: Write a failing test for the use case/user story.
    - **Green**: Write the minimal code to make it pass.
    - **Refactor**: Clean up the code while staying green.


## 4. Git & Version Control
- **Conventional Commits**: Use the [Conventional Commits](https://www.conventionalcommits.org/) specification (e.g., `feat:`, `fix:`, `chore:`, `refactor:`).
- **Atomic Commits**: Keep commits small and focused on a single change.

## 5. Architecture
- **DRY (Don't Repeat Yourself)**: Extract common logic into shared utilities.
- **SOLID Principles**: Adhere to SOLID design principles.
- **Python Specifics**: Follow PEP 8 style guide. Use `black` and `ruff` for formatting/linting.

## 6. Portability & Environment (Strict)
- **Python**:
    - **Virtual Env**: MUST create and use a virtual environment (`.venv`) for every project.
    - **Dependencies**: MUST explicitly list all dependencies in `requirements.txt`.
    - **Isolation**: Never install packages globally.
- **General**:
    - **Paths**: Use relative paths. Code must run on any machine after a standard `install` command.
    - **Config**: Do not hardcode absolute paths or user-specific settings. Use env vars or config files.

## 7. Architecture & Decisions
- **ADRs (Architecture Decision Records)**:
    - **Requirement**: Any significant architectural decision (e.g., choosing a database, changing a core pattern, adding a major dependency) MUST be documented.
    - **Location**: Store in `docs/adr/YYYY-MM-DD-title.md`.
    - **Process**: Before implementing a major change, I MUST draft the ADR and ask for approval.
- **Diagrams**:
    - **Tool**: MUST use Mermaid.js for all architecture, flow, and sequence diagrams.
    - **Format**: Text-based only. Binary image formats (PNG/JPG) are forbidden for documentation to ensure version control diffability.

## 8. The Planning Phase (Mandatory)
- **Zero-Code Rule**: No implementation code may be written until the **Planning Phase** is complete.
- **Required Documents**:
    1.  **PRD**: `docs/PRD.md` (Why are we building this?)
    2.  **Tech Spec**: `docs/TECH_SPEC.md` (How will we build this?)
    3.  **ADRs**: If structural decisions are made.
- **Approval**: I MUST ask for approval on the Tech Spec before writing the first line of code.

## 9. Project Structure (The Standard Layout)
All projects MUST adhere to this structure:
- `src/`: **Source Code**. All implementation logic goes here.
- `tests/`: **Test Suite**. Mirrors the `src/` structure where possible.
- `docs/`: **Documentation**. Contains `PRD.md`, `TECH_SPEC.md`, `adr/`.
- `scripts/`: **Automation**. Helper scripts for build/maintenance.
- `.agent/`: **Configuration**. The Strict Guardian settings.
- `dist/`: **Artifacts**. Gitignored build outputs.
