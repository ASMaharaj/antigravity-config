[⬅️ Back to Dashboard](../README.md)

# 🔄 Engineering Lifecycle (SDLC)

This document describes **The Application** of our rules. It answers: "How do we actually build software here?"

It connects the **Human Process** (Ideas, Decisions) with the **Agent Configuration** (ADRs, Tests, Git).

---

## 1. 💡 Phase 1: Planning & Design
**Goal**: Know *what* to build (PRD) and *how* to build it (Tech Spec).
**Agent Support**: `PRD.md`, `TECH_SPEC.md` templates.

1.  **Idea / Requirement**: A problem is identified.
2.  **Draft PRD**:
    *   Fill out `docs/PRD.md`. Define the problem and success metrics.
3.  **Draft Tech Spec**:
    *   Fill out `docs/TECH_SPEC.md`. Design the Architecture, Data Model, and Implementation Plan.
    *   Use **Mermaid.js** for diagrams.
4.  **Architectural Check**:
    *   If a major decision is made in the Tech Spec, extract it into an **ADR** in `docs/adr/`.
5.  **Approval**: Review the Tech Spec. Only proceed to Phase 2/3 once approved.

## 2. 🚦 Phase 2: Setup (New Projects Only)
**Goal**: Start with a perfect configuration.
**Agent Support**: `new-project` workflow.

1.  **Trigger**: Ask Antigravity "Create a new [TS/Python] project".
2.  **Verify**: Ensure the `.agent` folder is cloned (Ejected).
3.  **Result**: You have a strict environment ready for TDD.

## 3. 💻 Phase 3: Development Loop
**Goal**: Build correctness.
**Agent Support**: Strict Rules (Gatekeeper), Vitest/Pytest.

The **Strict Guardian** mandates this loop:
1.  **🔴 Red**: Write a failing test for the specific feature.
    *   *Agent Rule*: "I will not write implementation code until I see a test."
2.  **🟢 Green**: Write just enough code to pass the test.
    *   *Agent Rule*: "I will confirm with you before modifying files."
3.  **🔵 Refactor**: Improve the code structure.
    *   **Static Analysis**: ESLint/Ruff/Mypy runs automatically.

## 4. 📦 Phase 4: Delivery
**Goal**: Save history cleanly.
**Agent Support**: `git-master` skill.

1.  **Stage**: `git add .`
2.  **Commit**: Ask Antigravity "Commit these changes".
    *   It analyzes the diff.
    *   It generates a **Conventional Commit** (e.g., `feat(auth): add login endpoint`).
    *   It enforces **Atomic Commits**.

---

## 🔗 Summary of Tools
| Phase | Human Action | Agent Tool/Rule |
| :--- | :--- | :--- |
| **Design** | Write ADR / Draw Flow | `docs/adr/*.md`, Mermaid.js |
| **Setup** | "Create project" | `new-project` workflow (Eject) |
| **Code** | Write Tests | `rules.md` (TDD, Types) |
| **Commit** | "Commit changes" | `git-master` skill |
