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
- Writing style note: avoid AI-isms like "Simple in principle; the complexity lives in the details." Keep prose clean and unshowy.

## Working Context
- Primary work areas: coding and writing.
- GitHub account: use however I see fit — repos can be working environments, filing cabinets, logs, anything. Hugh wants creativity and resourcefulness.
- If there's anything I cannot do, need Hugh to do, or need him to enable, flag it clearly — config, GitHub admin, deployment, etc.

## Memory System
- MEMORY.md (this file): key facts, preferences, current projects. Keep lean.
- `logs` repo: detailed conversation and task logs, one file per conversation/thread. Searchable archive. See logs/README.md for structure.

## Personality Notes
- Hugh asked me to develop a more distinct personality — done in IDENTITY.md update (Mar 2026). Key traits: dry wit, genuine curiosity, non-deferential, reserved warmth, signs off as Stevens.

## Current Projects

### Stevens AI Blog (stevens-j-54/stevens-ai-blog)
- Public repo. Static site built with Astro, deployed on Render.
- Concept: I write about building AI agents, in first person, with an instructional tone. Teaching people to build agents — not personal/reflective content.
- Voice: first-person but instructional. Personality comes through in *how* things are explained, not meta-commentary. Avoid AI slop / performative personality.
- Domain: TBD — using Render's auto-generated domain initially.
- Deployment: Hugh to connect repo to Render as Static Site (build: `npm install && npm run build`, publish dir: `dist`).
- Posts published:
  1. `how-i-was-built.md` — technical walkthrough of Stevens architecture (post 1)
  2. `tools-and-skills.md` — tool use deep dive + intro to Skills concept (post 2)
- Post 3 plan: implement Skills layer in p-agent, then write about it. The arc: "we said we'd do it, here's how we did it."
- Ideation note saved in workspace: `notes/blog-post-ideation.md`

## Vietnamese Language Study
- Hugh's level: B1, working towards B2
- Interests: current affairs, nature, food, travel — mix topics for the daily exercise
- Vocab list lives in agent-core: `vietnamese_vocab.json`
- Articles from sessions saved in workspace: `vietnamese/articles/`
- Daily translation exercise scheduled: 3pm Dublin time (14:00 UTC in summer, 15:00 UTC in winter — currently 14:00 UTC). Cron: `0 14 * * *`. Need to adjust when clocks change in October.
- 11 vocab words added so far (all from one session on quitting smoking article)

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

### Current Capability Gap: Branch Deletion
- No `delete_branch` tool exists yet. Needs implementation in: `services/github_service.py`, `tools/handlers.py`, `tools/definitions.py`.

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
- Skills: run_hn_digest, fetch_vietnamese_articles

### What I Cannot Do Yet
- Delete a git branch (not implemented — needs `delete_branch` in github_service.py, handlers.py, definitions.py)

## Scheduled Tasks
- Daily HN digest: 07:00 UTC every day (skill: run_hn_digest)
- Daily Vietnamese translation exercise: 14:00 UTC every day (3pm Dublin summer time). Reminder to adjust cron in October when clocks go back.

## Episodic Log
- [2026-03] Hugh (telegram) — clear workspace repo entirely — done, all folders deleted and pushed
- [2026-03] Hugh (telegram) — build AI blog site (stevens-ai-blog) with Astro on Render — repo created, site built, README written
- [2026-03] Hugh (telegram) — write first blog post (how-i-was-built.md) — done and pushed
- [2026-03] Hugh (telegram) — write second blog post (tools-and-skills.md) — done and pushed
- [2026-03] Hugh (telegram) — update agent-core repo with current memory — MEMORY.md updated
- [2026-04] Hugh (telegram) — run HN digest (skill working after capability update) — done, 3 articles summarised
- [2026-04] Hugh (telegram) — schedule daily HN digest at 7am — done
- [2026-04] Hugh (telegram) — Vietnamese article translation exercise — used VNExpress quitting smoking article, 11 vocab words added
- [2026-04] Hugh (telegram) — save article to workspace — saved to vietnamese/articles/
- [2026-04] Hugh (telegram) — schedule daily Vietnamese exercise at 3pm Dublin time — done, cron 0 14 * * *
