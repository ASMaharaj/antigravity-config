---
description: Update project configuration to match Global Golden Masters
---

This workflow brings an existing project back into compliance with the Strict Guardian standards.

1.  **Analyze**:
    *   Check for existence of `tsconfig.json`, `.eslintrc*`, `.prettierrc*`.
    *   Check `package.json` for required devDependencies (`typescript`, `eslint`, `prettier`, `vitest`).

2.  **Confirm**:
    *   Show user what is missing or outdated.
    *   Ask: "Shall I overwrite configs with the latest Golden Masters?"

3.  **Update Configs**:
    *   **Copy** `.agent/configs/tsconfig.base.json` -> `tsconfig.json`.
    *   **Copy** `.agent/configs/.eslintrc.base.js` -> `.eslintrc.js`.
    *   **Copy** `.agent/configs/.prettierrc.json` -> `.prettierrc.json`.

4.  **Update Dependencies**:
    *   Run `npm install -D typescript eslint prettier vitest @typescript-eslint/eslint-plugin ...` (ensure versions match global standards).

5.  **Verify**:
    *   Run `npm run lint`.
    *   Run `npm run test` (if exists).
