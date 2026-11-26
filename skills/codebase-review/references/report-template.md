# Report template

Commands here are examples, not a required stack. The reply is only this report, starting with the verdict line. Columns: Sev, What's wrong, How to fix it. List only problems. Sort by severity: Critical, High, Medium, Low. Write each problem and fix in short sentences a non-specialist can follow. File names and commands stay in code spans. When one fix also solves another problem, put both in that row.

## EXAMPLE DATA

Fictional `acme-notes`. Do not copy it.

> **Verdict:** A new copy of the project cannot be installed. Fix that first. 1 Critical, 2 High, 1 Medium, 1 Low.

| Sev | What's wrong | How to fix it |
|---|---|---|
| Critical | A new copy of the project cannot be installed. There is no `package-lock.json`, and no file says which command installs dependencies. | Add `package-lock.json` and write the install command in `AGENTS.md`. |
| High | `package.json` has `npm test`, but no file says to run it after a change. | Write `npm test` in `AGENTS.md`. |
| High | The fields of a note are written out in both `src/note.ts` and `src/api.ts`. | Keep the fields in `src/note.ts` and use them from `src/api.ts`. |
| Medium | The sentence for an empty list is copied in `src/home.ts`, `src/search.ts`, and `src/archive.ts`. The copy in `src/archive.ts` is out of date. | Keep the copy in `src/home.ts` and use it from the other two files. |
| Low | `src/editor.ts` is 812 lines. The other source files are short. | Split `src/editor.ts` into smaller files with clear names. |

#### A new copy cannot be installed

- **Evidence:** no `package-lock.json`. `README.md` and `AGENTS.md` do not name an install command.
- **Change:** Add `package-lock.json` and write the install command in `AGENTS.md`.

#### The test command is not written down

- **Evidence:** `package.json:8` defines `npm test`. `AGENTS.md` and `README.md` never name it.
- **Change:** Write `npm test` in `AGENTS.md`.

#### Note fields are written twice

- **Evidence:** `src/note.ts:4` and `src/api.ts:18`.
- **Change:** Keep the fields in `src/note.ts` and use them from `src/api.ts`.

### Fix mode

Add this only after the named rows are changed. Say what changed. If the done command fails, say that the row was reverted.

`HEAD before: a1b2c3d · branch: review-fixes · after: e4f5g6h · done command: pass`

Placeholder SHAs.
