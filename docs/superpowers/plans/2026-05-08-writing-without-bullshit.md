# Writing Without Bullshit Skill — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Implement the `writing-without-bullshit` Claude skill per the design spec at `docs/superpowers/specs/2026-05-08-writing-without-bullshit-design.md`, ready to publish on skills.sh.

**Architecture:** Single skill, progressive disclosure. `SKILL.md` is the always-loaded entry point containing ROAM, the 10 line-edit habits, the meaning-ratio mechanic, the 30-second self-check, mode/format routing, and output templates. Format-specific guidance lives in `references/{email,blog,report,social-and-press}.md` and loads only when the format is detected. A built-in low-info word list lives in `references/weasel-words.md`. A `README.md` provides install instructions and attribution.

**Tech Stack:** Markdown content authoring; no executable code. Validation is qualitative — apply the skill's own methodology to its own files.

**Note on TDD:** This is a content-authoring task, not a code task, so the standard TDD step ordering doesn't apply. Each task creates one Markdown file with a defined section structure derived from the spec. Validation is a final pass that runs the skill's own diagnostic against its README and confirms cross-references resolve.

**Repo root:** `/Volumes/Coding-Environment/Claude/WWBS`

**Skill directory:** `/Volumes/Coding-Environment/Claude/WWBS/writing-without-bullshit/`

---

## Task 1: Create the weasel-words reference list

This is built first because `SKILL.md` references it; ordering avoids a forward dependency.

**Files:**
- Create: `writing-without-bullshit/references/weasel-words.md`

- [ ] **Step 1: Create the file with three labeled categories and a usage instruction.**

  Required content sections:
  - Title and one-line purpose
  - Category 1 — **Qualifiers**: very, leading, generally, robust, considerable, growing, most, many, significant
  - Category 2 — **Filler phrases**: across the landscape, at the end of the day, going forward, in order to, the fact that
  - Category 3 — **Hedges**: it should be noted, arguably, perhaps, somewhat
  - Closing instruction: "This is a starter list. Also flag domain-specific jargon and any word a non-expert reader wouldn't understand."

  Target length ~50 lines. Each entry should be on its own bullet line for parseability.

- [ ] **Step 2: Commit.**

  ```bash
  cd /Volumes/Coding-Environment/Claude/WWBS
  git add writing-without-bullshit/references/weasel-words.md
  git commit -m "Add weasel-words reference for meaning-ratio check"
  ```

---

## Task 2: Create the email playbook

**Files:**
- Create: `writing-without-bullshit/references/email.md`

- [ ] **Step 1: Author the file with three sections.**

  - **Anatomy** — subject line carries the ask; one-line greeting; one-sentence summary up front; facts on one topic only; CTA with deadline; brief sign-off (name + contact, done)
  - **Etiquette** — don't compose important emails on phone; reply, don't reply-all; if you have nothing to add, send nothing; read the latest message in a thread first; after three back-and-forths, stop typing and call
  - **Cold email template** — under 150 words, customized per recipient, what's-in-it-for-them, clear next step

  Include one good/bad subject-line pair. Target ~80 lines.

- [ ] **Step 2: Commit.**

  ```bash
  git add writing-without-bullshit/references/email.md
  git commit -m "Add email format playbook"
  ```

---

## Task 3: Create the blog playbook

**Files:**
- Create: `writing-without-bullshit/references/blog.md`

- [ ] **Step 1: Author the file.**

  - ROAM target sentence template tailored for blog posts
  - Title and first sentences must hook (Google + link previews)
  - Structural toolkit: subheads (max two levels), bullets with bolded openers, numbered lists for sequence, tables for parallel data, graphics
  - Shareable graphic with embedded URL
  - Promote on social; respond to comments; SEO last
  - Length target: <750 words

  Target ~80 lines.

- [ ] **Step 2: Commit.**

  ```bash
  git add writing-without-bullshit/references/blog.md
  git commit -m "Add blog format playbook"
  ```

---

## Task 4: Create the report playbook

**Files:**
- Create: `writing-without-bullshit/references/report.md`

- [ ] **Step 1: Author the file.**

  - ROAM target sentence template for reports
  - Anatomy: title/subtitle → executive summary → setup → analysis → conclusions/recommendations → end matter
  - Story arc: setup → analysis → resolution
  - Title and subtitle are memorable, descriptive, search-friendly; revise repeatedly
  - Executive summary: same story told briefly; written fresh at the end of every draft, not a section-by-section recap
  - Setup: the problem and why it matters
  - Analysis: skimmable; short sections; descriptive headings; bullets with bold openers; tables; graphics; case studies; sidebars
  - Conclusions and recommendations: tell the reader what to do; do not hedge
  - End matter: footnotes, methodology, bibliography
  - Graphics in parallel with text, not as afterthought

  Target ~120 lines.

- [ ] **Step 2: Commit.**

  ```bash
  git add writing-without-bullshit/references/report.md
  git commit -m "Add report format playbook"
  ```

---

## Task 5: Create the social-and-press playbook

**Files:**
- Create: `writing-without-bullshit/references/social-and-press.md`

- [ ] **Step 1: Author the file with three sections.**

  - **Social media**
    - ROAM target sentence: *After reading this, my followers will embrace my message, share it, and think of me as worth following.*
    - Per-platform notes: Facebook (highest reach, algorithm rewards early engagement), X/Twitter (brevity mandatory, works if already followed), LinkedIn (professional networks, lower-frequency reading)
    - Cross-platform: post regularly, front-load every post, include a graphic, share useful things, listen and respond
    - Cold DM rules: identify yourself, state the ask, invite a response; long elaborate DMs get ignored
  - **Press release**
    - Spokesperson voice (not stilted third-person)
    - News in title, plainly
    - Explain what you did and why it matters
    - Use facts and numbers; cut superlatives
    - Conversational so people will share
  - **Marketing pages / company pages**
    - Keep them short
    - Use "we" and "you"
    - Bullets and graphics, not walls of prose
    - Link to specs rather than dumping them in

  Target ~100 lines.

- [ ] **Step 2: Commit.**

  ```bash
  git add writing-without-bullshit/references/social-and-press.md
  git commit -m "Add social and press release format playbook"
  ```

---

## Task 6: Create SKILL.md (the always-loaded entry point)

This is the centerpiece. Order matters — Claude reads top-to-bottom.

**Files:**
- Create: `writing-without-bullshit/SKILL.md`

- [ ] **Step 1: Write the frontmatter.**

  ```markdown
  ---
  name: writing-without-bullshit
  description: Use when drafting or reviewing prose communication — emails, blog posts, reports, announcements, press releases, social posts, or marketing copy. Applies ROAM (Readers/Objective/Action/iMpression) before drafting, the 10 line-edit habits during writing, a meaning-ratio diagnosis, and a 30-second self-check. Skip for code, code comments, commit messages, or technical specs.
  ---
  ```

- [ ] **Step 2: Add the Iron Imperative.**

  One short paragraph: "Treat the reader's time as more valuable than your own. Every tactic in this skill is downstream of this rule. When you write a foggy subject line, bury the lead, hedge with weasel words, or wedge in jargon, you save yourself effort at the reader's expense."

- [ ] **Step 3: Add the ROAM section.**

  Required content:
  - Definitions of R / O / A / iM
  - Target sentence template: *After reading this, [readers] will realize [objective], so they will [action] and think of me as [impression].*
  - **Tiered gate rules:**
    - Short tier (estimated <250 words, casual replies, quick emails): infer ROAM from context, print the target sentence at the top of the draft.
    - Long tier (blog post, report, announcement, press release, or estimated >250 words): ask the user for any of R/O/A/M not stated in the request before drafting. Phrase: "I have [what you have] from your message but need [what's missing] — [specific question for each]."
  - "If you can't write the target sentence, you're not ready to write the piece."

  Target ~30 lines.

- [ ] **Step 4: Add the mode-routing section.**

  - **Detect mode**: generative (request contains draft/write/compose/send/publish/post) vs diagnostic (user pasted prose and said review/edit/critique/fix/rewrite/tighten).
  - **Detect format**: keyword match table:
    | Format | Trigger keywords | Reference file |
    |---|---|---|
    | Email | email, message, reply, send to, subject line | `references/email.md` |
    | Blog | blog, post, article | `references/blog.md` |
    | Report | report, white paper, memo, brief, analysis | `references/report.md` |
    | Social | tweet, X post, LinkedIn, Facebook, Instagram, social, DM | `references/social-and-press.md` |
    | Press release | press release, announcement, marketing copy, web page, product page | `references/social-and-press.md` |
  - If ambiguous, ask once before drafting. Load only the matching reference file.

  Target ~15 lines plus the table.

- [ ] **Step 5: Add the 10 line-edit habits, tight (1-2 lines each + one concrete example).**

  Order and structure exactly:

  1. **Write Short** — Targets: email <250 words, blog <750 words, manager-to-staff <400 words. Try deleting your first sentence; if the piece still works, delete the second.
  2. **Front-Load** — Conclusion first, reasoning after. Lead with the news/recommendation. If the reader stops after 20 words, they should still get the main message.
  3. **Purge Passive** — If you can add "by zombies" after the verb, it's passive. Ask "who is doing this?" and put the actor up front. Aim for far fewer, not zero.
  4. **Replace Jargon** — Three legitimate uses only: terms every reader knows, terms with required legal/technical meaning, terms you define and reuse. Picture an average reader, not the smartest.
  5. **Eliminate Weasel Words** — Replace qualifiers (very, leading, robust, growing) with a number, a named subgroup, or the bold claim itself. "140M trips" beats "millions."
  6. **Be Direct — use I, you, we** — If you can't write "you," you don't know your audience. "I" takes responsibility instead of hiding behind passives.
  7. **Use Numbers Wisely** — Always provide context (a 470-point Dow drop is meaningless without a percentage); cite source and date; cap at three significant digits; beware causation; stress-test with someone who disagrees.
  8. **Reveal Structure** — Headings (max two levels), bullets with **bolded openers**, numbered lists for sequence, tables, simple graphics. Use these in emails too.
  9. **Cut Cheery Filler** — "Have a great day," "Hope this finds you well," "Don't hesitate to reach out" soothe the writer, not the reader. Get to the point and sign off.
  10. **Earn Every Title and Subject Line** — More important than the rest combined. If the reader sees only this, has it communicated something? "July sales exceed quotas by 20%" beats "Some thoughts I had today."

  Target ~50 lines.

- [ ] **Step 6: Add the meaning-ratio check.**

  - The rule: bold every word that carries no real information (qualifiers, filler, jargon nobody outside your team uses). If more than 30% of words are bolded, rewrite.
  - **How to run the check:** load `references/weasel-words.md`. Scan the prose against the three categories in that file. Add Claude-judgment flags for context-specific jargon and empty phrasing the list doesn't cover.
  - **Output format:** `Meaning ratio: NN%  (target: ≥70%)` followed by the count of low-info words flagged. Show the prose with low-info words **bolded** if it's short enough to render.

  Target ~25 lines.

- [ ] **Step 7: Add the 30-second self-check (verbatim from the source guide).**

  ```
  1. Did I treat the reader's time as more valuable than my own?
  2. Does the subject line / title carry the main message?
  3. Is the conclusion in the first 50 words?
  4. Did I cut every weasel word, every passive I could fix, every piece of jargon I could replace?
  5. Is there anything I can delete without losing meaning? (If yes, delete it.)
  6. Do I know what I want the reader to do next, and did I say so?
  ```

  In diagnostic mode, render as a pass/fail list (✓ / ✗) per item.

- [ ] **Step 8: Add output templates.**

  **Generative** template:
  ```
  ROAM target: After reading this, [readers] will realize [objective],
                so they will [action] and think of me as [impression].

  [Draft, applying the 10 habits and matching format playbook.]
  ```

  **Diagnostic** template:
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
  1. [#N HabitName] "before" → "after"
  …

  REWRITE
  ─────────────────────────────────────────
  [Clean version applying every fix above.]
  ```

  Target ~40 lines.

- [ ] **Step 9: Add the attribution footer.**

  One paragraph crediting *Writing Without Bullshit* by Josh Bernoff (HarperBusiness, 2016) as the source methodology, noting this skill is a derivative practical tool.

- [ ] **Step 10: Commit.**

  ```bash
  git add writing-without-bullshit/SKILL.md
  git commit -m "Add SKILL.md entry point with ROAM, 10 habits, meaning ratio, and self-check"
  ```

---

## Task 7: Create README.md

**Files:**
- Create: `writing-without-bullshit/README.md`

- [ ] **Step 1: Author the README.**

  Sections:
  - **Title** and one-paragraph hook describing what the skill does
  - **What it does** — bullet list: pre-draft ROAM, 10 line-edit habits, meaning-ratio check, 30-second self-check, format playbooks
  - **Install** — copy `writing-without-bullshit/` into your skills directory; the skill auto-triggers based on its frontmatter description
  - **Example prompts** that activate it:
    - "Draft an email to my manager about the Q3 hiring freeze."
    - "Review this blog post and tighten it." (paste prose)
    - "Help me write the executive summary for this report."
  - **Attribution** — derivative practical summary based on Josh Bernoff's *Writing Without Bullshit* (HarperBusiness, 2016). Link: https://www.amazon.com/Writing-Without-Bullshit-Boost-Career/dp/0062477153
  - **License** — MIT for the skill structure; methodology credit belongs to Bernoff.

- [ ] **Step 2: Commit.**

  ```bash
  git add writing-without-bullshit/README.md
  git commit -m "Add README with install, examples, and attribution"
  ```

---

## Task 8: Validation pass

This is a meta-test: apply the skill's own diagnostic methodology to its own README and verify the skill files cross-reference correctly.

**Files:**
- No code changes. This task is read-only verification.

- [ ] **Step 1: Cross-reference check.**

  Run from repo root:
  ```bash
  cd /Volumes/Coding-Environment/Claude/WWBS
  grep -n "references/" writing-without-bullshit/SKILL.md
  ls writing-without-bullshit/references/
  ```

  Verify every `references/*.md` mentioned in `SKILL.md` exists in `writing-without-bullshit/references/`. Fix any mismatches.

- [ ] **Step 2: Frontmatter validity.**

  ```bash
  head -5 writing-without-bullshit/SKILL.md
  ```

  Confirm the frontmatter has `name:` and `description:` fields and is enclosed in `---` fences.

- [ ] **Step 3: Self-applied diagnostic on README.**

  Re-read `writing-without-bullshit/README.md`. Run the 30-second self-check against it as the skill itself would:
  1. Reader's time treated as more valuable? — should pass
  2. Title carries the main message? — should pass
  3. Conclusion in first 50 words? — verify
  4. Weasel words / passives / jargon cut? — scan against `weasel-words.md`
  5. Anything to delete without losing meaning? — trim if yes
  6. Reader's next action stated (i.e., install instructions)? — should pass

  Fix any failures inline. If the README fails its own check, the skill fails its own dogfood test.

- [ ] **Step 4: Self-applied diagnostic on SKILL.md prose.**

  Same check on `SKILL.md`'s prose (excluding code blocks and tables). Fix any failures.

- [ ] **Step 5: Commit any fixes.**

  ```bash
  git add -A writing-without-bullshit/
  git commit -m "Validation pass: tighten README and SKILL.md per self-check" || echo "no changes to commit"
  ```

---

## Task 9: Final push to GitHub

- [ ] **Step 1: Push all commits.**

  ```bash
  cd /Volumes/Coding-Environment/Claude/WWBS
  git push origin main
  ```

- [ ] **Step 2: Verify the push.**

  ```bash
  git log --oneline -10
  git status
  ```

  Working tree should be clean and `main` should be ahead of nothing (i.e., in sync with origin).

---

## Self-review

Coverage check against the design spec:
- §5.1 file layout → Tasks 1–7 create all listed files
- §6 trigger conditions → Task 6 Step 1 (frontmatter description)
- §7 mode routing → Task 6 Step 4
- §8 SKILL.md content shape → Task 6 Steps 1–9 follow the 9-section order
- §9 format playbook contents → Tasks 1–5
- §10 output templates → Task 6 Step 8
- §11 distribution / README → Task 7
- §12 decisions table → reflected throughout

Placeholder scan: every step states the actual content categories or exact text to include. No "TBD" or "implement later."

Type/name consistency: skill name `writing-without-bullshit` is consistent across SKILL.md frontmatter, README install path, and directory name. Reference filenames match the format-detection table.
