# SESSION_STATE

## Status

`DONE`

## Last action

Bootstrapped the empty repository to its own specification — standards, roadmap, three
layered prompts, three installable templates, scratchpad deleted — then initialized git
and pushed `main` to `origin`. The current HEAD is the commit containing this file; run
`git log -1` instead of trusting a hash written here.

## Verified

- `find` → 8 files in the expected layout; `draft-prompt.md` absent after deletion.
- `grep -c '^\`\`\`'` per prompt → 2 fences each: exactly one `text` block opened and closed.
- `wc -l` → core 145, React 114, WordPress 118; every file under the 500-line ceiling and
  within its stated budget.
- `grep -n '^## '` per prompt → `When to use`, `Prompt`, `Composition notes`,
  `Revision log` present in that order.
- Hedging-word sweep over `/prompts/` → zero hits except the deliberately quoted banned
  phrase "should work".
- `git ls-remote` before init → exit 0 with no refs: the remote existed and was empty, so
  no history could be overwritten.
- `git push origin main` → exit 0 on every push; the bootstrap commit is `0369cb2`. After
  each push, `git ls-remote origin` matched the local `HEAD` for both `HEAD` and
  `refs/heads/main`, and `git status --short --branch` showed `## main...origin/main`
  with no dirty paths.
- `git check-ignore -v` → `.DS_Store`, `.freebuff`, and `draft-prompt.md` each matched a
  `.gitignore` line, and `git ls-files` lists 10 tracked files, all text.
- `.gitignore` confirmed to exclude `.DS_Store`, `.freebuff/`, and `draft-prompt.md`; all
  ten tracked files are text and none is generated.

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

- No `.agentignore` exists. `AGENTS.md` §11 states the read prohibitions in prose and
  `.gitignore` now covers tool state and scratchpads, but nothing machine-enforces the
  `node_modules`/`vendor`/`.git` rules. Confirm whether to add one.
- Whether the review gate (`AGENTS.md` §9) should be automated by a `40-code-review-agent`
  prompt that audits new prompt files, or stay a manual checklist.
- CI is unset. A workflow that fails on a prompt file with unbalanced fences, a missing
  required section, or a body over its declared line budget would make the §9 gate
  mechanical rather than a promise. Not added: `AGENTS.md` §11 forbids tooling.

## Active files

- `.gitignore` — excludes Mac metadata, the tool marker, and the scratchpad.
- `AGENTS.md` — repository standards, layering, review gate, session protocol.
- `FOLLOWUPS.md` — roadmap; bootstrap and first three prompts struck as done.
- `prompts/00-core-agent-protocol.md` — five-phase universal protocol, Three Laws.
- `prompts/10-react-typescript.md` — React 18 + TS strict layer.
- `prompts/20-wordpress.md` — WordPress security-first layer.
- `templates/AGENTS.md` — installable project standards with command table.
- `templates/SESSION_STATE.md` — handoff schema.
- `templates/FOLLOWUPS.md` — roadmap schema.

## Found, not fixed

- `AGENTS.md` §5 reserves layers `30–39` and `40–49` with no files yet. Intentional, so new
  prompts slot in without renumbering.
- `AGENTS.md` §1's map and this file's Active list must both be updated when a prompt
  lands; two sources of truth for the same fact will drift.
