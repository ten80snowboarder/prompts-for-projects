# SESSION_STATE

## Status

`DONE`

## Last action

Bootstrapped the empty repository to its own specification: wrote the standards, roadmap,
three layered prompts, and three installable templates, then deleted the drafting
scratchpad.

## Verified

- `find` → 8 files in the expected layout; `draft-prompt.md` absent after deletion.
- `grep -c '^\`\`\`'` per prompt → 2 fences each: exactly one `text` block opened and closed.
- `wc -l` → core 145, React 114, WordPress 118; every file under the 500-line ceiling and
  within its stated budget.
- `grep -n '^## '` per prompt → `When to use`, `Prompt`, `Composition notes`,
  `Revision log` present in that order.
- Hedging-word sweep over `/prompts/` → zero hits except the deliberately quoted banned
  phrase "should work".

## Checks not run

- No Markdown renderer or linter was executed; this repository ships no tooling and
  `AGENTS.md` §11 forbids adding any. Structure was verified by fence and header counts
  instead.
- No prompt was executed against a live coding agent. Behavioral effect is unverified by
  construction — the prompts are the artifact, not code under test.

## Pending

1. Wait for a real agent run against each prompt before claiming the rules land; record
   observed drift as a revision, not a rewrite.
2. Split WordPress into `21-wordpress-plugins.md` / `22-wordpress-themes.md` only when the
   file crosses 150 lines (currently 118).
3. Decide the standards gap in `FOLLOWUPS.md`: whether prompt metadata must declare its own
   verification command set so composed layers cannot emit conflicting gates.
4. `AGENTS.md` §1 tree must be updated the moment a new prompt lands, or the map lies.

## Open questions

- Repository is not under version control. `git init` was not requested, so no history
  exists — every change so far is unstaged-by-absence. Confirm whether to initialize.
- No `.gitignore` or `.agentignore` exists. `AGENTS.md` §11 states the ignore rules in
  prose; a real ignore file would enforce them. Awaiting a decision.
- Whether the review gate (`AGENTS.md` §9) should be automated by a `40-code-review-agent`
  prompt that audits new prompt files, or stay a manual checklist.

## Active files

- `AGENTS.md` — repository standards, layering, review gate, session protocol.
- `FOLLOWUPS.md` — roadmap; bootstrap and first three prompts struck as done.
- `prompts/00-core-agent-protocol.md` — five-phase universal protocol, Three Laws.
- `prompts/10-react-typescript.md` — React 18 + TS strict layer.
- `prompts/20-wordpress.md` — WordPress security-first layer.
- `templates/AGENTS.md` — installable project standards with command table.
- `templates/SESSION_STATE.md` — handoff schema.
- `templates/FOLLOWUPS.md` — roadmap schema.

## Found, not fixed

- Repository has no `.git` directory at initialisation time. Out of scope for a
  documentation task; recorded above as an open question.
- `AGENTS.md` §5 reserves layers `30–39` and `40–49` with no files yet. Intentional, so new
  prompts slot in without renumbering.
