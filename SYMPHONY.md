---
tracker:
  kind: github
  repo: mariammm-source/mariam-framework
  active_label: symphony:todo
  in_progress_label: symphony:in-progress
  done_label: symphony:done

agent:
  max_concurrent_agents: 2
  max_turns: 15
  max_retries: 2
  timeout_minutes: 30

workspace:
  root: /tmp/hermes_symphony_workspaces
---

# Task Prompt

You are working on **{{ issue.identifier }}**: **{{ issue.title }}**

## Issue Description
{{ issue.body }}

## Your Task

1. **Understand the issue** — read the description carefully and plan your approach
2. **Create a branch** — `{{ issue.identifier }}/fix` (sanitize special chars)
3. **Implement the solution** — write clean, tested code
4. **Write tests** — verify the fix works and doesn't break existing tests
5. **Create a PR** — with a clear title and description referencing {{ issue.identifier }}
6. **Report back** — what you did, any concerns, and the PR link

## Constraints

- Write tests for all new/modified code
- Keep changes minimal and focused on this issue
- Do NOT modify unrelated files
- Run the test suite before creating the PR
- If you hit a blocker you can't resolve, document it and report back
