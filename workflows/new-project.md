---
description: Create a new project with Strict Guardian defaults (TS or Python)
---

This workflow sets up a new project with the strict standards defined in `.agent/rules.md`.

1.  **Ask User**:
    *   Project Name
    *   Language (TypeScript | Python)
    *   Type (CLI | Web App | Library)

2.  **Scaffold Project**:
    *   Create directory.
    *   Initialize git.
    *   **Install Antigravity Config** (Eject Mode):
        *   Run `git clone https://github.com/ASMHB/antigravity-config.git .agent`.
        *   Run `rm -rf .agent/.git` (Detach from global repo to make it standalone).
    *   **Initialize Docs**:
        *   Create `docs/adr`.
        *   Copy `.agent/templates/ADR.md` -> `docs/adr/0000-template.md`.
    *   Create `.gitignore` (ensure `.agent` is NOT ignored, so rules are committed).

3.  **Language Setup**:
    *   **If TypeScript**:
        *   Run `npm init -y`.
        *   Install `typescript`, `eslint`, `prettier`, `jest`/`vitest`.
        *   Create `tsconfig.json` with `"strict": true`.
        *   Create `.eslintrc` and `.prettierrc` with strict rules.
    *   **If Python**:
        *   Create virtual environment (`python3 -m venv .venv`).
        *   Create directory structure (`src`, `tests`).
        *   **Copy Config**: `.agent/configs/pyproject.base.toml` -> `pyproject.toml`.
        *   Create `requirements.txt` with:
            ```text
            mypy
            ruff
            black
            pytest
            ```
        *   Install dependencies: `source .venv/bin/activate && pip install -r requirements.txt`.

4.  **Initial Commit**:
    *   Commit with message "feat: Initial project setup with strict defaults".

5.  **Verify**:
    *   Run lint check.
    *   Run dummy test.
