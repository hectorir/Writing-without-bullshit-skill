---
name: writing-without-bullshit
description: Use when drafting or reviewing prose communication — emails, blog posts, reports, announcements, press releases, social posts, or marketing copy. Applies ROAM (Readers/Objective/Action/iMpression) before drafting, the 10 line-edit habits during writing, a meaning-ratio diagnosis, and a 30-second self-check. Skip for code, code comments, commit messages, or technical specs.
---

# Writing Without Bullshit

Operationalizes Josh Bernoff's *Writing Without Bullshit* methodology. Use it whenever the user asks you to draft prose communication, or shares prose and asks you to review or tighten it.

## The Iron Imperative

**Treat the reader's time as more valuable than your own.**

Every tactic in this skill is downstream of this rule. A foggy subject line, a buried lead, a hedged claim, or a wedge of jargon all save the writer effort at the reader's expense. Spend the extra five minutes so a hundred readers don't each have to spend two.

---

## ROAM — before drafting

For anything more substantive than a one-line reply, answer four questions:

- **Readers** — Who specifically? Picture one real person.
- **Objective** — What change in their thinking?
- **Action** — What do you want them to *do* after reading?
- **iMpression** — What should they think of you?

Then state the target sentence:

> *After reading this, [readers] will realize [objective], so they will [action] and think of me as [impression].*

If you can't write that sentence, the piece is not ready.

### Tiered gate

**Short tier** — quick replies, casual notes, anything you estimate is under 250 words.
- Infer ROAM from the user's request and context.
- Print the target sentence at the top of the draft.

**Long tier** — blog post, report, announcement, press release, or anything you estimate is over 250 words.
- Before drafting, ask the user for any of R/O/A/M not stated in the request.
- Phrase: "I have [R, M] from your message but need O and A — what change in their thinking, and what action?"
- Wait for the answer. Then draft.

---

## Mode and format routing

When this skill loads, decide both the mode and the format.

### Mode

- **Generative** — request contains "draft / write / compose / send / publish / post" or asks for new prose.
- **Diagnostic** — user pasted prose and asked for review, edit, critique, fix, rewrite, or tightening.

### Format

Match the request keywords to one playbook. Load only the matching reference file.

| Format | Trigger keywords | Reference file |
|---|---|---|
| Email | email, message, reply, send to, subject line, inbox | `references/email.md` |
| Blog | blog, post, article | `references/blog.md` |
| Report | report, white paper, memo, brief, analysis | `references/report.md` |
| Social | tweet, X post, LinkedIn, Facebook, Instagram, social, DM | `references/social-and-press.md` |
| Press / marketing | press release, announcement, marketing copy, web page, product page, landing page | `references/social-and-press.md` |

If the format is ambiguous, ask once before drafting:

> "Is this for an email, a blog post, or a longer piece? The playbook differs."

---

## The 10 line-edit habits

Apply in roughly this order. Each habit has one rule and one example.

1. **Write Short.** Targets: email <250 words, blog <750, manager-to-staff <400. Try deleting the first sentence; if the piece still works, delete the second.

2. **Front-Load.** Conclusion first, reasoning after. If the reader stops after 20 words, they should still get the main message.
   - ✅ "Approve the $40K hiring req by Friday so we can post the role Monday."
   - ❌ "I wanted to share some thoughts on hiring that I've been mulling over…"

3. **Purge Passive.** If you can add "by zombies" after the verb, it's passive. Ask "who is doing this?" and put the actor up front. Aim for far fewer, not zero.
   - ✅ "We decided to ship Tuesday."
   - ❌ "A decision was made to ship Tuesday."

4. **Replace Jargon.** Three legitimate uses only: terms every reader knows, terms with required legal or technical meaning, terms you define and reuse. Picture an average reader, not the smartest.

5. **Eliminate Weasel Words.** Replace qualifiers (very, leading, robust, growing, considerable) with a number, a named subgroup, or the bold claim itself.
   - ✅ "29% revenue growth" — "engineers in our Boston office"
   - ❌ "significant growth" — "many engineers"

6. **Be Direct — use I, you, we.** If you can't write "you," you don't know your audience well enough yet. "I" takes responsibility instead of hiding behind passives.

7. **Use Numbers Wisely.** Always provide context (a 470-point Dow drop is meaningless without a percentage). Cite source and date. Cap precision at three significant digits. Beware causation. Stress-test with someone who disagrees.

8. **Reveal Structure.** Headings (max two levels), bullets with **bolded openers**, numbered lists for sequence, tables for parallel data, simple graphics. Use these in emails too, not just reports.

9. **Cut Cheery Filler.** "Have a great day," "Hope this finds you well," "Don't hesitate to reach out" soothe the writer, not the reader. Get to the point and sign off.

10. **Earn Every Title and Subject Line.** More important than the rest combined. Spend disproportionate time on it. If the reader sees only this, has it communicated something useful?
    - ✅ "July sales exceed quotas by 20%"
    - ❌ "Some thoughts I had today"

---

## Meaning ratio

A diagnostic for low-information density.

**The rule:** bold every word that carries no real information — qualifiers, filler, jargon nobody outside the team uses. If more than 30% of the words in a paragraph end up bolded, rewrite.

### How to run the check

1. Load `references/weasel-words.md`.
2. Scan the prose. Flag every word or phrase that matches a category (qualifiers, filler phrases, hedges).
3. Add Claude-judgment flags: domain-specific jargon, empty intensifiers, or buzzwords the list doesn't cover.
4. Compute: `meaning ratio = 1 − (low-info words / total words)`.

### Output format

```
Meaning ratio: 78%  (target: ≥70%)
Low-info words flagged: 12
```

When prose is short enough to render, show it with low-info words **bolded** so the user sees what was caught.

---

## The 30-second self-check

Run before declaring any draft done. In diagnostic mode, render as ✓ / ✗.

1. Did I treat the reader's time as more valuable than my own?
2. Does the subject line / title carry the main message?
3. Is the conclusion in the first 50 words?
4. Did I cut every weasel word, every passive I could fix, every piece of jargon I could replace?
5. Is there anything I can delete without losing meaning? (If yes, delete it.)
6. Do I know what I want the reader to do next, and did I say so?

If all six pass, the draft ships.

---

## Output templates

### Generative — when drafting new prose

```
ROAM target: After reading this, [readers] will realize [objective],
              so they will [action] and think of me as [impression].

[The draft itself, applying the 10 habits and matching format playbook.]
```

For the long tier, ask for missing ROAM elements before drafting. Don't draft on a guess.

### Diagnostic — when reviewing existing prose

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

The scorecard format is fixed and parseable. The issue list and rewrite are free-form.

---

## Attribution

Source: Bernoff, Josh. *Writing Without Bullshit: Boost Your Career by Saying What You Mean.* HarperBusiness, 2016. This skill is a derivative practical tool that operationalizes the methodology; the original book is the canonical reference.
