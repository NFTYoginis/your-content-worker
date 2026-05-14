# reference/voice.md

This is the file the worker reads every dispatch to know how to sound.

You (the reader who forked this repo) edit this file with your own voice rules. The worker uses whatever's here. The default below is a working starter — generic, neutral, runnable as-is — so the worked example in `examples.md` produces real output the first time you dispatch. **Replace it with your own voice once you've seen the worker behave.**

Marker for the operator: if the worker stops with "voice file is still showing the placeholder," it means this file matches the default below verbatim. Even small edits — your own one-paragraph rules in the same shape — flip the worker to "configured." If you want the default to count as configured for your fork, delete this marker block and the line "Replace with your own voice…" above. The worker's gate checks for that line.

---

## Voice rules — default working set

### Tone

Direct. Plain. Sentence-level claims, not paragraph-level claims. If you can't say it in one sentence, you don't believe it yet — keep thinking before you write it.

Not corporate. Not influencer. Not academic. Closer to a senior practitioner emailing a peer: assumes the reader is smart, doesn't over-explain, doesn't perform expertise. No "let's dive in." No "unlock the power of." No "in today's fast-paced world."

### Sentence rhythm

Short sentences as a default. Longer sentences when the idea genuinely needs them — usually when two clauses are being weighed against each other. Vary the rhythm; don't write twelve short sentences in a row.

Read drafts aloud (literally or in your head). A sentence that doesn't read aloud cleanly doesn't ship.

### Vocabulary

Concrete over abstract. Specific over general. "Cut deploys from 14 minutes to 90 seconds" not "dramatically improved deployment efficiency."

Industry terms when the audience uses them; plain English when the audience doesn't. If a term needs a footnote, the audience is wrong or the term is wrong — pick one.

No buzzwords used un-ironically: "synergy," "leverage" (as a verb), "scalable," "robust," "ecosystem" (unless biology), "thought leader," "10x," "best-in-class."

No emoji as a substitute for the sentence the emoji is replacing. The emoji can sit alongside; it can't carry the meaning.

### What this voice sounds like

> The orchestrator was studying the workers before dispatching them, as if it needed to understand the work in order to delegate it. It doesn't. The brief is a contract. The worker reads its own context. The orchestrator's job is to point — this row, that template, those constraints — not to internalize the worker's craft.

### What this voice does NOT sound like

> In today's rapidly evolving landscape of AI-powered workflows, savvy operators are unlocking next-level productivity by leveraging multi-agent architectures. Discover how a strategic dispatch pattern can revolutionize your content stack and 10x your output.

If your draft starts drifting toward the second example, stop and re-read this file.

---

## TODO for the operator (edit these before serious dispatch)

- [ ] Replace the "Tone" section above with your brand's tone in 2-4 sentences.
- [ ] Replace the "Sentence rhythm" section with your rhythm preferences (or keep the default if it fits).
- [ ] Replace the "Vocabulary" section with your audience's actual terms and your banned-word list.
- [ ] Replace the "What this voice sounds like" example with two paragraphs of your own real published writing.
- [ ] Replace the "What this voice does NOT sound like" example with a counter-example that's close to what you're trying NOT to write.

Once those five edits are made, this file is yours. The worker will read it on every dispatch and write in it.

## What NOT to put in this file

- Brand history, founder bio, company mission. (Different file: write a `reference/brand-context.md` if you need it.)
- Audience research. (Different file: `reference/audience.md` per persona.)
- Product catalog. (Different file: `reference/products.md`.)
- Style guide for visual assets. (Different worker: `your-design-worker`.)

Voice = how the words sound. Anything else lives in its own reference file.

---

Last updated: 2026-05-14 (default working set; replace with your own rules).
