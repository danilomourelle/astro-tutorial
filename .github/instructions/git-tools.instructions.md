---
description: "Use when running git operations: status, diff, log, commit, push, pull, branch, checkout, stash, or opening pull requests. Enforces MCP-first tool usage over shell commands."
---
# Git Tool Usage

Always prefer MCP server tools over shell commands for git and GitHub operations.

## Tool Priority

1. **GitKraken MCP** (`mcp_gitkraken_git_*`) — for local git operations:
   - `mcp_gitkraken_git_status` → `git status`
   - `mcp_gitkraken_git_log_or_diff` (required: `action`) → `git log` / `git diff`
     - `action: "log"` — shows commit history; supports `revision_range`, `since`, `until`, `authors`
     - `action: "diff"` — shows unstaged/staged changes; supports `revision_range` (e.g. `"main..feature"`)
   - `mcp_gitkraken_git_add_or_commit` (required: `action`) → `git add` / `git commit`
     - `action: "add"` — stages files; pass `files` array (repo-relative paths, no leading slash) to stage specific paths, omit to stage all
     - `action: "commit"` — commits already-staged changes; requires `message`; do NOT pass `files` here — always call `add` first
     - **Always use two separate calls**: one `add`, then one `commit`
   - `mcp_gitkraken_git_push` → `git push`
   - `mcp_gitkraken_git_pull` → `git pull`
   - `mcp_gitkraken_git_branch` → `git branch`
   - `mcp_gitkraken_git_checkout` → `git checkout`
   - `mcp_gitkraken_git_stash` → `git stash`

2. **GitHub MCP** (`mcp_io_github_git_*`) — for GitHub API operations:
   - `mcp_io_github_git_create_pull_request` → open PR
   - `mcp_io_github_git_list_pull_requests` → list PRs
   - `mcp_io_github_git_create_branch` → create remote branch
   - `mcp_io_github_git_get_file_contents` → read file from GitHub

3. **Shell fallback** — only when no MCP tool covers the operation. State why the fallback is needed.
