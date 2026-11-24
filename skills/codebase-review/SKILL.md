---
name: codebase-review
description: Scores a repository for agent-readiness and AI readiness, and proposes changes without editing the target. Covers AGENTS.md, CLAUDE.md, naming, and repo layout.
---

# Codebase review

Review mode is the default. Score the rubric and report. Do not modify the target, apply fixes, write instruction files, or run the suite. Scoring those files and the done command is in scope. Fix mode is opt-in and runs only on rows the user names.

## Input

A readable path. Optional focus: a directory, module, or area. None means the whole target.

## Steps

1. Stay read-only. Do not create, edit, format, delete, or commit in the target.
2. If the path is a git checkout, record `git status --porcelain` and `git rev-parse HEAD`. Otherwise note that.
3. Map the focus: layout, languages, modules, entry points, instruction files, schemas, scripts, and git history.
4. Score all 13 practices. Cite paths, names, and counts.
5. Write the report in the format below. Use `references/report-template.md` for the shape.
6. In review mode, repeat step 2. Stop if it changed. With no git checkout, confirm you wrote nothing.

## Scores

- **Good** — holds across the focus.
- **Mixed** — partly holds; say what's missing.
- **Weak** — missing or mostly fails where it applies.
- **N/A** — does not apply.

## Rubric

1. **Nearest sample.** Agents copy the nearest, most frequent example, so keep one current sample next to the work. Weak: a stale or competing copy sits beside it. A vendored or locked copy counts only where it disagrees with the instruction file.
2. **Exact names and error strings.** Functions, variables, and errors need unique names, not `utils`, `helpers`, or `Card2`. Console output, and UI copy if any, needs a stable phrase. Weak: a generic name, or an error with no stable phrase.
3. **Names are the map.** Folder, file, and symbol names should show where a feature lives. Use the same words in the feature name, files, functions, and UI copy, if any. Weak: the names do not match the words used to ask for it.
4. **Lean searchable tree.** A hit enters context even if the file stays closed. Keep generated files, build output, logs, large data, old exports, and second experiments out. A committed file is still searched. Generated text (for example JSON) counts. Byte-for-byte baselines are N/A. Weak: that noise is committed. A binary counts only when a small text or vector master in the target can rebuild it.
5. **File size.** Count source, tests, and styles, if any. Skip docs, generated or data files, lockfiles, fixtures, and snapshots. Rule of thumb: Weak over 400 lines, Good under 250, 250–400 between.
6. **Referenced shared modules.** Import a shared module at each use and export a clear signature. Weak: the same helper is written again in two or more places.
7. **Readable repo state.** The working tree holds the current task. Commits are small and say what changed. One default branch needs no written naming rule. N/A with no git history. Weak: unrelated edits share the tree, or messages do not say what changed.
8. **One schema.** One type or model plus its validator in one module counts (a TypeScript type and parser, a Pydantic model, a Go struct and validation). A doc or table of the same fields does not. Pasted values are practice 9. Weak: those fields are declared again in another type, struct, or validator.
9. **Instruction file.** Short, at the root, plus one per project; the closest wins (https://agents.md/). Say only what the code cannot. Point from a file the agent always loads, instead of pasting a guide, sample, or values. Every path, script, and command it names must exist. Versioned docs for a fast-moving dependency are optional. No file: Weak only with unusual commands, required env vars, or hard rules; otherwise Mixed, and file-only parts are N/A. Weak: missing where those facts exist, or it pastes, or a named path or command is missing. A skill repeating its own commands is not Weak.
10. **One done command.** Document the done command (a test, a type check, or lint) and a fast check for one file or package. Good when `AGENTS.md`, or `README` if none, and the required CI check name it. Subset jobs do not change the score. Do not add or run it. Weak: no done command is documented.
11. **Fresh offline sandbox.** Read only. Do not run tests. Good: a committed lockfile, a pinned toolchain or runtime file, and one documented setup command. Weak: no lockfile, setup is unwritten, or tests or setup call live URLs or need secrets missing from an env example.
12. **Hard rules are checked.** Each "never" or "must" in the instruction file has a lint, test, hook, or CI step that prints the rule and the fix. N/A with no instruction file. Weak: the rule is only prose, or the check prints only an exit code.
13. **Secrets.** Keep secrets and never-read paths out of search, under a name the agent recognizes (for example `.env`). Weak: a secret is committed, or the ignored path is not recognizable.

## Fix mode

The user must name rows, such as "fix 1 and 3". Load `references/measure.md`. Do not push, open a pull request, or merge unless asked.

1. Review. Write the report first.
2. Pick. Change only the named rows.
3. Baseline. On a clean HEAD, record the default metrics, each row's metric, and HEAD.
4. Branch. New branch or worktree. Leave the default branch untouched.
5. Change. One commit per row: the smallest change that moves that metric.
6. Re-measure. Same commands, same machine, then the done command. If it fails, revert that row and say so.
7. Report. Before/after table. Every improved claim cites a number.

## Report

Critical: Weak on 10, 11, or 13, or a broken command in the instruction file. High: any other Weak. Medium: Mixed across several files. Low: Mixed in one place, or one file that contradicts an otherwise Good score. Sort by severity, then by effort, smallest first.

Follow `references/report-template.md`. One verdict line, then a table: Sev, Practice, Finding, Fix, Effort, Metric now. Detail blocks for Critical and High only: Evidence, Change, Measure. Under the table, one line per N/A with the reason. In fix mode, add the before/after table and the HEAD line.
