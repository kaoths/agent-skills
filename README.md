# agent-skills

Personal agent skills, managed with [Vercel's `skills` CLI](https://github.com/vercel-labs/skills) so they install the same way across every agent harness (Claude Code, ZCode, OpenCode, amp, and more) instead of being locked to one tool's plugin format.

## Layout

Skills live under `skills/<category>/<name>/SKILL.md`:

- `github/` — GitHub PR workflow: fetching changes, fetching/replying to review comments, requesting reviewers

Each skill is a directory containing a `SKILL.md` with YAML frontmatter (`name`, `description`) and its instructions in the body. A `.claude-plugin/plugin.json` at the repo root groups them under "Kaoths Skills" in `skills list`.

## Install

```bash
npx skills add kaoths/agent-skills
```

Pick the skills you want and which agents to install them to (`-g` for a global, cross-project install).

## Reference

### GitHub

- **[fetch-pr-detail](./skills/github/fetch-pr-detail/SKILL.md)** — Fetch a PR's metadata and file changes via a two-phase hybrid approach: triage file stats first (no patches), then pull full diffs only for files worth looking at. Skips lockfiles, codegen, and trivial wiring changes by default.
- **[fetch-pr-review-comments](./skills/github/fetch-pr-review-comments/SKILL.md)** — Fetch a PR's inline review comments and general issue-style comments via `gh api`.
- **[reply-pr-review-comments](./skills/github/reply-pr-review-comments/SKILL.md)** — Reply to a specific inline review comment, threaded, with an `[AgentName::ModelName]` signature so reviewers can tell AI-authored replies apart from human ones. User-invoke only.
- **[request-pr-reviewers](./skills/github/request-pr-reviewers/SKILL.md)** — Request PR reviewers (including Copilot) by browsing valid candidates and confirming a selection conversationally, instead of requiring an exact login upfront. User-invoke only.
