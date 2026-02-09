[⬅️ Back to Dashboard](../README.md)

# 🚀 Project Setup Guide

This document outlines the two approved methods for starting a new project with the **Strict Guardian** configuration.

---

## Method 1: The "Command Center" (Recommended)
**Best for:** Starting a new project from scratch within your main workspace.

**Prerequisite:** You must have the entire `~/Developer` folder (or your main workspace root) open in Antigravity.

1.  **Open Antigravity**: Ensure you are in the root of your workspace (`~/Developer`).
2.  **Command**: Ask Antigravity to create the project.
    > "Create a new TypeScript CLI project called 'my-new-tool'"
    > "Scaffold a Python library named 'data-processor'"
3.  **Automation**:
    *   Antigravity runs the `new-project` workflow.
    *   It creates the folder `~/Developer/my-new-tool`.
    *   It **clones** the latest `antigravity-config` into `my-new-tool/.agent`.
    *   It initializes Git, installs strict dependencies, and **sets up Git Hooks**.
4.  **Result**: A fully configured, standalone project. You can now open a new Antigravity window for `~/Developer/my-new-tool`.

---

## Method 2: Manual Setup (Standalone)
**Best for:** When you cannot open the main workspace, or for setting up on a different machine/location.

**Prerequisite:** Terminal access and Git installed.

1.  **Create Directory**:
    ```bash
    mkdir my-new-project
    cd my-new-project
    git init
    ```

2.  **Install Configuration (The "Eject" Step)**:
    Clone the `antigravity-config` repo into a `.agent` folder:
    ```bash
    git clone https://github.com/ASMHB/antigravity-config.git .agent
    ```
    *Note: We clone into `.agent` so Antigravity sees it as the configuration source.*

3.  **Detach from Config Repo**:
    Remove the git history of the config so it becomes part of *your* project:
    ```bash
    rm -rf .agent/.git
    ```

4.  **Open in Antigravity**:
    Open the `my-new-project` folder in Antigravity.

5.  **Initialize**:
    Command Antigravity:
    > "Initialize this project"
    
    Antigravity will detect the `.agent/workflows/maintain-project.md` file and execute it, copying the "Golden Master" configs (`tsconfig.json`, `.eslintrc`, etc.) into your project root.

---

## Summary of Differences

| Feature | Command Center (Method 1) | Manual Setup (Method 2) |
| :--- | :--- | :--- |
| **Trigger** | AI Chat Command | Terminal Commands |
| **Workspace** | Must be in `~/Developer` | Anywhere |
| **Speed** | Fastest (1 step) | Slower (Manual setup) |
| **Result** | Identical | Identical |
