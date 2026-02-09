# 🛡️ Antigravity Configuration: The Strict Guardian

Welcome to the **Strict Guardian** workspace configuration. This document explains the conventions, workflows, and setup required to maintain our high engineering standards.

## 🧠 Philosophy
We optimize for **Long-term Maintainability** and **Reliability**.
- We prefer **Types** and **Static Analysis** over runtime debugging.
- We prefer **Integration Tests** (Kent C. Dodds style) over implementation-detail unit tests.
- We do not take shortcuts.

## 📋 Core Rules
See [Rules](./rules.md) for the detailed specification.
1.  **Strict Typing**: No `any`. Strict Mode enabled for TS and Python.
2.  **Linting**: Use the provided "Golden Master" configs.
3.  **Process**: Always use Workflows to create or update projects.

## ⚙️ Workflows
Do not run manual setup commands. Use the Agent Workflows to ensure compliance.

### 🆕 `new-project`
> **Usage**: "Create a new React app called 'dashboard'"
Scaffolds a new project with our **Golden Master** configurations copied into place.
- **Includes**: TypeScript/Python setup, ESLint, Prettier, Vitest/Pytest.
- **Why**: Ensures every project starts with the correct strict settings.

### 🔧 `maintain-project`
> **Usage**: "Check if this project is compliant" or "Fix the linting config"
Audits an existing project and updates its config files to match the current Golden Masters.
- **Use when**: You inherit legacy code or when our Global Rules change.

## 📂 Directory Structure
```
.agent/
├── configs/           # The "Golden Master" configuration files
│   ├── tsconfig.base.json
│   ├── .eslintrc.base.js
│   └── .prettierrc.json
├── rules.md           # The Law. Agent conventions.
├── workflows/         # Automations (new-project, maintain-project)
└── README.md          # This file.
```

## 🚀 Setup for New Developers
To adopt this configuration on a new machine:
1.  Copy the `.agent` folder to the root of your workspace (e.g., `~/Developer/.agent`).
2.  Ensure you have the core tools installed:
    - Node.js (via `fnm` or `nvm`)
    - Python (via `pyenv`)
3.  Start a conversation with Antigravity and say: "I have initialized the .agent folder. Please read the README."
