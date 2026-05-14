# reference/icm-layer-model.md

## The 60-30-10 layer framework

From ICM (Internal Coherence Maximization), Jake Van Clief's framework for thinking about where the value of an AI workflow actually lives. A real workflow is three layers, by share of value:

- **60% Infrastructure** — databases, file storage, routing, approval chains. Systems that already exist and shouldn't be replaced.
- **30% Orchestration** — templates, rules, decision logic. The connective tissue that makes raw tools useful for a specific context.
- **10% AI** — summarize, extract, generate, compare against a standard.

AI is the *smallest* layer. Most of the value lives in the other two.

This is the corrected definition. If you've seen 60-30-10 framed as a context-budget split ("60% always-loaded, 30% task-scoped, 10% on-demand") — that's a different concept and not what Van Clief teaches. The numbers happen to match; the layers don't.

## How this worker maps to the framework

| Layer | What it is in this repo |
| --- | --- |
| **60% Infrastructure** | The file system. The orchestrator's calendar (your own, outside this repo). The git history of `output/`. The platforms where you publish the artifact. Claude doesn't touch most of this. |
| **30% Orchestration** | `CLAUDE.md` + `CONTEXT.md` + `STATUS.md` + `rules.md` + `briefs/_BRIEF-TEMPLATE.md` + the routing table. Declarative rules that tell the worker what to do, what to load, what to refuse. Read by Claude, but not derived by Claude. |
| **10% AI** | The actual prose generation. Take the brief + the voice + the domain context → produce one artifact. This is the only step where Claude's reasoning is load-bearing. |

The crucial discipline: do not let the 10% layer absorb work that belongs in the 60% or 30%. Symptoms of the 10% absorbing too much:

- The worker re-derives routing decisions every dispatch (should be declarative in `CONTEXT.md`).
- The worker re-reads its own past output to "remember the voice" (should be a stable rule in `reference/voice.md`).
- The worker formats and saves the artifact itself rather than handing it back for the operator's filesystem move (should be infrastructure).

When the 10% absorbs the other layers, token cost explodes and output gets inconsistent. The fix is always: move that decision out of Claude and into a file or a script.

## Worked example from Article 1

The operator's daily content routine was costing roughly 800,000 tokens per morning. Same routine every day, same outputs. The orchestrator (then a single Claude session doing everything) was:

- Reading whole reference files when it needed a slice — infrastructure leak into AI.
- Re-deriving worker boundaries every morning — orchestration leak into AI.
- Drafting partial artifacts before dispatching — AI doing work that belonged to the dispatched worker.

After applying the role boundary and slicing reads, the same daily routine cost roughly 8,000-10,000 tokens. Two orders of magnitude. Same outputs. Same quality.

The savings weren't from a smarter model. They were from removing work the orchestrator was never supposed to be doing.

## Attribution and further reading

The 60-30-10 layer framework comes from Jake Van Clief's ICM teaching. We don't reproduce the source material here — go to the source.

If you want the practical version applied to a solo operator's content workflow, see Article 1 of the operator-AI series ("I burned 800,000 tokens on one daily routine") — link in the README.

## Why this file exists in this repo

You forked this starter to put it to work. The 60-30-10 framework is the rationale for everything in the architecture — why `CLAUDE.md` is short, why `CONTEXT.md` exists as a separate file, why the worker reads in slices, why the brief is a contract, why scope extension is a bug.

When you find yourself tempted to "just let Claude figure it out" — re-read this file. The architecture exists to keep AI in its 10% lane.

---

Last updated: 2026-05-14.
