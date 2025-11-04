# Copilot Coding Agent Onboarding Guide for NetAppDocs/workload-fsx-ontap-internal

## High-Level Overview

- The `workload-fsx-ontap-internal` repository contains all source files for the HTML documentation of Amazon FSx for NetApp ONTAP in Workload Factory.
- This documentation repository focuses on providing user guides, procedures, reference material, and support documentation for FSx for ONTAP workloads.

---

## Content Quality and Standards Enforcement

- **Always align** newly added or modified content to the requirements in the `content-standards.pdf` (not currently in-repo; check org standards if available).
- *Each build must include:*
  - Clear, precise writing.
  - Verification that the Markdown and AsciiDoc syntax in `.adoc` files meets formatting and code standards (headers, lists, links, and blocks must match house style).
  - Validation of code snippets and technical instructions.
  - Consistent terminology and section organization as per the content standards.
- **Explicit Validation Steps:**
  - Manually run a spell check and grammar check.
  - Review AsciiDoc for correct rendering (try using a compatible AsciiDoc viewer if possible).
  - Cross-check new content against existing documentation for redundant information or style mismatches.

---

## Build Instructions

1. Make all documentation changes in `.adoc` or `.md` files as relevant.
2. Review content for quality control using the `content-standards.pdf`.
3. Validate:
    - No broken links.
    - All images referenced in documentation are present in the `media/` directory and described as needed.
    - No orphaned or unreferenced files.
    - Consistency in naming, numbering, and structure of procedures/topics.
    - Code examples render correctly in preview.
4. Build previews if possible using local AsciiDoc toolchains or GitHub's AsciiDoc preview feature.

---

## Project Layout & Architectural Elements

### Major Directories and Files (repo root)

- `.gitignore`
- `.vscode/settings.json` (editor preferences)
- `README.md`: Minimal—expand with project purpose and instructions if adding content.
- `_index.yml`: Site navigation/structure definition.
- `project.yml`: Project configuration, possibly site-wide settings.
- Multiple `.adoc` files: Each named by purpose and topic (e.g. `create-file-system.adoc`, `cascade-replication.adoc`, etc.).

### Key Subdirectories

- `_include/` – reusable AsciiDoc snippets (contains files such as `create-replication.adoc`)
- `_whatsnew/` – changelogs or release notes by date (e.g., `2024-07-07.adoc`, `2025-03-02.adoc`, etc.)
- `media/` – image assets (screenshots, diagrams; filenames often self-descriptive).
- `store-redirects/` – possible support for redirects or legacy documentation links.

### Editor/Build Configuration

- `.vscode/settings.json` maintains workspace settings (tab size, markdown formatting, preview options), useful for maintaining editor consistency.

### CI/CD and Validation

- No explicit CI/CD or lint workflows in evidence from this inventory.
- All validation and pre-check-in steps should be manual, referencing content standards and local preview.

### Typical Check-In Steps

1. Draft/update document in appropriate `.adoc` file.
2. Add any images to `media/` and reference in doc.
3. If reusable snippet, update/add in `_include/`.
4. If announcing new features, update in `_whatsnew/` with dated file format.
5. Preview and validate that .adoc renders correctly.
6. Spellcheck, grammar check, and cross-reference to avoid duplication.
7. Submit changes and notify reviewers of manual quality assurance steps taken.

---

## File Inventory (root and select subdirs)

**Repo Root:**
- Documentation files: `access-data.adoc`, `add-ha-pairs.adoc`, `cascade-replication.adoc`, etc.
- Project/config: `.gitignore`, `project.yml`, `_index.yml`
- README.md (empty/minimal as of latest inventory)

**_include/:**
- `README.md` (placeholder—delete when populated)
- `create-replication.adoc` (snippet)

**_whatsnew/:**
- Files named by YYYY-MM-DD (e.g., `2024-09-29.adoc`, `2025-03-02.adoc`, etc.)

**media/:**
- `README.md` (placeholder)
- Images: `diagram-fsx-data-protection.png`, `screenshot-menu-tracker-option.png`, and various screenshots

---

## Noted Alignment Errors and Workarounds

- The repository's README is **minimal** and does not conform to typical standards; recommend expanding to describe repo goals, major directories, and contribution process.
- If `content-standards.pdf` is missing from repo, always refer to the most up-to-date version available in org documentation or request access.
- No automated validation or CI/CD present—require manual QA for all changes.

---

### Summary of Best Practices for Efficient Work

- Use in-file headers and explicit section names in `.adoc` for clarity.
- Prioritize documentation reuse via the `_include/` directory.
- Confirm all new images are correctly referenced.
- Update `_whatsnew/` promptly to reflect all released changes.
- Always align with content quality standards, even if not enforced by automation.
- If workflow or CI config is added in future, document validation steps here for agent reference.

---