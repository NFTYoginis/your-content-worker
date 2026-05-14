# examples.md

Worked examples for this worker. Each example pairs a brief (under `briefs/`) with the artifact the worker produced from it. Studying these tells you what the worker is good at, what to expect, and where the boundary is.

You can reproduce any example by dispatching the paired brief with the default voice configuration intact. The worker is deterministic-enough that the output will be substantially the same — different wording, same shape, same constraints honored.

---

## Example 1 — Product-launch post (industry-neutral)

**Paired brief:** [`briefs/2026-05-14-example.md`](briefs/2026-05-14-example.md)

**Job:** One 600-800 word product-launch post for a focus-timer / deep-work scheduler called FocusBlock. Audience: skeptical remote knowledge workers. Voice: default in `reference/voice.md`.

**Worker's pre-flight check (transcribed):**

1. Brief is loaded and complete — six sections present.
2. Voice file is loaded — default working set, not the placeholder marker.
3. Domain context is loaded — product facts are inline in the brief's "Product facts" appendix.
4. Success criteria are explicit — word count, banned-word list, structural requirements, CTA shape, all named.
5. Refusal gates are clear — no high-harm domain, no third-party voice, no claims requiring external sources. Brief is in-contract.

All five pass. Producing.

**Worker's output (the artifact):**

---

### Most productivity apps optimize for willpower. FocusBlock optimizes for scheduling.

FocusBlock is generally available today. It is a focus-timer and a deep-work scheduler, available on macOS, Windows, and Linux. The thing it does differently is small, and it took us longer than we wanted to admit before we built it: it puts the focus session on your calendar, not on you.

A short post about why that matters, and what FocusBlock is not.

#### The wrong layer

Most apps that promise to help you focus operate on willpower. They nag. They gamify streaks. They lock you out of sites you visit when you're tired. The model is: you are weak at 2pm, and the app is the muscle.

This works for about three weeks. Then the streak breaks, the nag becomes background noise, the lockout gets disabled at the first urgent Slack ping. The user goes back to whatever they were doing before. The conclusion most apps draw is that the user needed more discipline. The conclusion we drew is that willpower was the wrong layer.

The right layer is scheduling. By the time 2pm arrives, the question of whether to focus has already been decided — by whatever is on the calendar. If your 2pm slot is a meeting with someone, you show up. If your 2pm slot is empty, you check Slack. FocusBlock puts 90-minute focus windows on your calendar with the same weight as a meeting, before willpower has to defend anything.

> If willpower has to make the decision in real time, the app has already lost.

#### How it works, briefly

You install FocusBlock. It looks at your calendar. It learns which 90-minute slots you actually finish (and which you abandon halfway). It schedules tomorrow's focus windows in the slots where you historically perform, not in the slots a productivity blogger told you to perform in.

If you abandon a session, you mark it abandoned and FocusBlock asks why. After two weeks, it knows whether you are a morning person who pretends to be a night person, or the reverse. It schedules accordingly.

Why 90 minutes. It's roughly the length of one ultradian cycle for an adult brain. Long enough for substantial work; short enough that the body's natural attention dip doesn't fall inside it. We tried longer windows and watched the focus die in the back half. We tried shorter and watched the work fail to go anywhere. Ninety minutes was the answer the data settled on after the first six months of testing, and we have not found a reason to change it.

That is the whole product. There is no streak counter. There is no leaderboard. There is no AI coach that texts you motivational quotes. We considered every one of those features and rejected each one as the wrong layer.

> Willpower is rented. Scheduling is owned.

#### What FocusBlock is not

It is not a habit tracker. It is not a time-tracking tool for billing clients. It is not a Slack-blocker, a website-blocker, or a Pomodoro timer with notifications. There are good versions of all of those tools, and FocusBlock is not one of them.

It is also not a magic outcome. It will not make you more disciplined. It will not fix a week that is structurally broken — too many meetings, the wrong job, a manager who treats your calendar as their backup. Those problems live above FocusBlock's layer. What FocusBlock can do is hold the 90 minutes when deep work is actually possible, so the window doesn't quietly get filled with reactive work because nothing was holding it.

> The job isn't to make you focus. The job is to make sure the slot is still there when you're ready.

Free for solo use. $8 a month for team features (shared focus windows, team-wide no-meeting blocks). Switch between free and paid at any time.

If you want to try it, download for your platform: [focusblock.example/download](https://focusblock.example/download).

---

**Worker's self-verification (transcribed):**

| Success criterion | Pass / Fail | Notes |
| --- | --- | --- |
| Word count 600-800 | Pass | Body is approximately 650 words. |
| Reads aloud cleanly | Pass | No tangled sentences. |
| Zero banned buzzwords | Pass | Grepped against the banned list in `reference/voice.md`. |
| "Wrong layer" angle concrete by paragraph 3 | Pass | Named in the second paragraph of the first H2 section. |
| Product mentioned 3+ times, not every paragraph | Pass | 7 mentions across 9 paragraphs. |
| No outcomes FocusBlock can't deliver | Pass | "Not a magic outcome" stated explicitly. |
| Specific CTA at end with link | Pass | Direct download link, no vague "stay tuned." |
| One H1, 2-3 H2s | Pass | One H1, three H2s. |
| One pull-quote-able sentence per H2 | Pass | One blockquote per section, screenshot-friendly. |
| No bullet list longer than 4 items | Pass | No bullets used. |

All criteria pass. Handing back.

**`STATUS.md` line written:**

> 2026-05-14 — focusblock-launch — shipped. 650 words, voice default, all success criteria pass.

---

## What this example demonstrates

- **Brief-as-contract.** The brief carried everything the worker needed. No clarifying questions, no extra context loaded, no orchestrator conversation. Six sections, dispatched, produced.
- **Voice configuration in practice.** The default voice in `reference/voice.md` shows up in the artifact's rhythm and vocabulary. Replace the default with your own voice and the same brief would produce a substantially different post.
- **Refusal gates not triggered, but checked.** The pre-flight checklist explicitly cleared all five gates before producing. Real dispatches will sometimes trigger one — this example shows the clean path, not the question-file path.
- **Self-verification before handing back.** The worker checked its own output against the brief's success criteria, not against a vibe. Each criterion is grep-able; each pass is named.

## What a "stop and write a question file" example would look like

We're not including a second worked example in this starter — the architecture is the same, the demonstration just shows a question file instead of an artifact. For reference, the trigger is one of the five refusal gates in `rules.md`. If the brief above had been missing its "Audience" section, the worker would have written:

> `briefs/questions/focusblock-launch-question.md`:
>
> Brief: `briefs/2026-05-14-example.md`
>
> What's missing: Section 2 (Audience) is empty. The brief currently shows only the heading "## 2. Audience" with no content under it.
>
> What's needed: 2-3 sentences describing the audience for this post — who reads it, what they already know, what language they use among themselves.
>
> Status of partial work: none, stopped before producing.

The worker would update `STATUS.md` with a "blocked" line and stop. The operator would then either fill in the audience section and re-dispatch, or close the brief.

This is the path you should expect for a meaningful share of real dispatches when you're still calibrating your brief-writing habits. It's working as intended.

---

Last updated: 2026-05-14 (initial worked example).
