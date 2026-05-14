# CONTEXT.md — routing and load logic

This file is the 30% orchestration layer made explicit. It tells the worker which reference files to load for which kind of dispatch, so context doesn't get loaded speculatively.

`CLAUDE.md` is the entry point — read first. This file is referenced from there.

## Why this file exists

In the 60-30-10 framework (see `reference/icm-layer-model.md`), Orchestration is 30% of the workflow's value: templates, rules, decision logic, the connective tissue that makes raw tools useful for a specific job. Most starter kits put orchestration logic *inside* Claude's reasoning — "decide which file to read." That's expensive and inconsistent.

This file moves that decision out of Claude's working context and into a declarative rule list. Worker reads this once, applies the rule, loads only what the rule says to load. No speculation.

## The dispatch types this worker handles

| Dispatch type | What it produces | Files to load (in this order) |
| --- | --- | --- |
| **Article / long-form** | 500-2000 word article in configured voice | `reference/voice.md` → the brief → any domain reference the brief names |
| **Social post** | Single post (LinkedIn / X / blog comment) in configured voice | `reference/voice.md` → the brief → previous-post examples if the brief names a campaign |
| **Caption** | Image or video caption (one or several variants) in configured voice | `reference/voice.md` → the brief |
| **Script** | Voice-over or short-form video script in configured voice | `reference/voice.md` → the brief → any product/audience reference |
| **Sequence** | Multi-part series (email sequence, post series) in configured voice | `reference/voice.md` → the brief → the campaign reference if one exists in `reference/` |

Add a row above when you (the operator) start dispatching a new kind of work to this worker. Don't let the routing live in Claude's head — declare it here.

## What never gets loaded automatically

- The full `briefs/` history. Each dispatch is grounded by ONE brief. Loading prior briefs is speculative context — exactly the mistake that burns tokens.
- Examples from `examples.md` — that file is for *you* to study the worker's behavior, not for the worker to study its own past output. Past output is usually noise during a fresh dispatch.
- Output files from prior dispatches. Same reason.
- Any file under `output/` — write-only from the worker's perspective.

The worker reads what the brief requires, and nothing more. If a brief asks the worker to "write a follow-up to last week's post," the brief itself names that prior post; the worker reads only the named file, not the whole archive.

## Slice-not-file Read habit (mechanical rule)

For any reference file longer than 100 lines:

1. `grep -n "<section-header>" reference/<file>.md` — find the line number.
2. `Read reference/<file>.md` with `offset=<line>` and `limit=<lines-needed>` — pull only the slice.

Never `Read` a 600-line reference file to find the 30 lines that matter. That's the single most expensive habit in this kind of build (Article 1, Mistake 2).

## When the operator configures a new dispatch type

1. Add a row to the dispatch-type table above.
2. Decide which reference files load by default. Be miserly.
3. If a new reference file is needed (campaign notes, audience research, product catalog), add it under `reference/` with a clear filename.
4. Add a one-line note to `STATUS.md` so the worker knows the routing changed.

## Open routing question (for the operator, not the worker)

If a brief names a dispatch type that isn't in the table above, the worker writes a question file at `briefs/questions/<slug>-question.md` and stops. It does not invent a routing decision on the fly. Add the row first, dispatch second.

---

Read this file when in doubt about what to load. Read `CLAUDE.md` first.
