# your-content-worker

A content-generation Claude worker, ICM-structured, fork-ready. Dispatched a brief, produces prose in a configurable voice. MIT licensed.

Live landing page (once you've pushed and enabled Pages): `https://<your-username>.github.io/your-content-worker/`

---

## Why this exists

There are other Claude-worker starter kits. This one is opinionated about five things, each enforced by the architecture rather than by README aspiration:

1. **ICM rigor.** The three always-relevant files — `CLAUDE.md`, `CONTEXT.md`, `STATUS.md` — plus `identity.md`, `rules.md`, `examples.md`, and `reference/`. Not "a CLAUDE.md and hope." Structural, named, enforced.
2. **60-30-10 layer separation.** Infrastructure / Orchestration / AI, in the corrected definition (see `reference/icm-layer-model.md`). AI is the 10%; the other 90% lives in scripts, files, and declarative rules outside Claude. Most kits make Claude the whole stack. This one keeps it in its lane.
3. **Brief-as-contract dispatch.** Clean role boundary between orchestrator and worker. The worker is meant to be called, not driven free-form. The brief is durable, audit-trail-friendly, and complete-or-refused — no "I'll do my best with what's missing."
4. **Pages-ready landing.** Every repo IS its own marketing surface. Push it, enable GitHub Pages from `/docs`, public URL in sixty seconds.
5. **Tied to a real article series.** The architecture is documented in the operator-AI series, starting with "I burned 800,000 tokens on one daily routine." Read the article for the receipts; read this repo for the code that runs the fix.

The article: [Article 1 — destination TBD]. Update this link once the Medium URL is live.

---

## What this worker does

| Job | Input | Output |
| --- | --- | --- |
| Article | Brief naming topic, audience, angle, word count | One article in the configured voice |
| Social post | Brief naming platform, audience, point | One post in the configured voice |
| Caption | Brief naming asset, audience, CTA | One or several captions in the configured voice |
| Script | Brief naming format, duration, point | One script marked for performance |
| Sequence | Brief naming campaign, cadence, arc | A series of artifacts, each in the configured voice |

Full job definitions in [identity.md](identity.md). Routing logic in [CONTEXT.md](CONTEXT.md).

See [examples/](examples/) for a generated sample — a paired brief ([sample-brief.md](examples/sample-brief.md)) and the prose this worker produced from it ([sample-output.md](examples/sample-output.md)), run end-to-end in the default voice. Fork, edit `reference/voice.md`, re-dispatch the same brief, and the mechanism speaks in your voice instead.

---

## Five-minute setup

### 1. Fork or clone

```bash
git clone https://github.com/NFTYoginis/your-content-worker.git
cd your-content-worker
```

Or click "Fork" on GitHub if you want your own copy under your account.

### 2. Open in a Claude session

Either:

- **Claude Code** in the terminal: `cd` into the folder, run `claude`. The worker reads `CLAUDE.md` as its entry point.
- **Claude Project** (claude.ai): create a project, upload the folder. Same entry point.

### 3. Edit `reference/voice.md`

The repo ships with a working default voice so the worked example dispatches as-is. Replace the default with your own voice rules before serious use:

- Tone — 2-4 sentences.
- Sentence rhythm — short by default? mixed? Read aloud cleanly?
- Vocabulary — your audience's actual terms; your banned-word list.
- "What this voice sounds like" — two paragraphs of your real published writing.
- "What this voice does NOT sound like" — a counter-example close to what you're trying not to write.

Five edits. The voice file walks you through them.

### 4. Write your first brief

Copy `briefs/_BRIEF-TEMPLATE.md` to `briefs/<today>-<slug>.md`. Fill the six sections:

1. What to produce
2. Audience
3. Format and constraints
4. Voice override (or default)
5. Success criteria
6. Refusal context (if relevant)

The brief should fit on one screen. If yours is sprawling, you're orchestrating in the wrong place — split it.

### 5. Dispatch

Paste this into the Claude session:

```
Read the brief at briefs/<your-filename>.md and execute.
```

That's the entire dispatch. The worker takes it from there: reads STATUS, reads the brief, reads the voice, runs the pre-flight checklist, produces the artifact, self-verifies, updates STATUS.

---

## File map

```
your-content-worker/
├── README.md             ← you are here
├── CLAUDE.md             ← worker entry point (first read every session)
├── CONTEXT.md            ← routing / load logic — the 30% orchestration made explicit
├── STATUS.md             ← first read, last write (you maintain)
├── identity.md           ← who the worker is, who it serves, what it does
├── rules.md              ← always / never / refusal gates / escalation
├── examples.md           ← worked examples — study these to understand worker behavior
├── briefs/
│   ├── _BRIEF-TEMPLATE.md       ← copy this for each dispatch
│   └── 2026-05-14-example.md    ← paired with the worked example in examples.md
├── reference/
│   ├── icm-layer-model.md       ← 60-30-10, corrected definition, attributed to Van Clief
│   ├── dispatch-pattern.md      ← orchestrator-worker boundary, explained
│   └── voice.md                 ← YOU EDIT THIS — the worker's voice config
├── docs/
│   └── index.html               ← Pages-ready landing page
├── LICENSE                      ← MIT
└── .gitignore
```

---

## What this worker doesn't do

The full list is in [rules.md](rules.md). Headline items:

- Doesn't orchestrate. Doesn't pick its own topics, set its own deadlines, or dispatch other workers.
- Doesn't invent facts. If a brief asks for a claim the brief doesn't ground, the worker writes a question file and stops.
- Doesn't write in an unconfigured voice. Empty `reference/voice.md` or unedited placeholder triggers a refusal.
- Doesn't impersonate real third parties without consent confirmation in the brief.
- Doesn't produce content for high-harm domains without explicit operator authorization.
- Doesn't extend scope. One brief, one artifact. No bonus material.

When any refusal gate fires, the worker writes `briefs/questions/<slug>-question.md` with verbatim quotes from the brief and the specific information needed to proceed. Then it stops.

---

## Push to GitHub + enable Pages

```bash
# 1. Initialize the repo (if you haven't already)
git init
git add .
git commit -m "Initial commit"

# 2. Create the remote and push (assumes gh CLI authenticated)
gh repo create <your-username>/your-content-worker --public --source=. --remote=origin --push

# 3. Enable GitHub Pages serving from /docs
gh api repos/<your-username>/your-content-worker/pages \
  -X POST \
  -f "source[branch]=main" \
  -f "source[path]=/docs"

# 4. Wait ~30-60 seconds, then verify
open https://<your-username>.github.io/your-content-worker/
```

If `gh` CLI isn't authenticated, use the GitHub web UI: Settings → Pages → Source = `main` branch, `/docs` folder → Save.

---

## The series

This repo is one of three in the operator-stack series. Same architecture, different domains:

- **your-content-worker** (this repo) — prose
- **your-design-worker** — images, HTML previews, social variants (coming next)
- **your-animation-worker** — voice-to-video MP4 via Remotion (coming after design)

Cross-links will be added here once the sibling repos ship.

---

## Article series

The architecture is documented in:

- **Article 1** — "I burned 800,000 tokens on one daily routine. Here's the architecture that killed it." [Medium URL TBD]

Future articles will link from this section as they publish.

---

## License

MIT. See [LICENSE](LICENSE). Replace `<YOUR NAME OR HANDLE>` in the copyright line when you fork.

## Acknowledgments

- The 60-30-10 layer framework is from Jake Van Clief's ICM (Internal Coherence Maximization) teaching.
- The `docs/index.html` Pages-ready discipline is adapted from the existing public landing-page pattern in this maintainer's earlier worker repositories.

---

Last updated: 2026-05-14.
