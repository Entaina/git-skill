---
name: git
description: Git conventions and commit message formatting. Use when generating commit messages, working with Git history, or using /git:commit. Strictly applies Conventional Commits v1.0.0 to generated messages, in English unless the user explicitly requests another language.
---

# Git Conventions

Git conventions reference. Commit message formatting strictly follows the Conventional Commits v1.0.0 specification.

## Conventional Commits

When generating a commit message, read and strictly follow `references/conventional-commits-v1.0.0.md`.

### Language

Write all generated commit messages in English unless the user explicitly requests another language. This includes the description, body, and footer text. The language of the conversation alone does not override this default. Preserve Conventional Commits syntax and required tokens such as `BREAKING CHANGE` regardless of the requested language.

User-provided messages are handled separately as described below; do not translate them.

### Format

```text
<type>[(scope)][!]: <description>

[optional body]

[optional footer(s)]
```

### Valid Types

| Type | Use when... |
|------|-------------|
| `feat` | Adding new functionality (MINOR in SemVer) |
| `fix` | Fixing a bug (PATCH in SemVer) |
| `docs` | Changing documentation only |
| `style` | Changing formatting without changing logic (whitespace, semicolons, etc.) |
| `refactor` | Changing code without fixing a bug or adding a feature |
| `perf` | Improving performance |
| `test` | Adding or correcting tests |
| `build` | Changing the build system or external dependencies |
| `ci` | Changing CI/CD configuration |
| `chore` | Performing maintenance that does not touch source code or tests |
| `revert` | Reverting a previous commit |

### Rules for Generated Messages

1. **Choose the type**: Analyze the changes and choose the type that best describes the work. Consult the types table and specification rules 2, 3, and 14.

2. **Infer the scope**: Analyze the directories and modules affected by the changes.
   - If changes are concentrated in a clear directory or module, use it as the scope: `feat(auth):`, `fix(parser):`
   - If changes affect multiple areas without a predominant module, omit the scope: `refactor:`
   - The scope must be a short noun describing a section of the codebase (specification rule 4).

3. **Write the description**: Provide a short, imperative summary of the change.
   - Use lowercase (do not capitalize the first letter).
   - Do not end with a period.
   - Limit the entire first line to 50 characters.
   - Use the imperative: "add feature", not "added feature" or "adds feature".

4. **Body** (optional): Include it when changes are complex or need additional context.
   - Separate it from the description with a blank line (rule 6).
   - Use free-form text; multiple paragraphs are allowed (rule 7).
   - Explain "why" the change was made, not just "what" changed.

5. **Breaking changes**: Indicate changes that break backward compatibility.
   - Use `!` before `:` in the type/scope prefix: `feat(api)!: remove deprecated endpoint`
   - And/or use a footer: `BREAKING CHANGE: description of the breaking change` (rules 11–13).

6. **Footers** (optional): Include additional metadata.
   - Format: `Token: value` or `Token #value` (rule 8).
   - Use `-` instead of spaces in tokens: `Reviewed-by`, `Refs` (rule 9).

### User-Provided Messages

When the user provides a message with `-m`, **preserve it exactly without modifying, translating, or validating it**. Conventional Commits formatting and the English default apply only to generated messages.
