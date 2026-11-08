# AGENTS.md — `<PROJECT_NAME>`

Operating rules for autonomous agents in this repository. Read this file before touching
any code. It overrides an agent's defaults.

Replace every `<PLACEHOLDER>` before installing. Delete sections that do not apply rather
than leaving them as `TBD` — an empty rule is worse than no rule.

## 1. What this project is

`<ONE_PARAGRAPH: what it does, who uses it, what is out of scope.>`

## 2. Commands

Agents run these verbatim. Do not guess a command; if one is missing, add it here first.

| Purpose | Command |
|---|---|
| Install | `<INSTALL_CMD>` |
| Dev server | `<DEV_CMD>` |
| Typecheck / compile | `<TYPECHECK_CMD>` |
| Test (focused) | `<TEST_CMD> <path>` |
| Test (full) | `<FULL_TEST_CMD>` |
| Lint | `<LINT_CMD>` |
| Build | `<BUILD_CMD>` |

## 3. Structure

```
<DIR_TREE: annotate each top-level directory with its responsibility in one line.>
```

Where new code goes:

- `<FEATURE_OR_MODULE>` → `<PATH>`
- Tests → `<PATH>` (mirror the source path)
- Shared utilities → `<PATH>` (only after a second caller exists)

## 4. Conventions

- Language/runtime: `<VERSION>`
- Formatting: `<FORMATTER_AND_CONFIG>`
- Naming: `<FILE_AND_SYMBOL_CONVENTIONS>`
- Error handling: `<PATTERN>`
- Logging: `<PATTERN>`

Rules that are easy to get wrong:

- `<RULE: the specific thing agents break here>`
- `<RULE>`

## 5. The Three Laws

Non-negotiable in this repository.

1. **Context before code.** Read this file, `SESSION_STATE.md`, and the files the task
   names before editing anything.
2. **Prove it.** Run the verification command for what you changed and report its real
   result. Never claim a check passed without the output. Never describe a check you did
   not run.
3. **Never stop silent.** Overwrite `SESSION_STATE.md` before ending the session, using the
   schema in `templates/SESSION_STATE.md`.

## 6. Boundaries

Forbidden without explicit human approval:

- `<DESTRUCTIVE_OR_EXTERNAL_ACTION>` (e.g. `git push`, deploy, migration on shared data)
- Adding or upgrading dependencies
- Editing `<GENERATED_OR_VENDORED_PATH>`
- Changing `<PROTECTED_AREA: auth, billing, schema>`
- Reading or writing `.env*`, credentials, or customer data

Never read `.git`, `node_modules`, `vendor`, build output, or binary assets.

## 7. Definition of done

- [ ] Requested behavior implemented, nothing extra.
- [ ] Verification command run; result known.
- [ ] `SESSION_STATE.md` updated.
- [ ] No unrequested changes in the diff.
