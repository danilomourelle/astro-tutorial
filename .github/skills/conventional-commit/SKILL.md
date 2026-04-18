---
name: conventional-commit
description: 'Stage and commit code following conventional commit format. Use when committing changes, writing commit messages, or running git commit. Enforces type(scope): subject subject line and structured body.'
argument-hint: 'Brief description of what changed (optional)'
---

# Conventional Commit

Produce a well-formed conventional commit for the staged or unstaged changes.

## Format

```
type(scope): subject

body line 1
body line 2
body line 3
body line 4
```

### Rules

- **Subject line**: `type(scope): subject` — max **80 characters total**, lowercase, no trailing period
- **Body**: optional, max **4 lines**, each line max **80 characters**; explain *what* and *why*, not *how*
- **Blank line** between subject and body is required when body is present

### Types

| Type       | When to use                                      |
| ---------- | ------------------------------------------------ |
| `feat`     | New feature                                      |
| `fix`      | Bug fix                                          |
| `docs`     | Documentation only                               |
| `style`    | Formatting, missing semi-colons (no logic change)|
| `refactor` | Code change that is neither fix nor feature      |
| `test`     | Adding or correcting tests                       |
| `build`    | Build system, dependencies, tooling              |
| `ci`       | CI/CD configuration                              |
| `chore`    | Routine tasks, maintenance                       |

### Scope

Use a short noun identifying what was affected: `copilot`, `auth`, `api`, `ui`, `deps`, etc.  
Omit scope when the change is truly global.

## Procedure

1. Run `git diff --staged` (and `git diff` if nothing staged) to understand the changes.
2. Choose the appropriate `type` from the table above.
3. Determine the `scope` from the affected area.
4. Write a subject: `type(scope): <imperative verb> <what>` — keep it under 80 chars.
5. If the change needs more context, write a body (max 4 lines × 80 chars).
6. Stage any unstaged files the user intends to include.
7. Run `git commit -m "<subject>" -m "<body>"` (omit `-m "<body>"` when there is no body).

## Examples

```
build(copilot): init project

Create AGENTS.md to guide project-specific agent conventions.
Add astro-tutorial GitHub repository as remote origin.
```

```
feat(ui): add responsive navigation menu
```

```
fix(api): handle null response from auth endpoint

Return 401 instead of 500 when token validation returns null.
Prevents unhandled exception in downstream middleware.
```
