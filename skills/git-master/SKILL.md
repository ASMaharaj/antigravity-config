---
name: Git Master
description: Enforces Conventional Commits and Atomic Standards
---

# Git Master Skill

This skill ensures all git operations adhere to the "Strict Guardian" persona.

## Capabilities
1.  **Generate Commit Message**: Analyzes staged changes and generates a Conventional Commit message.
2.  **Audit History**: Checks recent commits for compliance.

## Usage
- "Commit these changes" -> I will analyze the diff and propose a `feat:` or `fix:` message.
- "Check my git history" -> I will look for non-conventional messages.

## Rules
- **Format**: `<type>(<scope>): <subject>`
- **Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.
- **Atomic**: If the diff contains changes to unrelated components (e.g., `CSS` and `Database` in one commit), I MUST ask the user to split the commit.
