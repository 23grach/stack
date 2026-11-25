# Measure

In review mode, fill Metric now from the read-only measures below. Run the done command only in fix mode.

Read and search for repo metrics. Grade outcomes, not claims. Use several trials.

## Repo metrics

Numbers match `SKILL.md`.

| # | Practice | Metric | How |
|---|---|---|---|
| 1 | Nearest sample | Duplicate file hashes; vendored instruction disagreements | Hash counted files; compare a vendored skill with the repo's rules |
| 2 | Exact names and error strings | Repeated user-facing errors; generic names (`utils`, `helpers`, `misc`) | Search each literal |
| 3 | Names are the map | None. Judgment only | — |
| 4 | Lean searchable tree | Committed generated files: count and bytes, including raster derivatives and visual-test baselines | Count files and bytes |
| 5 | File size | Files over 400 lines, and the largest (lines; tokens ≈ bytes/4) | Line counts |
| 6 | Referenced shared modules | Duplicated helper bodies; unused exports | Compare helper bodies; search exports |
| 7 | Readable repo state | Dirty files now | `git status --porcelain` |
| 8 | One schema | Names defined in more than one place | Search names |
| 9 | Instruction file | Broken references. Always-loaded tokens (bytes/4) | Resolve each path. Skip setup paths and tool-owned blocks |
| 10 | One done command | Same steps in the documented command and CI. Pass and runtime, full and scoped, in fix mode | Read scripts. Run only in fix mode |
| 11 | Fresh offline sandbox | Steps to a passing done command. Offline yes, no, or not measured | Fresh worktree, network off if allowed |
| 12 | Hard rules are checked | "never" or "must" with no check. Mixed when checked rules print a fix and the leftover "must" cannot be linted | Read file, search checks |
| 13 | Secrets | Tracked secret-like paths or strings | List tracked files |

No single readiness percentage.

## Default set

These eight, before and after every fix. A split can add a broken reference.

Broken references. Always-loaded tokens. Files over 400, plus the largest. Generated file count and bytes. Duplicate definitions. Done command pass and runtime, full and scoped (fix mode). Offline pass. Unchecked hard rules.

Add the row's own metric when it is not in this list.

## Fix scope

One row is one practice in one place, and one commit. Compare that metric plus the default set. Do not bundle. An unisolated change cannot be attributed.

## Agent outcome eval

Optional, and only if the user asks. It costs time and money.

Take 3 to 5 merged tasks (≤100 lines, ≤5 files). Revert each, restate it, grade with its checks. Hold model, harness, prompt, and tools fixed. Three trials per task per state. Record pass rate, tool calls, tokens, wall time, and edits outside the diff.

- Claim an effect only if most tasks agree and it beats the trial spread. Otherwise write "no measurable change."
- Public history may be in training data. Say so.
- Effects are often small. Do not generalize one suite.
