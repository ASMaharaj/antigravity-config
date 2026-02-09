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
    *   Create `.gitignore` (ensure `.agent` is NOT ignored, so rules are committed).

3.  **Language Setup**:
    *   **If TypeScript**:
        *   Run `npm init -y`.
        *   Install `typescript`, `eslint`, `prettier`, `jest`/`vitest`.
        *   Create `tsconfig.json` with `"strict": true`.
        *   Create `.eslintrc` and `.prettierrc` with strict rules.
    *   **If Python**:
        *   Create virtual environment (`python -m venv .venv`).
        *   Create `requirements.txt` / `pyproject.toml`.
        *   Install `mypy`, `ruff`, `pytest`, `black`.
        *   Create `codestyle` config files.

4.  **Initial Commit**:
    *   Commit with message "feat: Initial project setup with strict defaults".

5.  **Verify**:
    *   Run lint check.
    *   Run dummy test.
