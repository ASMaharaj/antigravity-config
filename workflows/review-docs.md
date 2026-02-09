---
description: Interactively review all project documentation to Update, Archive, or Keep.
---

This workflow helps you maintain valid documentation by iterating through your markdown files.

1.  **Preparation**:
    *   Create `docs/archive` if it doesn't exist.
    *   List all `.md` files in the project (excluding `node_modules`, `.agent`).

2.  **Review Loop**:
    *   **For each markdown file**:
        *   Display the file path and last modified date.
        *   Ask: "**Status?** (KEEP | UPDATE | ARCHIVE)"
        *   **If UPDATE**:
            *   Ask: "What has changed in the system?"
            *   Agent reads the file and edits it to reflect the current codebase state.
        *   **If ARCHIVE**:
            *   Move file to `docs/archive/YYYY-MM-DD-[filename]`.
            *   Add header: `> **ARCHIVED**: [Date]. Reason: Obsolete.`
        *   **If KEEP**:
            *   Do nothing.

3.  **Completion**:
    *   Commit changes with message "docs: Routine documentation review and cleanup".
