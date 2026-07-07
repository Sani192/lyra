# Branching Strategy

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative branching rules, git workflows, and pull request conventions for Lyra contributors and AI agents.

## Purpose

Define the workflow for version control branch management, ensuring every change is isolated, reviewable, traceable to a requirement ID, and safely integrated.

## Scope

Applies to all branches, pull requests, and merges in the Lyra repository.

## Branch Naming Standard

All feature, fix, refactoring, and documentation branches must be scoped to specific requirements and named using the following format:

`<type>/LYRA-<CATEGORY>-<NUM>-<short-description>`

1. **Branch Types (`<type>/`):**
   - `feature/` - for new requirements.
   - `bugfix/` - for fixing existing bugs.
   - `refactor/` - for cleanups and performance optimization.
   - `docs/` - for documentation additions or changes.
2. **Short Description:** Lowercase, hyphen-separated, under 5 words (e.g., `feature/LYRA-FR-001-conversation-engine`).
3. **Examples:**
   - `feature/LYRA-FR-001-conversation-engine`
   - `bugfix/LYRA-SEC-002-sanitize-transcripts`
   - `refactor/LYRA-NFR-003-optimize-cache`
   - `docs/LYRA-OBS-001-add-audit-logging-docs`

If a change is purely administrative and has no requirement ID, use `docs/admin-<description>` or `admin/cleanup-<description>` with prior maintainer approval.

## Git Workflow Standards

* **Main Branch Safety:** Direct commits to `main` are strictly blocked. All changes must go through feature branches and pull requests.
* **Feature Isolation:** Start every new task by pulling the latest changes from `main` and creating a new branch. Keep branches small and focused on a single requirement or a closely related group of requirement IDs.
* **Rebase Strategy:** Frequently rebase feature branches against `main` to resolve conflicts early and before submitting a pull request. This ensures a clean, linear git history. Merge commits are disabled on `main`.
* **Squash Merging:** Pull requests must be squash-merged into `main` to combine the feature branch's commit history into a single clean commit on the target branch.

## Review Checklist

- [ ] Branch is based on the latest commit of `main`.
- [ ] Branch name includes a valid, stable requirement ID matching naming standards.
- [ ] Pull request description links to the issue or specification containing the requirement ID.
- [ ] Branch contains no changes unrelated to the targeted requirement.
- [ ] Branch is rebased and syncs cleanly with the latest `main`.
- [ ] No merge commits exist within the feature branch (use rebase instead).
- [ ] Commit history is clean and ready for squash merging.
