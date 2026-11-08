# FOLLOWUPS — ai-agent-prompts

Roadmap. Strike items with `- [x]` when they land in `/prompts/` or `/templates/`.
Keep entries as one line naming the outcome; details belong in the prompt itself.

## Now

- [ ] **`21-wordpress-plugins.md`** — split plugin concerns out of the WordPress prompt
      once it approaches its line budget: custom post types, REST routes, admin screens.
- [ ] **`11-react-testing.md`** — separate the testing doctrine (what to test, what never
      to assert on) if React Testing Library guidance outgrows the React prompt.
- [ ] **`40-code-review-agent.md`** — a read-only agent that reviews a diff against
      `AGENTS.md` and reports violations without editing. No verification phase; a review
      agent proves nothing.

## Next

- [ ] **`12-nextjs-app-router.md`** — server/client component boundary, data fetching,
      caching, and route handlers. Must not repeat generic React rules.
- [ ] **`13-vue-typescript.md`** — Composition API, `defineProps`/`defineEmits` typing,
      Pinia boundaries.
- [ ] **`22-laravel.md`** — Eloquent vs query builder, form requests, policies, migrations
      safety, Pest/PHPUnit verification.
- [ ] **`30-node-typescript-service.md`** — layered services, input validation at the
      boundary, graceful shutdown, structured logging.
- [ ] **`31-python-service.md`** — typing discipline, virtualenv/uv, pytest, no bare
      `except`.
- [ ] **`41-migration-agent.md`** — framework or major-version upgrades: staged diffs,
      proving each stage, never mixing a migration with a feature.

## Ideas

- [ ] **`42-test-backfill-agent.md`** — adds tests to untested code without changing
      behavior; the diff must contain tests only.
- [ ] **`43-docs-agent.md`** — updates docs from a diff; forbids documenting behavior that
      is not in the code.
- [ ] **`14-astro-svelte.md`** — static-first stacks, islands, hydration boundaries.
- [ ] **`23-shopify-liquid.md`** — theme limits, section schemas, no core edits.
- [ ] **`24-drupal.md`** — config export discipline, service container, no `db_query`.
- [ ] **`32-go-service.md`** — error wrapping, context propagation, table-driven tests.
- [ ] **`33-rust-service.md`** — ownership-driven refactors, clippy gate, no `unwrap` in
      library paths.
- [ ] **`50-database-migrations.md`** — reversible migrations, backfill strategy, proving
      on a restored copy instead of production.
- [ ] **`90-incident-response.md`** — read-only triage agent: gather evidence, propose one
      hypothesis at a time, never patch during triage.
- [ ] **`templates/PR_DESCRIPTION.md`** — reviewer-facing PR body template that demands
      verification evidence.
- [ ] **Standards gap:** decide whether a prompt must declare its own verification command
      set in metadata, so composed prompts never emit contradictory gate commands.

## Done

- [x] **Repository bootstrap** — `AGENTS.md`, `SESSION_STATE.md`, `FOLLOWUPS.md`,
      `/prompts`, `/templates` standards established.
- [x] **`00-core-agent-protocol.md`** — universal five-phase protocol enforcing the Three
      Laws.
- [x] **`10-react-typescript.md`** — React 18 + TS strict stack layer.
- [x] **`20-wordpress.md`** — child theme / custom plugin discipline, security-first.
- [x] **`templates/AGENTS.md`**, **`templates/SESSION_STATE.md`**,
      **`templates/FOLLOWUPS.md`** — installable boilerplate.
