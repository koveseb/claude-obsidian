---
type: meta
title: "Hot Cache"
updated: 2026-05-31T00:00:00
tags:
  - meta
  - hot-cache
status: evergreen
related:
  - "[[index]]"
  - "[[log]]"
  - "[[Wiki Map]]"
  - "[[getting-started]]"
  - "[[DragonScale Memory]]"
---

# Recent Context

Navigation: [[index]] | [[log]] | [[overview]]

## Last Updated

2026-05-31: hot.md rewritten to reflect v1.9.2 state. Previous entry was from 2026-05-17 (v1.7.1). Three releases shipped in the interim (v1.9.0, v1.9.1, v1.9.2).

## Key Recent Facts

- v1.9.2 is current. Public canonical repo is `AgriciDaniel/claude-obsidian`; install slug `claude-obsidian@agricidaniel-claude-obsidian`. AI-Marketing-Hub repo is now the Pro/early-access mirror (inverted from v1.7.1 era).
- 9 hermetic test suites green (`make test`). New suite added in v1.9.2: `test_contextual_prefix.py` (prompt-cache floor logic).
- `/think` skill added (v1.9): 10-principle loop (OBSERVE-OBSERVE-LISTEN-THINK-CONNECT-CONNECT-FEEL-ACCEPT-CREATE-GROW) invocable as a workflow. Every other skill has a "How to think" appendix.
- Methodology modes shipped (v1.8): LYT / PARA / Zettelkasten / Generic. Configured via `bash bin/setup-mode.sh`; written to `.vault-meta/mode.json`.
- SSS+ compliance files added: `CITATION.cff`, `PRIVACY.md`, `CODEOWNERS`, `.github/FUNDING.yml`.
- SECURITY.md added: single-tenant threat model (v1.9.1).

## Recent Changes (2026-05-17 to 2026-05-31)

### v1.9.2 (2026-05-27, cb93ff6 + 00213b7 + 73616fa)

- `scripts/contextual-prefix.py`: `cache_control` marker attached only when body clears Haiku 4.5 floor (`HAIKU_CACHE_MIN_CHARS = 16384`, ~4096 tokens). Below floor the marker was a silent no-op; now guarded. Extracted as unit-tested `cache_control_for()`.
- Cache telemetry: tier-1 path logs `cache: wrote=N read=N tok` from response `usage` fields (integers only, no content).
- Explicit missing-path now exits 3 cleanly (was silent exit 0). Out-of-vault path exits 2 (was raw `ValueError` traceback).
- Public canonical promotion: `marketplace.json` rewritten; install slug corrected to `agricidaniel-claude-obsidian` everywhere. README, install-guide, CONTRIBUTING, IDE configs updated.
- SEO/GEO pass on README: H1 leads "Self-Organizing AI Second Brain"; 4 verbatim GEO Q&As in FAQ targeting AI Overview + Perplexity citation.
- Social preview card added: `docs/assets/social-preview-1280x640.png`.

### v1.9.1 (2026-05-18, 5cdfecf...1b54a79)

- `fix(hooks)`: SessionStart stale-lock reaper; PostToolUse opt-out gate (H4+S2).
- `fix(scripts)`: symlink canon in wiki-lock; `locks/.gitkeep` added (Data M3+M4).
- `fix(retrieve)`: rerank `hook.log` routing; `setup-retrieve` ollama-localhost assert (Data M1+S4).
- `fix(data)`: atomic chunk writes via tmp+rename (B2).
- `fix(hooks)`: pathspec on add+diff+commit prevents auto-commit blast radius (B1+H1).
- `fix(docs)`: cascade canonical URL fix to 8 files.
- `docs(security)`: SECURITY.md single-tenant threat model.
- README SSS+ tier rewrite (72/100 to ~95/100). Interlinked with public `AgriciDaniel/claude-obsidian` + tagged historical versions.

### v1.9.0 (2026-05-18, 209aad9)

- Audit closure + 10-principle framework added to all skills as "How to think" appendices.
- `/think` skill scaffolded (`skills/think/`).
- AI-Marketing-Hub migration completed.
- Methodology modes (v1.8): LYT/PARA/Zettelkasten/Generic via `bin/setup-mode.sh` + `scripts/wiki-mode.py`.
- Repo hygiene: `workspace-visual.json` gitignored; v1.9.0 audit doc closed.

## Plugin State

- **Version**: 1.9.2
- **Public install**: `claude-obsidian@agricidaniel-claude-obsidian` (AgriciDaniel/claude-obsidian)
- **Pro/early-access**: `claude-obsidian@ai-marketing-hub-claude-obsidian`
- **Skills**: 15 (wiki, wiki-ingest, wiki-query, wiki-lint, wiki-fold, save, autoresearch, canvas, defuddle, obsidian-bases, obsidian-markdown, wiki-cli, wiki-retrieve, wiki-mode, think)
- **Tests**: `make test` 9 suites green. Zero ollama + zero network dependency.
- **Scripts**: v1.6 DragonScale scripts + v1.7 retrieval/lock/transport scripts + v1.8 `scripts/wiki-mode.py` + v1.9.2 `scripts/contextual-prefix.py` (updated).
- **Hooks**: 4 (SessionStart, PostCompact, PostToolUse, Stop).

## DragonScale Mechanisms

1. **Fold** (M1): `skills/wiki-fold/`. First real fold: `wiki/folds/fold-k3-from-2026-04-23-to-2026-04-24-n8.md`.
2. **Deterministic addresses** (M2): counter at 3. `c-000001` on DragonScale Memory.md.
3. **Semantic tiling lint** (M3): `nomic-embed-text`. First report: `wiki/meta/tiling-report-2026-04-24.md` (0 errors, 15 review pairs).
4. **Boundary-first autoresearch** (M4): `scripts/boundary-score.py`. `/autoresearch` without topic surfaces top-5 frontier candidates.

## Style Preferences

- No em dashes (U+2014) or `--` as punctuation. Periods, commas, colons, parentheses only.
- Short and direct. No trailing summaries.
- Parallel tool calls when independent.

## Active Threads

- No known open threads. Repo is public-canonical and v1.9.2 is shipped.
- Working tree has untracked files: `.cursor/skills`, `.windsurf/skills`, `skills-lock.json`, `.obsidian/plugins/obsidian-memos/`.

## Repo Locations

- Public: https://github.com/AgriciDaniel/claude-obsidian
- Pro mirror: https://github.com/AI-Marketing-Hub/claude-obsidian
