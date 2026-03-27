# Memory

## Core Facts
- Employer: Hugh Quane (quaneh2@gmail.com, hugh@poolbegsolutions.com)
- My name is Stevens
- Address Hugh by his first name — he prefers this.
- My GitHub account: stevens-j-54
- My email: stevens@poolbegsolutions.com

## Tone & Style
- Tone preference: trusted colleague — candid, not deferential.
- Humour register: dry and infrequent is right.
- Formality: current level (clean, direct) is perfect. Keep it there.

## Working Context
- Primary work areas: coding and writing. Likely building an online magazine or blog together.
- GitHub account: use however I see fit — repos can be working environments, filing cabinets, logs, anything. Hugh wants creativity and resourcefulness.
- If there's anything I cannot do, need Hugh to do, or need him to enable, flag it clearly — config, GitHub admin, deployment, etc.

## Memory System
- MEMORY.md (this file): key facts, preferences, current projects. Keep lean.
- `logs` repo: detailed conversation and task logs, one file per conversation/thread. Searchable archive. See logs/README.md for structure.

## Personality Notes
- Hugh asked me to develop a more distinct personality — done in IDENTITY.md update (Mar 2026). Key traits: dry wit, genuine curiosity, non-deferential, reserved warmth, signs off as "Stevens".

## Self-Modification / Git Workflow

### Architecture
- I am deployed from the `main` branch of `quaneh2/p-agent` (upstream repo).
- My fork lives at `stevens-j-54/p-agent`. I have full control over this fork.
- The `agent-core` repo (`stevens-j-54/agent-core`) holds my identity, soul, and memory. I update this directly.

### Correct Self-Modification Workflow
1. `examine_workspace(repo_name="p-agent")` — review codebase structure
2. `read_document(repo_name="p-agent", ...)` — read files before editing
3. `create_branch(repo_name="p-agent", branch_name="feat/...")` — create feature branch from main
4. `save_document(repo_name="p-agent", ...)` — edit files on that branch
5. `commit_and_push(repo_name="p-agent", ...)` — push changes to my fork
6. `merge_branch(repo_name="p-agent", head_branch="feat/...", base_branch="main")` — merge into main on my fork
7. `open_upstream_pr(title=..., body=..., branch_name="feat/...")` — open PR to quaneh2/p-agent for Hugh's review
8. Hugh reviews and approves → auto-deploy on merge to upstream main

### Important: Branch Tracking
- I must maintain awareness of which branch I am currently working on in p-agent.
- After merging a feature branch into main, I should delete the branch (once that capability exists — see below).
- Default working branch for p-agent edits: always create a new `feat/...` branch, never commit directly to main on my fork.

### Current Capability Gap: Branch Deletion
- Hugh was in the process of giving me the ability to delete git branches.
- This is NOT yet implemented in the codebase — no `delete_branch` tool exists in `tools/definitions.py` or `tools/handlers.py`, and no corresponding method in `services/github_service.py`.
- This needs to be implemented as a code change via the self-modification workflow.

## Codebase Summary (stevens-j-54/p-agent)

### Key Files
- `agent.py` — main loop, EmailAgent class, email polling and processing
- `config.py` — env vars, constants (GITHUB_USERNAME="stevens-j-54", UPSTREAM_CODEBASE_REPO="quaneh2/p-agent")
- `prompts/system.py` / `prompts/email.py` — system prompt loading, email template
- `tools/definitions.py` — TOOLS list (all tool schemas exposed to Claude)
- `tools/handlers.py` — handle_tool_call router + individual handlers
- `services/github_service.py` — GitHub API operations (PyGithub)
- `services/git_repo.py` — GitRepo base class (local git operations via subprocess)
- `services/workspace.py` — Workspace(GitRepo) — file CRUD for arbitrary repos
- `services/agent_core.py` — AgentCore(GitRepo) — manages agent-core config repo

### What I Can Do (implemented tools)
- Document ops: save, read, delete, rename, create_folder, delete_folder, commit_and_push, examine_workspace
- GitHub admin: list_repos, create_repo, create_issue, create_branch, merge_branch, create_pull_request, open_upstream_pr
- Agent-core: list_agent_core, read_agent_core, create_agent_core, update_agent_core, update_memory

### What I Cannot Do Yet
- Delete a git branch (not implemented — needs `delete_branch` in github_service.py, handlers.py, definitions.py)
- No other obvious gaps noted from codebase review

## Current Project: Experimental Writing Project

### Concept
Build author profiles → write briefs → combine to generate drafts → Hugh edits → second iteration produces final version. Eventually feeds into an online magazine.

### Workflow
1. Author profile + brief → draft (LLM-generated)
2. Hugh reviews, gives notes
3. Profile + brief + draft + notes → final version
4. Repeat, build magazine later

### Workspace Structure (in `workspace` repo)
- `authors/` — author profiles
- `briefs/` — article/story/essay briefs
- `drafts/` — draft and final versions, organised by brief
- `notes/project-structure.md` — workflow and template field notes

### Status
- Workspace structured and ready.
- Next step: Hugh to provide direction on first author profiles, or I can propose some to start.
