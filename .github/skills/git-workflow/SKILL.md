---
name: git-workflow
description: 'Manage the git workflow for this project. Use when creating branches, opening pull requests, or finishing a feature or fix. Enforces branch naming (type/topic), ensures branches start from main, and opens PRs targeting main.'
argument-hint: 'What you are working on (e.g. fix login bug, add hero section)'
---

# Git Workflow

This project has a single integration branch (`main`). There are no staging or
production environments — all work branches are cut from `main` and merged back
via pull request.

## Branch Naming

```
type/topic
```

| Part    | Rules                                                                 |
| ------- | --------------------------------------------------------------------- |
| `type`  | Single lowercase word: `feat`, `fix`, `test`, `docs`, `refactor`, `chore`, `build` |
| `topic` | Kebab-case summary, fewest words that remain clear (e.g. `hero-section`, `nav-links`, `login-redirect`) |

**Examples**: `feat/hero-section`, `fix/nav-overflow`, `docs/readme-commands`

## Procedure

### Starting new work

1. Ensure the local `main` is up to date:
   ```sh
   git checkout main && git pull origin main
   ```
2. Choose `type` and a short `topic` for the branch.
3. Create and switch to the new branch:
   ```sh
   git checkout -b type/topic
   ```
4. Implement the changes, committing with the `conventional-commit` skill.

### Finishing work

1. Push the branch to the remote:
   ```sh
   git push -u origin type/topic
   ```
2. Open a pull request targeting `main` — use the branch name as the PR title
   base and summarize the changes in the PR body.
3. After the PR is merged, delete the remote branch and update local `main`:
   ```sh
   git checkout main && git pull origin main
   git branch -d type/topic
   ```

## Quality Checks

- Branch was created from an up-to-date `main` (not from another branch).
- Branch name matches `type/topic` pattern (single-word type, kebab-case topic).
- All commits follow the `conventional-commit` skill format.
- PR targets `main`.
