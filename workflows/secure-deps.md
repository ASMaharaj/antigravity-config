---
description: Audit project dependencies for known vulnerabilities.
---

This workflow inspects the dependency tree for security issues.

1.  **Detector**:
    *   Identify usage: `package.json` (Node) or `requirements.txt`/`pyproject.toml` (Python).

2.  **Audit Execution**:
    *   **If Node**: Run `npm audit`.
    *   **If Python**: Run `pip-audit` (requires installation) or check known vulnerabilities against a DB.

3.  **Analysis**:
    *   If **0 vulnerabilities**: Pass.
    *   If **Vulnerabilities found**:
        *   Display Severity (Critical, High, Moderate).
        *   Ask: "**Attempt Auto-Fix?**"
    *   **If Fix**: Run `npm audit fix` or upgrade python package.

4.  **Report**:
    *   Output a summary: "Security Audit Passed" or "Actions Required".
