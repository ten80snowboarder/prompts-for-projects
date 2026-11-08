# SESSION_STATE

## Status

`DONE`

## Last action

Restructured the prompt set to the `00`–`03` series: wrote `01-vanilla-web.md`,
`02-php-modern.md`, and `03-wordpress.md`, retired `10-react-typescript.md` and
`20-wordpress.md`, extended the Core Protocol with the 500-line and scratchpad rules, and
renumbered `AGENTS.md` §1/§5, `FOLLOWUPS.md`, and this file to match.

## Verified

- `ls prompts/` → `00-core-agent-protocol.md`, `01-vanilla-web.md`, `02-php-modern.md`,
  `03-wordpress.md`. `git rm` removed the two retired files; content survives at
  `0369cb2:prompts/10-react-typescript.md` and `0369cb2:prompts/20-wordpress.md`.
- `wc -l` → `00` 152 (budget 200), `01` 116, `02` 113, `03` 123 (budget 150 each). All under
  the 500-line ceiling.
- Fence count per prompt → 2, with exactly one `text` block opened and closed.
- Section presence per prompt → `When to use`, `Prompt`, `Composition notes`,
  `Revision log`, exactly once each, in order.
- Requirement sweep — `01` contains the 500-line limit, `draft-<task>.md`, WCAG 2.2 AA,
  `min-width` mobile-first, and Flexbox/Grid; `02` contains `declare(strict_types=1)`, PSR-4,
  PDO prepared statements, `htmlspecialchars` with `ENT_QUOTES`, and PHP 8.3; `03` contains
  the `wp-admin`/`wp-includes` ban, `add_action`, `sanitize_*`, `esc_html`, WPCS, and
  `$wpdb->prepare()`.
- Hedging sweep over the three new prompts → no hits.
- Stale-numbering sweep over all files → one hit, the deliberate git-history pointer in
  `FOLLOWUPS.md`.
- `git push origin main` → exit 0; `git ls-remote origin` matches local `HEAD`;
  `git status --short --branch` shows `## main...origin/main` with no dirty paths.

## Checks not run

- No Markdown linter or renderer: this repository ships no tooling and `AGENTS.md` §11
  forbids adding it. Verified by fence, section, and length counts instead.
- No prompt has been executed against a live coding agent. Their behavioral effect remains
  unverified by construction — they are the artifact, not code under test.

## Pending

1. Split `03-wordpress.md` into `20-wordpress-plugins.md` and `21-wordpress-themes.md` when it
   crosses 150 lines (currently 123), and link both from `03`.
2. Write `30-code-review-agent.md` — the mechanical gate for `AGENTS.md` §9 is the largest
   open gap.
3. Rebuild `04-react-typescript.md` from the retired draft against the current anatomy.
4. Field-test one prompt pair against a real task and record observed rule drift as revisions.

## Open questions

- Retiring `10-react-typescript.md` rather than renumbering it to `04` keeps the set at
  exactly three stack prompts, as specified — but leaves React without coverage until `04`
  lands. Reverse it from `0369cb2` if that was the wrong call.
- No `.agentignore` exists; the `node_modules`/`vendor`/`.git` read prohibitions are prose
  only. `.gitignore` covers tool state and scratchpads, nothing else.
- CI is unset. A workflow failing on unbalanced fences, a missing section, or an over-budget
  body would make §9 mechanical, but `AGENTS.md` §11 forbids adding tooling.

## Active files

- `.gitignore` — Mac metadata, tool marker, scratchpad.
- `AGENTS.md` — standards; §1 map and §5 numbering now describe the `00`–`03` series.
- `FOLLOWUPS.md` — renumbered roadmap; moved React to `04` and recorded the retirement.
- `prompts/00-core-agent-protocol.md` — five phases, Three Laws, budget rules.
- `prompts/01-vanilla-web.md` — HTML semantics, WCAG 2.2 AA, mobile-first CSS, ES modules,
  Express.
- `prompts/02-php-modern.md` — PHP 8.3 strict types, PSR-4, PDO, output separation.
- `prompts/03-wordpress.md` — zero core edits, hooks over overrides, WPCS, data security.
- `templates/AGENTS.md`, `templates/SESSION_STATE.md`, `templates/FOLLOWUPS.md` — unchanged.

## Found, not fixed

- `AGENTS.md` §1's map and this file's Active list describe the same files; adding a prompt
  requires editing both or the map drifts.
- `02` and `03` are the same language with incompatible idioms. That is deliberate and stated
  in both files, but nothing prevents loading both at once — the Core Protocol's composition
  rule is the only guard.
