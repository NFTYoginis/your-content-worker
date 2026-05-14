# Brief — <DATE>-<SLUG>

The brief is the worker's contract. Copy this template to `briefs/<YYYY-MM-DD>-<slug>.md` and fill it in. If a section is genuinely N/A, write "N/A — [one-line reason]" rather than deleting the heading.

---

## 1. What to produce

The deliverable, in concrete terms. The worker should be able to grep this section and know exactly what to make.

**Examples of complete answers:**
- "One 600-800 word product-launch post for the company blog."
- "Three LinkedIn post variants (each ~180 words), same point, three different angles."
- "A 90-second voice-over script for a product demo video, formatted with pauses marked."

**Examples of incomplete answers:**
- "Some content about the new launch." (No format, no length, no platform.)
- "A post." (Which platform? How long?)

---

## 2. Audience

Who reads this. What they already know. What they care about. What language they use among themselves.

A useful answer is two or three sentences. A useless answer is "everyone" or "our customers."

**Example:** "Solo founders and indie developers running their own infrastructure. They already understand Docker and CI/CD but are skeptical of any tool that adds another service to their stack. They read Hacker News, they roll their eyes at SaaS-y marketing, they want a concrete time-saved number before they'll keep reading."

---

## 3. Format and constraints

Word count (as a range or a hard ceiling). Platform. Structural requirements. Anything the worker would otherwise have to guess.

**Examples:**
- "600-800 words. Markdown. H2 section headings. One pull-quote-able sentence per H2."
- "LinkedIn post, 150-200 words, single paragraph, ends with a question."
- "Email, plain text, no subject line in the body, ~250 words, signed off with [name]."

---

## 4. Voice override (or default)

Either:
- "Use the default voice in `reference/voice.md`." (Most common.)
- "Use the voice in `reference/voice-<variant>.md`." (For when you maintain multiple voice configurations — different brands, different audiences.)
- "Override the default with the following clauses: …" (For one-off voice tweaks. Use sparingly; if you're overriding repeatedly, edit the voice file instead.)

---

## 5. Success criteria

What "done" looks like, in concrete terms the worker can verify itself against before handing back.

**Examples:**
- "Reads aloud cleanly. No buzzwords from the banned list. Word count in range. One pull-quote-able sentence per H2. No invented statistics."
- "Sounds like the published examples in `reference/voice.md`. Audience would recognize the tone. Ends with a single specific question."

Make this list grep-able. The worker will check each item before declaring shipped.

---

## 6. Refusal context (if relevant)

If this brief touches a domain where the worker needs extra care — claims requiring sources, real third parties named, high-harm domains, regulatory considerations — note that here. The worker uses this section to decide whether to apply any of the refusal gates from `rules.md`.

If the brief is in a high-harm domain (medical, legal, mental-health crisis, financial advice for vulnerable audiences), this section MUST include the line:

> operator-authorized: I have reviewed the regulatory and harm context for this domain, and I authorize the worker to produce content here.

Without that line, the worker refuses high-harm content.

Otherwise, leave this section empty or write "N/A — no third-party voice, no high-harm domain, no claims requiring external sources."

---

## Notes for the operator (delete this section before dispatch)

- A complete brief should fit in one screen. If yours is sprawling, you're orchestrating in the wrong place.
- The brief is permanent. Once dispatched, it lives in `briefs/` as the contract for what was asked. Don't edit it after the fact.
- If you find yourself writing the brief twice for similar dispatches, the duplicated content probably belongs in a `reference/` file, not in every brief.
