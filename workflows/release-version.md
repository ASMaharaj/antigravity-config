---
description: Semantic Versioning and Changelog generation workflow.
---

This workflow automates the release process by analyzing git history and enforcing SemVer.

1.  **Preparation**:
    *   Identify the current version (from `package.json` or `pyproject.toml`).
    *   Run `git fetch --tags`.
    *   Get commits since the last tag.

2.  **Analysis**:
    *   Analyze commit messages (Conventional Commits).
    *   **Major**: Breaking changes (`BREAKING CHANGE` or `feat!`).
    *   **Minor**: New features (`feat`).
    *   **Patch**: Fixes (`fix`, `perf`, `refactor`).
    *   Display: "Current: 1.0.0 -> Recommended: 1.1.0 (Minor)".

3.  **Confirmation**:
    *   Ask: "**Proceed with release v[Version]?**"

4.  **Execution**:
    *   **Update File**: Bump version in `package.json`/`pyproject.toml`.
    *   **Update Changelog**: Prepend new section to `CHANGELOG.md`:
        ```markdown
        ## [1.1.0] - YYYY-MM-DD
        ### Added
        - feat: ...
        ### Fixed
        - fix: ...
        ```
    *   **Commit**: `chore(release): prepare v1.1.0`.
    *   **Tag**: `git tag -a v1.1.0 -m "v1.1.0"`.

5.  **Push**:
    *   `git push --follow-tags`.
