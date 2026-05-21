# Brief — 2026-05-21-overlap-how-it-works

A generated sample, run end-to-end through this worker exactly as a forker would dispatch it. Paired with `examples/sample-output.md`. Deliberately industry-neutral — a fictional SaaS, no real brand — so the example shows the mechanism in the default configurable voice, not any one operator's domain.

The output was produced against the **default working voice** in `reference/voice.md`. Fork the repo, edit that file with your own voice, re-dispatch this same brief, and you'll see the mechanism speak in your voice instead.

---

## 1. What to produce

One 500-700 word "how it works" explainer for the Overlap marketing site. Overlap is a meeting-scheduler for distributed teams that finds the working-hours window everyone actually shares, instead of making people do timezone math in their heads. The angle: the problem isn't finding a free slot, it's finding a *humane* slot — one that isn't 6 a.m. for someone.

## 2. Audience

Operations leads, EMs, and chiefs-of-staff at fully-distributed companies — teams spread across four or more timezones. They've already tried the obvious fixes: a shared "working hours" doc nobody reads, a Slack bot that posts the time in five cities, asking everyone to "just be flexible." They're tired of being the person who notices, three minutes before the call, that they scheduled it during someone's dinner. They don't want another integration to babysit. They want the math to stop being their job.

## 3. Format and constraints

- 500-700 words.
- Markdown.
- One H1 (the title).
- Three H2 sections, each one step of how it works.
- One pull-quote-able sentence per H2 (something the reader could screenshot).
- Ends with a single, specific call to action — a link to start a workspace, not a vague "learn more."
- No bullet list longer than four items.

## 4. Voice override (or default)

Use the default voice in `reference/voice.md`.

## 5. Success criteria

- Word count is between 500 and 700.
- Reads aloud cleanly.
- Zero buzzwords from the banned list in `reference/voice.md` ("leverage," "synergy," "scalable," "robust," "ecosystem," "thought leader," "10x," "best-in-class," "unlock the power of," "in today's fast-paced world," "let's dive in").
- The "humane slot, not just a free slot" angle is concrete by the second paragraph — names the real problem, not the assumed one.
- The product is named at least three times, but not in every paragraph.
- No invented statistics, no testimonials, no outcome promises Overlap can't keep ("never schedule a bad meeting again" — no).
- Each H2 is an actual step in the order it happens, not a feature grab-bag.
- Ends with a specific CTA (a start/create link, not "stay tuned").

## 6. Refusal context

N/A — no third-party voice, no high-harm domain, no claims requiring external sources. All product facts below are supplied by the brief; the worker invents none.

---

## Product facts (supplied by the brief)

- **Product name:** Overlap
- **What it is:** A scheduling tool for distributed teams. Connects to each member's calendar and their stated working hours.
- **How it works (the three steps the explainer should follow):**
  1. Each person sets their real working hours once — including the hard edges (school run, dinner, the hour they refuse to take calls). Overlap stores the edges, not just a 9-to-5 guess.
  2. When someone proposes a meeting, Overlap maps everyone's hours onto a single timeline and shows the windows where the meeting lands inside *everyone's* working day — and flags windows that only work by making someone sacrifice an edge.
  3. The organizer picks from the humane windows. If no shared humane window exists (it happens with wide spreads), Overlap says so plainly and suggests an async alternative or a rotating-inconvenience option, rather than hiding the bad news.
- **Differentiator:** Most schedulers optimize for *a free slot* — any time the calendars don't collide. Overlap optimizes for *a shared humane slot* — a time that's inside everyone's working day, not just empty on everyone's calendar. Empty and humane are not the same thing.
- **What it does not do:** It does not pretend a good time always exists. It does not auto-book. It does not track productivity or monitor anyone.
- **Available:** Web. Free for teams up to 8; paid above that.
- **CTA URL:** `https://overlap.example/start`

These facts are the only product information the worker has. The explainer must not invent additional features, integrations, outcomes, or testimonials.
