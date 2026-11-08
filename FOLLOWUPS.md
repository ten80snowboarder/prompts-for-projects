# FOLLOWUPS — ai-agent-prompts

Roadmap. Strike items with `- [x]` when they land in `/prompts/` or `/templates/`.
Keep entries as one line naming the outcome; details belong in the prompt itself.

## Now

- [ ] **`20-wordpress-plugins.md`** — split post types, REST routes, admin screens,
      capabilities, and hooks out of `03-wordpress.md` when it crosses 150 lines.
- [ ] **`21-wordpress-themes.md`** — split templates, enqueueing, `theme.json`, and block
      patterns out at the same time. Both link back from `03`.
- [ ] **`30-code-review-agent.md`** — a read-only agent that audits a diff or a new prompt
      file against `AGENTS.md` and cites file and line for every violation. No verification
      phase; a review agent proves nothing. This mechanical gate is the largest open gap.

## Next

- [ ] **`04-react-typescript.md`** — React 18 + TypeScript strict. A retired draft exists in
      git history at `0369cb2:prompts/10-react-typescript.md`; rebuild it against the current
      anatomy rather than resurrecting the old numbering.
- [ ] **`05-nextjs-app-router.md`** — server/client boundary, data fetching, caching, route
      handlers. Must not repeat generic React rules.
- [ ] **`06-vue-typescript.md`** — Composition API, typed `defineProps`/`defineEmits`, Pinia
      boundaries.
- [ ] **`07-astro-svelte.md`** — static-first, islands, hydration boundaries.
- [ ] **`08-node-typescript-service.md`** — layered services, boundary validation, graceful
      shutdown, structured logging. Distinct from `01`'s Express section, which stays
      page-serving.
- [ ] **`09-laravel.md`** — Eloquent relationships, queues, policies, Artisan, Pest. Referenced
      from `02` as its surface split.

## Ideas

- [ ] **`10-shopify-liquid.md`** — theme limits, section schemas, no core edits.
- [ ] **`11-drupal.md`** — config export discipline, service container, no `db_query`.
- [ ] **`12-python-service.md`** — typing discipline, uv/virtualenv, pytest, no bare `except`.
- [ ] **`13-go-service.md`** — error wrapping, context propagation, table-driven tests.
- [ ] **`14-rust-service.md`** — ownership-driven refactors, clippy gate, no `unwrap` in
      library paths.
- [ ] **`22-react-testing.md`** — what to assert and what never to assert if RTL guidance
      outgrows `04`.
- [ ] **`31-migration-agent.md`** — staged upgrades, proving each stage, never mixing a
      migration with a feature.
- [ ] **`32-test-backfill-agent.md`** — adds tests to untested code without changing behavior;
      the diff must contain tests only.
- [ ] **`33-docs-agent.md`** — documents a diff; forbids documenting behavior absent from the
      code.
- [ ] **`34-incident-response.md`** — read-only triage: evidence first, one hypothesis at a
      time, never patch during triage.
- [ ] **`templates/PR_DESCRIPTION.md`** — reviewer-facing PR body that demands verification
      evidence.
- [ ] **Standards gap:** decide whether prompt metadata must declare its own verification
      command set, so composed layers cannot emit conflicting gates.
- [ ] **Enforcement gap:** `.gitignore` covers scratchpads, but nothing machine-checks fence
      balance, required sections, or line budgets. `AGENTS.md` §11 forbids adding tooling, so
      this stays manual until that rule changes.

## Done

- [x] **Repository bootstrap** — `AGENTS.md`, `SESSION_STATE.md`, `FOLLOWUPS.md`,
      `/prompts`, `/templates` standards established.
- [x] **`00-core-agent-protocol.md`** — universal five-phase protocol enforcing the Three
      Laws, plus the 500-line budget and scratchpad rules.
- [x] **`01-vanilla-web.md`** — static sites, frontend-only apps, Express.
- [x] **`02-php-modern.md`** — PHP 8.3+, Composer, PSR-4, PDO, Laravel, Symfony.
- [x] **`03-wordpress.md`** — zero core edits, hooks over overrides, WPCS, `$wpdb->prepare`.
- [x] **`templates/AGENTS.md`**, **`templates/SESSION_STATE.md`**,
      **`templates/FOLLOWUPS.md`** — installable boilerplate.
- [x] **Retired `10-react-typescript.md`** and **`20-wordpress.md`** — numbering superseded by
      the `01–03` series; content recoverable from commit `0369cb2`.
