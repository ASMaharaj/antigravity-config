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

## 🚦 Process: Starting a New Project
To start a new project in this workspace, follow these exact steps:

1.  **Open Antigravity**: Start a new chat.
2.  **Trigger the Workflow**: Type a command like:
    > "Create a new TypeScript CLI project called 'my-tool'"
    > "Scaffold a Python library named 'data-processor'"
3.  **Provide Details**: If you didn't specify, Antigravity will ask for:
    - **Name**: (e.g., `utils-lib`)
    - **Language**: (`TypeScript` or `Python`)
    - **Type**: (`CLI`, `Web App`, `Library`)
4.  **Verification**: Antigravity will automatically:
    - Create the folder.
    - Initialize Git.
    - **Eject Configuration**: Installs a standalone copy of `.agent` (Rules, Workflows, Skills) into the project.
    - Copy the "Golden Master" configs (`tsconfig.base.json`, etc.).
    - Install `strict` dependencies (`eslint`, `prettier`, `vitest`/`pytest`).
    - run a dummy test to prove the setup works.
5.  **Result**: You are ready to code immediately with full type safety and linting enabled.

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

## 🚀 Setup for New Developers / New Machines
**Crucial**: Antigravity looks for `.agent` in the **root of your open workspace**.
To activate the "Strict Guardian", you must open your `~/Developer` folder (or whereever you cloned this), not just a sub-project.

1.  **Open Workspace**: Open `~/Developer` in Antigravity.
2.  **Install Config**: Run this command to fetch our Global Rules:
    ```bash
    git clone https://github.com/ASMHB/antigravity-config.git .agent
    ```
    *(Ensure `.agent` is in the .gitignore of your Developer folder if it's a repo, or just ignore it globally)*.
3.  **Verify**: Ask Antigravity "What are the global rules?". It should reply with "Strict Guardian".
