# Setup — install on a new machine

The hub expects fixed absolute paths. Easiest: clone both repos to the same
locations used throughout the prompts:

```bash
git clone <research-agent-repo>   "$HOME/ws/Research agent"
git clone <document-extractor-repo> "$HOME/ws/Document Extractor"
```

If you clone elsewhere, search-and-replace `/Users/samalmutairi/ws/Research agent`
and `/Users/samalmutairi/ws/Document Extractor` across both repos with your paths.

## Cursor

Copy the user-level pieces (they must live outside the repo so every project sees them):

```bash
mkdir -p ~/.cursor/agents ~/.cursor/skills/research-agent
cp setup/cursor/agents/researcher.md  ~/.cursor/agents/
cp setup/cursor/agents/extractor.md   ~/.cursor/agents/
cp setup/cursor/skills/research-agent/SKILL.md ~/.cursor/skills/research-agent/
```

Done. Any Cursor project can now say "research X" and the skill routes
cache → researcher → extractor automatically.

## Claude Code

`CLAUDE.md` in the repo root points at `AGENTS.md`, so opening this repo in
Claude Code gives the agent the same rules. To use the hub *from other
projects*, add the contents of `setup/cursor/skills/research-agent/SKILL.md`
to your global `~/.claude/CLAUDE.md` (Claude Code has no per-agent subagent
files; the skill text works as an instruction block).

## ChatGPT / Codex

Codex (CLI and cloud) reads `AGENTS.md` natively — clone the repo and the
rules apply. ChatGPT in the browser cannot run local scripts; use Codex or
another local agent runtime for the full pipeline.

## Dependencies

- `rg` (ripgrep), `curl` — used by `scripts/search-knowledge` and `scripts/fetch-source`.
- Python 3 — the Document Extractor bootstraps its own `.venv` on first run.
