# AGENTS.md — ai-agent-prompts

Repository standards for maintainers and agents working on this prompt library.
Read this file first. It overrides your defaults.

This repository contains no software. It contains **instructions for autonomous coding
agents**. Judge every change by one question: *does this make a coding agent more
predictable, more verifiable, or cheaper to run?*

## 1. Repository map

```
/
├── AGENTS.md            # This file. Standards and structure. Updated when rules change.
├── SESSION_STATE.md     # Handoff state. Overwritten at the end of every session.
├── FOLLOWUPS.md         # Roadmap. Completed items struck, new ideas appended.
├── prompts/             # Finalized system prompts. One file per agent role or stack.
│   ├── 00-core-agent-protocol.md
│   ├── 10-react-typescript.md
│   └── 20-wordpress.md
└── templates/           # Boilerplate Markdown dropped into target projects.
    ├── AGENTS.md
    ├── SESSION_STATE.md
    └── FOLLOWUPS.md
```

Two destinations only: `/prompts/` for executable instructions, `/templates/` for
boilerplate a human installs into another repository. No new root-level directories
without explicit approval.

## 2. The Three Laws

Every prompt in this repository must enforce these. A prompt that omits one is unfinished,
regardless of how good its stack advice is.

| Law | Mechanism | Failure it prevents |
|---|---|---|
| **1. Context before code** | Mandatory Phase 0 read list: `AGENTS.md`, `SESSION_STATE.md`, the files named by the task. Editing in Phase 0 is forbidden. | Agents inventing conventions and hallucinating file paths. |
| **2. Prove it** | Mandatory verification phase: run the command, paste the command and its real exit status. Unrun checks are reported as unrun, never as passes. | "Should work" reports and fake completion. |
| **3. Never stop silent** | Mandatory handoff phase: overwrite `SESSION_STATE.md` with the fixed schema — last action, status, verified, pending, open questions, active files. | Lost context between sessions and repeated work. |

Each law needs a *forced output artifact* (a read, an exit status, a written state file).
A rule the agent can satisfy by remembering instead of by producing something is not a rule.

## 3. Prompt file anatomy

Every file in `/prompts/` follows this order exactly:

1. `# <Title>` — one H1, the prompt's name.
2. A metadata table: Layer, Stack, Composes with, Extends, Excludes, Line budget.
3. `## When to use` — two to four sentences. When this prompt applies, and when it doesn't.
4. `## Prompt` — **exactly one** fenced block containing the copy-paste prompt body.
5. `## Composition notes` — how to combine it with the other layers.
6. `## Revision log` — table of date and change.

The prompt body lives inside a single code fence so it can be copied without dragging
repository commentary into another agent's context. Nothing else goes inside that fence.

## 4. Writing standards

- **Imperative voice.** "Run the typecheck." Not "you should run", "consider running",
  "it's recommended to".
- **Binary rules only.** Every rule is pass/fail and observable. Ban "appropriate",
  "sensible", "reasonable", "as needed", "try to", "be careful".
- **No persona padding.** Do not open with "You are a meticulous senior engineer with 20
  years of experience". State the role in one line and move to behavior.
- **No restating.** If the Core Protocol already covers it, a stack prompt references the
  law by name instead of repeating the paragraph.
- **Verification is always a command.** Never "verify it works". Name the command or the
  observable behavior.
- **Prohibitions beat preferences.** When a mistake is common and costly, forbid it
  explicitly ("Never add `@ts-ignore`") rather than implying it.
- **Token budget.** Core protocol ≤ 200 lines. Stack prompts ≤ 150 lines. Hard ceiling for
  any file: 500 lines (see §6).

## 5. Layering and naming

File names are `<layer>-<slug>.md`. The layer number decides what may appear inside.

| Layer | Scope | May contain |
|---|---|---|
| `00` | Core protocol | Universal behavior only. Zero language or framework names. Exactly one file. |
| `10–19` | Frontend / JS-TS | React, TypeScript, Vue, browser APIs, bundlers. |
| `20–29` | PHP / CMS | WordPress, Laravel, Composer, WP-CLI, WPCS. |
| `30–39` | Backend runtimes & services | Node, Python, Go, Rust, databases, queues. |
| `40–49` | Process agents | Review, migration, test-writing, docs, release. Not stack-bound. |

Reserved numbers are intentional: new prompts slot into an existing range instead of
renumbering files. Never reuse a retired number for a different stack.

## 6. Modularity

A file over 500 lines is too large for reliable sequential processing. When a prompt
approaches the ceiling, split by *phase* or by *surface* (e.g. `21-wordpress-themes.md`,
`22-wordpress-plugins.md`) and link them from the parent's Composition notes. Split by
responsibility, never by arbitrary line count.

## 7. Stack isolation

A prompt for one stack must not carry another stack's rules. No React advice in the
WordPress prompt. No PHP escaping rules in the TypeScript prompt. When two stacks share a
genuine rule (e.g. "escape output"), the shared rule belongs in the Core Protocol if it is
universal, or it is restated in each stack's own vocabulary if the mechanism differs.

## 8. Drafting protocol

Complex, multi-phase prompts are drafted in a scratchpad at the repository root
(`draft-prompt.md`) before touching `/prompts/`. The scratchpad records design decisions,
rejected options, and the self-review gate. It is deleted the moment the finalized file
lands. Never commit a scratchpad. Never finalize directly into `/prompts/` for anything
longer than a single-section prompt.

## 9. Pre-publish review gate

Run this on every prompt before finalizing. Every box must be checked or the file stays a
draft.

- [ ] **Contradictions:** no two rules can be obeyed in conflict. Fix by scoping, not by
      softening.
- [ ] **Authority:** zero hedging words. Every sentence is an instruction or a fact.
- [ ] **Edge cases:** missing context files, failing checks, unavailable tooling,
      unauthorized destructive actions, and ambiguity are each addressed.
- [ ] **Sequential flow:** the body reads top-to-bottom with no forward references. An
      agent must never need a later section to understand an earlier one.
- [ ] **Three Laws present:** context phase, verification phase, handoff phase.
- [ ] **Output artifacts:** every phase names what the agent must produce.
- [ ] **Stack purity:** nothing from another stack leaked in.
- [ ] **Budget:** within the line budget in §4.
- [ ] **Fence integrity:** exactly one fenced prompt block, properly closed.

## 10. Session protocol

At the end of every session, in this order:

1. Overwrite `SESSION_STATE.md` — last action, pending revisions, active files.
2. Update `AGENTS.md` **only** if structure, a template type, or a writing rule changed.
3. Update `FOLLOWUPS.md` — strike completed items, append new prompt ideas.

Do not append to `SESSION_STATE.md`. Overwrite it. It is state, not a log.

## 11. Boundaries

- Read nothing inside `.git`, `node_modules`, `vendor`, build output, or `.DS_Store`.
- Treat `.agentignore` and `.gitignore` as absolute. Never modify ignored paths.
- Never read or write binary assets. Text and Markdown only.
- No code, scripts, config, or dependencies are added to this repository. It is a
  document library. If a task appears to need code, stop and ask.
