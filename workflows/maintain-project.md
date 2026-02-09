---
description: Update project configuration to match Global Golden Masters
---

This workflow brings an existing project back into compliance with the Strict Guardian standards.

1.  **Analyze**:
    *   Check for existence of `tsconfig.json`, `.eslintrc*`, `.prettierrc*` (TS) or `pyproject.toml` (Python).
    *   Check `package.json` (TS) or `requirements.txt` (Python) for required devDependencies.

2.  **Confirm**:
    *   Show user what is missing or outdated.
    *   Ask: "Shall I overwrite configs with the latest Golden Masters?"

3.  **Update Configs**:
    *   **Applies to TypeScript**:
        *   **Copy** `.agent/configs/tsconfig.base.json` -> `tsconfig.json`.
        *   **Copy** `.agent/configs/.eslintrc.base.js` -> `.eslintrc.js`.
        *   **Copy** `.agent/configs/.prettierrc.json` -> `.prettierrc.json`.
    *   **Applies to Python**:
        *   **Copy** `.agent/configs/pyproject.base.toml` -> `pyproject.toml`.

4.  **Update Dependencies**:
    *   Run `npm install -D typescript eslint prettier vitest @typescript-eslint/eslint-plugin ...` (ensure versions match global standards).

5.  **Verify**:
    *   Run `npm run lint`.
    *   Run `npm run test` (if exists).
