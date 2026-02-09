---
description: Set up Husky (TS) or Pre-Commit (Python) git hooks.
---

This workflow installs and configures pre-commit hooks to enforce code quality.

1.  **Detection**:
    *   Detect language (TS or Python).

2.  **TypeScript Setup**:
    *   Run `npm install --save-dev husky lint-staged`.
    *   Run `npx husky init`.
    *   Create `.lintstagedrc`:
        ```json
        {
          "*.{ts,tsx}": [
            "eslint --fix",
            "prettier --write"
          ],
          "*.{json,md}": [
            "prettier --write"
          ]
        }
        ```
    *   Add hook to `.husky/pre-commit`: `npx lint-staged`.

3.  **Python Setup**:
    *   Run `pip install pre-commit`.
    *   Create `.pre-commit-config.yaml`:
        ```yaml
        repos:
          - repo: https://github.com/pre-commit/pre-commit-hooks
            rev: v4.4.0
            hooks:
              - id: trailing-whitespace
              - id: end-of-file-fixer
          - repo: https://github.com/psf/black
            rev: 23.3.0
            hooks:
              - id: black
          - repo: https://github.com/charliermarsh/ruff-pre-commit
            rev: v0.0.261
            hooks:
              - id: ruff
        ```
    *   Run `pre-commit install`.
