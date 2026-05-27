---
name: writing-without-bullshit
description: Use drafting/reviewing prose: emails, blog posts, reports, announcements, press releases, social posts, marketing copy. Applies ROAM before drafting, 10 line-edit habits during writing, meaning-ratio diagnosis, 30-sec self-check. Skip: code, comments, commits, tech specs.
---

# Writing Without Bullshit

Operationalizes Bernoff's *Writing Without Bullshit*. Use when user drafts prose or shares prose for review/tightening.

## The Iron Imperative

**Treat the reader's time as more valuable than your own.**

Every tactic downstream of this rule. Foggy subject line, buried lead, hedged claim, jargon — all save writer effort at reader's expense. Spend 5 min so 100 readers don't each spend 2.

---

## ROAM — before drafting

Beyond a one-line reply, answer:

- **Readers** — Who specifically? Picture one real person.
- **Objective** — What change in their thinking?
- **Action** — What do you want them to *do* after reading?
- **iMpression** — What should they think of you?

Then state the target sentence:

> *After reading this, [readers] will realize [objective], so they will [action] and think of me as [impression].*

Can't write it → piece not ready.

### Tiered gate

**Short tier** — quick replies, casual notes, <250 words.
- Infer ROAM from request + context.
- Print target sentence at top of draft.

**Long tier** — blog, report, announcement, press release, >250 words.
- Ask user for any R/O/A/M not stated.
- Phrase: "I have [R, M] but need O and A — change in thinking? action?"
- Wait for answer, then draft.

---

## Mode and format routing

On load, decide mode + format.

### Mode

- **Generative** — request contains "draft / write / compose / send / publish / post" or asks for new prose.
- **Diagnostic** — user pasted prose and asked for review, edit, critique, fix, rewrite, or tightening.

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

1. **Write Short.** email <250, blog <750, mgr-to-staff <400. Try deleting first sentence; if works, delete second.

2. **Front-Load.** Conclusion first, reasoning after. Reader stops at 20 words → main message already landed.
   - ✅ "Approve the $40K hiring req by Friday so we can post the role Monday."
   - ❌ "I wanted to share some thoughts on hiring that I've been mulling over…"

3. **Purge Passive.** Can add "by zombies" after verb → passive. "Who is doing this?" → actor up front. Aim fewer, not zero.
   - ✅ "We decided to ship Tuesday."
   - ❌ "A decision was made to ship Tuesday."

4. **Replace Jargon.** 3 legit uses: terms every reader knows; legal/technical required; terms you define + reuse. Picture avg reader, not smartest.

5. **Eliminate Weasel Words.** Replace qualifiers (very, leading, robust, growing, considerable) with number, named subgroup, or bold claim.
   - ✅ "29% revenue growth" — "engineers in our Boston office"
   - ❌ "significant growth" — "many engineers"

6. **Be Direct — use I, you, we.** Can't write "you" → don't know audience yet. "I" takes responsibility instead of hiding behind passives.

7. **Use Numbers Wisely.** Always provide context (470-pt Dow drop meaningless without %). Cite source + date. Cap at 3 sig digits. Beware causation. Stress-test with dissenter.

8. **Reveal Structure.** Headings (max 2 levels), bullets w/ **bolded openers**, numbered lists for sequence, tables for parallel data, simple graphics. Emails too, not just reports.

9. **Cut Cheery Filler.** "Have a great day," "Hope this finds you well," "Don't hesitate to reach out" — soothe writer, not reader. Get to point, sign off.

10. **Earn Every Title and Subject Line.** More important than rest combined. Spend disproportionate time. Reader sees only this → did it communicate something useful?
    - ✅ "July sales exceed quotas by 20%"
    - ❌ "Some thoughts I had today"

---

## Meaning ratio

Diagnostic for low-information density.

**Rule:** bold every word carrying no real info — qualifiers, filler, jargon no non-expert uses. >30% bolded → rewrite.

### How to run the check

1. Load `references/weasel-words.md`.
2. Scan prose. Flag every word/phrase matching a category (qualifiers, filler, hedges).
3. Add Claude-judgment flags: domain jargon, empty intensifiers, buzzwords not on list.
4. Compute: `meaning ratio = 1 − (low-info words / total words)`.

### Output format

```
Meaning ratio: 78%  (target: ≥70%)
Low-info words flagged: 12
```

Short enough prose → show with low-info words **bolded**.

---

## The 30-second self-check

Run before declaring draft done. Diagnostic mode → render ✓ / ✗.

1. Reader's time treated as more valuable than mine?
2. Subject/title carries main message?
3. Conclusion in first 50 words?
4. Cut every weasel word, fixable passive, replaceable jargon?
5. Anything deletable without losing meaning? → delete it.
6. Reader's next action clear and stated?

All six pass → draft ships.

---

## Output templates

### Generative

```
ROAM target: After reading this, [readers] will realize [objective],
              so they will [action] and think of me as [impression].

[The draft itself, applying the 10 habits and matching format playbook.]
```

Long tier → ask for missing ROAM before drafting. Don't guess.

### Diagnostic

```
SCORECARD
─────────────────────────────────────────
Meaning ratio: NN%  (target: ≥70%)
30-second check:
  ✓/✗ Reader's time treated as more valuable
  ✓/✗ Subject line carries the main message
  ✓/✗ Conclusion in first 50 words
  ✓/✗ Weasel/passive/jargon cut
  ✓/✗ Nothing further to delete
  ✓/✗ Reader's next action stated
ROAM (inferred): R=… · O=… · A=… · M=…

ISSUES (mapped to habits)
─────────────────────────────────────────
1. [#N HabitName] "before phrase" → "after phrase"
2. [#N HabitName] "before phrase" → "after phrase"
…

REWRITE
─────────────────────────────────────────
[Clean version applying every fix above.]
```

Scorecard fixed + parseable. Issue list + rewrite are free-form.

---

## Attribution

Source: Bernoff, Josh. *Writing Without Bullshit: Boost Your Career by Saying What You Mean.* HarperBusiness, 2016. Derivative tool; original is canonical.
