# SESSION_STATE

Overwrite this file at the end of every session. Do not append. It is current state, not a
log — an agent resuming work reads only this file.

## Status

`<DONE | PARTIAL | BLOCKED>`

## Last action

`<ONE_SENTENCE: what the previous session actually completed>`

## Verified

`<COMMAND` → `RESULT`. One line per check. Include exit status or the failing output.>`

## Checks not run

`<CHECK` → `WHY IT COULD NOT RUN`. Write "none" if every required check ran.>`

## Pending

1. `<NEXT CONCRETE STEP>`
2. `<NEXT CONCRETE STEP, in execution order>`

## Open questions

`<DECISION NEEDED FROM THE HUMAN, with the options and the consequence of each>`

## Active files

- `<PATH>` — `<what changed, one clause>`
- `<PATH>` — `<what changed, one clause>`

## Found, not fixed

`<UNRELATED ISSUE + FILE:LINE. Write "none" if clean. Do not fix these here.>`
