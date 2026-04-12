# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A knowledge base and strategy workspace for discovering, evaluating, and launching AI-native businesses. No application code — this is a research-and-docs repo driven entirely by Claude Code sessions.

The current focus is a WCAG accessibility audit business evaluated through a multi-phase PMF discovery process (see `task_plan.md` for status).

## Repository Structure

- **`docs/`** — All deliverables: research tracks (`docs/research/`), business strategy (`docs/strategies/`, `docs/business/`), outreach templates (`docs/outreach/`), portfolio samples (`docs/portfolio/`), evaluation reports, and business idea categories (`docs/ideas/`)
- **`skills/`** — ~86 Claude Code skills (PM frameworks, design agents, engineering patterns, context management, etc.). Each skill lives in its own directory with a `SKILL.md` and optional `template.md`/`examples/`
- **`task_plan.md`** / **`findings.md`** / **`progress.md`** — File-based planning artifacts for tracking multi-phase work across sessions

## Key Conventions

### Notion Dual-Write (mandatory)
Every substantive file written via the Write tool **must** also be mirrored to Notion using `mcp__claude_ai_Notion__notion-create-pages`. See `.claude/rules/notion-dual-write.md` for the exact payload format and exceptions. Config files, `.claude/` files, test files, and binaries are exempt.

### File-Based Planning
Complex multi-step work uses `task_plan.md` (phases/tasks), `findings.md` (research notes), and `progress.md` (status tracking). These persist across sessions — read them first when resuming work.

### Commit Style
Commit after each meaningful step. Use conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `research:`, `analysis:`, `chore:`.

### Parallel Subagents
Use subagents for independent research tracks (e.g., market sizing, competitor analysis, technical feasibility run in parallel). This keeps the main context window clean and speeds up multi-track research.

## gstack

Use the `/browse` skill from gstack for all web browsing. Never use `mcp__claude-in-chrome__*` tools.

Available skills: `/office-hours`, `/plan-ceo-review`, `/plan-eng-review`, `/plan-design-review`, `/design-consultation`, `/design-shotgun`, `/design-html`, `/review`, `/ship`, `/land-and-deploy`, `/canary`, `/benchmark`, `/browse`, `/connect-chrome`, `/qa`, `/qa-only`, `/design-review`, `/setup-browser-cookies`, `/setup-deploy`, `/retro`, `/investigate`, `/document-release`, `/codex`, `/cso`, `/autoplan`, `/plan-devex-review`, `/devex-review`, `/careful`, `/freeze`, `/guard`, `/unfreeze`, `/gstack-upgrade`, `/learn`.

## Common Commands

```bash
# No build/test/lint — this is a docs-only repo
# Typical workflow is research → write docs → commit

# Check planning state
cat task_plan.md
cat progress.md
cat findings.md
```

## Skill routing

When the user's request matches an available skill, ALWAYS invoke it using the Skill
tool as your FIRST action. Do NOT answer directly, do NOT use other tools first.
The skill has specialized workflows that produce better results than ad-hoc answers.

Key routing rules:
- Product ideas, "is this worth building", brainstorming → invoke office-hours
- Bugs, errors, "why is this broken", 500 errors → invoke investigate
- Ship, deploy, push, create PR → invoke ship
- QA, test the site, find bugs → invoke qa
- Code review, check my diff → invoke review
- Update docs after shipping → invoke document-release
- Weekly retro → invoke retro
- Design system, brand → invoke design-consultation
- Visual audit, design polish → invoke design-review
- Architecture review → invoke plan-eng-review
- Save progress, checkpoint, resume → invoke checkpoint
- Code quality, health check → invoke health
