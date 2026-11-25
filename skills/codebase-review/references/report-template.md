# Report template

Commands here are examples, not a required stack. Columns: Sev, Practice, Finding, Fix, Effort, Metric now. Effort: S is one file, M is one module, L crosses the repo. In review, Metric now is a read-only measure. The done command runs only in fix mode.

## EXAMPLE DATA

Fictional `acme-notes`. Do not copy it.

> **Verdict:** Work is possible here, but not verifiable offline. Fix the done command and the instruction file first. 2 Critical, 2 High, 3 Medium, 1 Low.

| Sev | Practice | Finding | Fix | Effort | Metric now |
|---|---|---|---|---|---|
| Critical | 9 Instruction file | `AGENTS.md:12` `npm run verify` is missing | Point at the real test | S | 3 broken refs |
| Critical | 11 Fresh offline sandbox | A test calls `api.acme.dev` | Fake the client | M | offline: fail |
| High | 5 File size | Editor file is 812 lines | Split it | M | 4 over 400 |
| High | 8 One schema | `Note` defined twice | Keep one | S | 3 duplicates |
| Medium | 4 Lean searchable tree | `dist/` committed | Untrack and ignore | S | 14 files, 2.1MB |
| Medium | 12 Hard rules are checked | Never-import has no check | Add a boundary check | S | 2 unchecked |
| Medium | 10 One done command | No scoped check | Document one file | S | scoped missing |
| Low | 2 Exact names and error strings | `utils2.ts` | Rename it | S | 1 generic |

#### 9. Instruction file: Critical

- **Evidence:** missing script, two missing paths.
- **Change:** point at the real test. Delete the dead lines.
- **Measure:** broken refs 3, target 0.

Same block for 11, 5, and 8.

### Fix mode: before/after

| Row | Metric | Before | After | Delta | Done cmd |
|---|---|---|---|---|---|
| 9 | Broken refs | 3 | 0 | −3 | pass |
| 11 | Offline pass | fail | pass | yes | pass |
| — | Generated files | 14 files, 2.1MB | 14 files, 2.1MB | 0 | — |
| — | Always-loaded tokens | 1140 | 980 | −160 | — |

`HEAD before: a1b2c3d · branch: review-fixes · after: e4f5g6h · outcome eval: not run`

Placeholder SHAs. A dash is a default-set metric.
