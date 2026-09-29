# RETIRED: cortex

- **Retired:** 2026-09-29
- **Reason:** Current models (the Claude 5 family) carry enough context, and Claude Code's own memory
  (CLAUDE.md, auto-memory, path-scoped rules) covers cross-session continuity, so an external
  event-sourced memory layer is no longer needed. The CLI was already uninstalled, and the hooks
  still wired in two repos were failing silently on every session.
- **Superseded by:** Claude Code built-in memory (CLAUDE.md files, auto-memory, `.claude/rules/`)

## Surfaces

| Surface | Status | Verified how |
|---|---|---|
| Schedulers | N/A | `launchctl list`, `~/Library/LaunchAgents`, `crontab -l`: no cortex entries |
| Credentials | N/A | value-pattern scan of the clone found none; `gh secret list` empty; no `.env` tracked |
| Permissions | removed | cortex hooks (`cortex stop` / `precompact` / `session-start`) stripped from the untracked `.claude/settings.local.json` in social-media-scheduling-app and RR-Editorial-Workflow (their permissions left intact); the clone's own `settings.local.json` goes with the clone |
| Integrations | removed, one exception | Snyk webhook on GitHub `Jmeg8r/cortex` deleted (hooks = 0); forge hooks = 0; 9 open PRs closed on both forges; forge push mirror removed before archiving; both remotes archived |
| Consumer residue | removed | `.claude/rules/cortex-*.md` deleted: RR-Editorial-Workflow (untracked, deleted locally), social-media-scheduling-app (forge PR #7), revri (forge PR #156, also its CLAUDE.md pointer and .gitignore entry) |
| Local clone | deleted | nothing unique: all branches pushed except `chore/coderabbit-tools-key` (one `.coderabbit.yaml` reshuffle, dropped by James's decision); untracked `lefthook.yml` and PR template are byte-identical to project-template's copies |
| Caches & state | N/A | `~/.cortex` does not exist; no `cortex` binary on PATH, in pyenv, pipx or npm globals |

## NOT retired, and why

- **Snyk project** for `Jmeg8r/cortex`: the webhook is gone, but the project entry lives in the Snyk
  UI, which this session cannot reach. James removes it there.
- **Uncommitted clone edits discarded:** a one-word README change ("Cursor" to "etc.") and four
  local-tooling `.gitignore` entries. Neither mattered for a retired repo.

## Rescued artifacts

None needed. The code, the research paper (`docs/research/paper/`) and the A/B results
(`docs/testing/AB-COMPARISON-RESULTS.md`) remain in both archived remotes.
