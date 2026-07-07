# Markdown Standards

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Standard style rules for markdown formatting and structural formatting.

## Purpose

Define the formatting and structural styling rules for Markdown (`.md`) files in the Lyra repository.

## Formatting Rules

1. **Headers:** Use ATX-style headers (e.g., `# Header`) rather than Setext underlines. Ensure there is a space after the `#` character.
2. **Lists:**
   - Use hyphens (`-`) for unordered lists.
   - Indent sub-lists with 2 spaces.
3. **Tables:** Ensure all tables have a header row and alignment dashes. Wrap all rows in pipe characters (`|`).
4. **Code Blocks:** Always specify a language for syntax highlighting (e.g., ````python`, ````json`, ````mermaid`).
5. **Backticks:** Use backticks only for code symbols, file paths, variables, and literal values. Do not use them for emphasis.

## Review Checklist

- [ ] Unordered lists use hyphens (`-`) for items.
- [ ] No Setext underlines are used for headers.
- [ ] Code blocks specify the programming language.
- [ ] Tables use valid pipe formats with alignment dashes.
