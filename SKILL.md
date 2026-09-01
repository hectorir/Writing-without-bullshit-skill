---
name: writing-without-bullshit
description: Use when the user asks to draft, write, reply to, tighten, edit, review, or rewrite prose meant for another person, including emails, replies, blog posts, articles, reports, memos, announcements, press releases, social posts, and marketing or web copy. Not for code, code comments, commit messages, or technical specs.
---

# Writing Without Bullshit

Operationalizes Bernoff's *Writing Without Bullshit*.

## The Iron Imperative

**Treat the reader's time as more valuable than your own.**

Every tactic downstream of this rule. Foggy subject line, buried lead, hedged claim, jargon, invented statistic — all save writer effort at reader's expense.

---

## Output contract

The response **is** the deliverable. Three shapes.

**Draft request → the draft.** Subject line or title (when format has one), then body. Nothing above. Nothing below. Unknown fact → bracketed placeholder inside the draft: `[X%]`, `[date]`, `[episode you've actually heard]`.

**Review request → the edited text.** Same shape. Edited text only.

**Long-tier request with missing ROAM → one question.** No draft in that message.

User asks for notes or options in the same message → after the draft, brief. Otherwise ROAM target, scorecard, issues list, weasel flags, and full rewrite are follow-ups only (see On request only).

---

## ROAM — before drafting

Answer silently before writing:

- **Readers** — Who specifically? Picture one real person.
- **Objective** — What change in their thinking?
- **Action** — What do you want them to *do* after reading?
- **iMpression** — What should they think of you?

Target sentence, held in mind, never printed:

> *After reading this, [readers] will realize [objective], so they will [action] and think of me as [impression].*

### Tiered gate

**Micro** — reply under ~40 words, "say yes," "decline politely." Skip ROAM. Habits 2, 3, 9. Send.

**Short** — replies, notes, <250 words. Infer ROAM. Draft.

**Long** — blog, report, announcement, press release, >250 words. Any R/O/A/M not stated → ask once, one message, every missing part with a best guess so user can answer "yes." Same message asks for facts the draft needs. Shape:

> "Before I draft: Readers = [guess]? Objective = [guess]? Action = [guess]? Confirm or correct, and send any numbers, names, or reasons you want in it."

Wait. Then draft.

---

## Mode and format routing

On load, decide mode + format.

### Mode

- **Draft** — "draft / write / compose / reply / send / post" or any ask for new prose.
- **Light edit** — "tighten / trim / edit / fix / shorten / clean up / polish / proofread," any other review verb, or prose pasted with no verb.
- **Full rewrite** — "rewrite / redo / overhaul / restructure / go harder," or a light edit already delivered and user asks for more.

### What a light edit is

Keeps: author's voice, register, paragraph order, sentence order, their word choices for anything that isn't bullshit, their facts, their sign-off. Length ≤ original.

Changes: cut weasel words, filler, hedges, cheery filler, AI tells; fix passives with a clear actor; move a buried ask or decision to the first sentence; supply a subject line that carries the ask when one is missing.

Leaves alone: structure (no new lists or headings), content (nothing added), facts, tone.

### What a full rewrite is

Every habit plus the format playbook. Restructure freely, re-title, front-load, bullets with bolded openers, one topic per email. Facts stay the author's. Nothing invented.

### Format

Match request keywords → load matching reference file.

| Format | Trigger keywords | Reference file |
|---|---|---|
| Email | email, message, reply, send to, subject line, inbox | `references/email.md` |
| Blog | blog, post, article | `references/blog.md` |
| Report | report, white paper, memo, brief, analysis | `references/report.md` |
| Social | tweet, X post, LinkedIn, Facebook, Instagram, social, DM | `references/social-and-press.md` |
| Press / marketing | press release, announcement, marketing copy, web page, product page, landing page | `references/social-and-press.md` |

Ambiguous format → ask once:

> "Is this for an email, a blog post, or a longer piece? The playbook differs."

---

## The 10 line-edit habits

Apply roughly in order.

1. **Write Short.** email <250, cold email <150, blog <750, mgr-to-staff <400. Try deleting first sentence; if works, delete second.

2. **Front-Load.** Conclusion first, reasoning after. Reader stops at 20 words → main message already landed.
   - ✅ "Approve the $40K hiring req by Friday so we can post the role Monday."
   - ❌ "I wanted to share some thoughts on hiring that I've been mulling over…"

3. **Purge Passive.** Can add "by zombies" after verb → passive. "Who is doing this?" → actor up front. Aim fewer, not zero.
   - ✅ "We decided to ship Tuesday."
   - ❌ "A decision was made to ship Tuesday."

4. **Replace Jargon.** 3 legit uses: terms every reader knows; legal/technical required; terms you define + reuse. Picture avg reader, not smartest.

5. **Eliminate Weasel Words.** Replace qualifiers (very, leading, robust, growing, considerable) with number, named subgroup, or bold claim. No number in hand → `[X%]` placeholder. **Never invent a figure, date, name, source, or quote.** A plausible fake number is the worst bullshit in the book.
   - ✅ "29% revenue growth" — "engineers in our Boston office" — "[N]% revenue growth"
   - ❌ "significant growth" — "many engineers" — a number the user never gave you

6. **Be Direct — use I, you, we.** Can't write "you" → don't know audience yet. "I" takes responsibility instead of hiding behind passives.

7. **Use Numbers Wisely.** Numbers come from the user or their source material, nowhere else. Always provide context (470-pt Dow drop meaningless without %). Cite source + date. Cap at 3 sig digits. Beware causation.

8. **Reveal Structure.** Headings (max 2 levels), bullets w/ **bolded openers** that add rather than echo, numbered lists for sequence, tables for parallel data. Emails too, not just reports. Light edit → leave structure as found.

9. **Cut Cheery Filler and AI Tells.** "Hope this finds you well," "Don't hesitate to reach out," "Happy to adjust" — soothe writer, not reader. Same for em-dash glue, "it's not X, it's Y," forced triplets, announced structure (list in `references/weasel-words.md`). Get to point, sign off.

10. **Earn Every Title and Subject Line.** More important than rest combined. Reader sees only this → did it communicate something useful?
    - ✅ "July sales exceed quotas by 20%"
    - ❌ "Some thoughts I had today"

---

## The 30-second self-check

Run silently before sending. Render ✓/✗ only when scorecard is requested.

1. Reader's time treated as more valuable than mine?
2. Subject/title carries main message?
3. Conclusion in first 50 words?
4. Cut every weasel word, fixable passive, replaceable jargon, AI tell?
5. Anything deletable without losing meaning? → delete it.
6. Reader's next action clear and stated?
7. Every number, name, date, and quote came from the user or their material?

All seven pass → ships. Any fail → fix, then ship. Never a note to the user.

---

## On request only

Never volunteered. User follows up with "show the ROAM," "show the scorecard," "what did you change," "flag the weasel words," "full rewrite / go harder," or "show your work" → load `references/diagnostics.md` and deliver that item only.

---

## Red flags

| Thought | Reality |
|---|---|
| "A quick note on what I changed will help" | They ask "what did you change" when they want it. Text only. |
| "A few tips before they send it" | Tips are a follow-up. Draft only. |
| "They said tighten, but it needs restructuring" | Light edit. They say "go harder" if they want more. |
| "No number given, but a plausible one reads better" | Placeholder. Invented numbers are the one unforgivable thing. |
| "Long piece; I'll draft with brackets instead of asking" | Long tier asks first. One message, guesses included. |

---

## Attribution

Source: Bernoff, Josh. *Writing Without Bullshit: Boost Your Career by Saying What You Mean.* HarperBusiness, 2016. Derivative tool; original is canonical.
