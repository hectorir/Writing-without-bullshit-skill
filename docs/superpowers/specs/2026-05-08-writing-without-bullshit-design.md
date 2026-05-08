# Writing Without Bullshit — Skill Design

*Date: 2026-05-08*
*Status: Approved — ready for implementation plan*
*Source material: Josh Bernoff,* Writing Without Bullshit *(HarperBusiness, 2016) — distilled into a practical user's guide that this skill operationalizes.*

---

## 1. Overview

A single Claude skill, `writing-without-bullshit`, that helps users draft and review business prose using Bernoff's methodology. The skill auto-triggers for prose-writing tasks (emails, blog posts, reports, social posts, press releases, marketing copy) and operates in two modes:

- **Generative** — when the user asks Claude to draft something, the skill applies ROAM up front and the 10 line-edit habits during writing.
- **Diagnostic** — when the user shares existing prose, the skill produces a scorecard (meaning ratio, 30-second self-check, inferred ROAM), an issue list mapped to the 10 habits, and a clean rewrite.

Format-specific playbooks (email, blog, report, social-and-press) load only when the relevant format is detected. The skill is published to GitHub and listed on skills.sh.

## 2. Goals

- Make it effortless to apply Bernoff's discipline consistently across prose work
- Keep the always-loaded core small; defer format details until needed
- Produce output that is actionable, not just descriptive (rewrites, not lectures)
- Be easy to install as a single skill on skills.sh

## 3. Non-goals

- Cover code, code comments, commit messages, or technical specifications
- Replace human judgment on tone, voice, or audience nuance
- Reproduce the source book; this is a derivative practical tool

## 4. Scope

**In scope (the five core mechanics):**
- ROAM (Readers / Objective / Action / iMpression)
- Meaning ratio
- The 10 line-edit habits
- The 30-second self-check
- Format playbooks for email, blog, report, social, and press release / marketing copy

**Explicitly out of scope:**
- The Disciplined Writing Process (Prepare → Draft → Revise three-stage workflow)
- High-fear writing notes (bad news, crisis comms)
- "For women especially" notes
- Coauthor protocol
- "Spreading it" organizational adoption guidance

## 5. Architecture

### 5.1 File layout

```
writing-without-bullshit/
├── SKILL.md                          # always-loaded entry point
├── references/
│   ├── email.md                      # email playbook
│   ├── blog.md                       # blog playbook
│   ├── report.md                     # report / long-form playbook
│   ├── social-and-press.md           # social posts + press release / marketing
│   └── weasel-words.md               # built-in low-info word list
└── README.md                         # GitHub + skills.sh listing
```

### 5.2 Loading model (progressive disclosure)

- `SKILL.md` always loads.
- A format playbook from `references/` loads only when the user's task matches that format.
- `references/weasel-words.md` loads when the meaning-ratio check runs.

### 5.3 Approximate sizes

- `SKILL.md`: 350–450 lines
- Each format playbook: 80–150 lines
- `weasel-words.md`: ~50 lines

## 6. Trigger conditions

Frontmatter `description` field:

> Use when drafting or reviewing prose communication — emails, blog posts, reports, announcements, press releases, social posts, or marketing copy. Applies ROAM (Readers/Objective/Action/iMpression) before drafting, the 10 line-edit habits during writing, a meaning-ratio diagnosis, and a 30-second self-check. Skip for code, code comments, commit messages, or technical specs.

This description is what surfaces in skills.sh listings and what Claude pattern-matches to auto-invoke the skill.

## 7. Mode routing

`SKILL.md` contains routing logic that runs when the skill loads.

### 7.1 Detect mode

- **Generative** — request contains "draft / write / compose / send / publish / post" or asks for new prose.
- **Diagnostic** — user pasted prose and said "review / edit / critique / fix / rewrite / tighten."

### 7.2 Detect format

Keyword match to email / blog / report / social / press. If ambiguous, ask once before drafting. Load only the matching reference file.

### 7.3 Generative branch

- **Length tier — short (<250 words estimated):** infer ROAM, print the target sentence at the top of the draft.
- **Length tier — long (blog, report, announcement, or >250 words):** ask for any of R/O/A/M not stated in the request, then draft.
- Apply the 10 habits and matching format playbook while writing.
- Run the 30-second self-check internally before returning the draft.

### 7.4 Diagnostic branch

- Run the meaning-ratio check (load `weasel-words.md`, scan, add Claude-judgment flags for context-specific jargon and empty phrasing).
- Run the 30-second self-check (six items, pass/fail).
- Infer ROAM and state it.
- List specific issues mapped to which of the 10 habits, with line references.
- Produce a rewrite.

## 8. `SKILL.md` content shape

Order matters because Claude reads top-to-bottom.

1. **Frontmatter** — `name`, `description` as above.
2. **The Iron Imperative** — one or two sentences. "Treat the reader's time as more valuable than your own."
3. **ROAM** (~30 lines) — four definitions, target sentence template, tiered gate rules.
4. **Mode routing** (~15 lines) — generative vs diagnostic flow, format-detection table mapping keywords to reference files.
5. **The 10 line-edit habits** (~50 lines, tight) — one bolded habit name + 1–2 line summary + concrete example each. Order: Write Short → Front-Load → Purge Passive → Replace Jargon → Eliminate Weasel Words → Be Direct → Use Numbers Wisely → Reveal Structure → Cut Cheery Filler → Earn the Title.
6. **The meaning-ratio check** (~25 lines) — the 30% rule, instruction to load `references/weasel-words.md`, guidance for adding Claude-judgment flags beyond the list, output format ("78% meaning ratio · 12 low-info words").
7. **The 30-second self-check** (~15 lines) — six items, verbatim from source, pass/fail format for diagnostic mode.
8. **Output templates** (~40 lines) — generative draft format, diagnostic scorecard format.
9. **Attribution footer** — Bernoff source citation.

## 9. Format playbook contents

### 9.1 `references/email.md` (~80 lines)

- Anatomy: subject line carries the ask; one-line greeting; one-sentence summary; facts on one topic; CTA with deadline; brief sign-off.
- Etiquette: don't compose important emails on phone; reply (not reply-all); skip empty acknowledgments; read latest message first; after three back-and-forths, call.
- Cold email template: <150 words, customized, what's-in-it-for-them, clear next step.

### 9.2 `references/blog.md` (~80 lines)

- Title and first sentences must hook (Google + link previews).
- Full structural toolkit: subheads, bullets with bolded openers, graphics.
- Shareable graphic with embedded URL.
- Promote on social; respond to comments; SEO last.
- ROAM target sentence template tailored for blog use.

### 9.3 `references/report.md` (~120 lines)

- Anatomy: title/subtitle → executive summary → setup → analysis → conclusions/recommendations → end matter.
- Story arc: setup → analysis → resolution.
- Executive summary written fresh at the end of every draft (not section recaps).
- Skimmable structural toolkit: short sections, descriptive headings, bullets with bold openers, tables, graphics.
- Conclusions don't hedge.

### 9.4 `references/social-and-press.md` (~100 lines)

- **Social** — ROAM target sentence; per-platform notes (Facebook reach, X brevity, LinkedIn cadence); post regularly; front-load every post; include a graphic; cold-DM rules.
- **Press release** — spokesperson voice; news in title; explain what you did and why it matters; cut superlatives; conversational tone.
- **Marketing pages** — short, "we" / "you", bullets and graphics, link to specs.

### 9.5 `references/weasel-words.md` (~50 lines)

Three categories with starter lists, plus an instruction to extend with judgment.

- **Qualifiers:** very, leading, generally, robust, considerable, growing, most, many, significant
- **Filler phrases:** across the landscape, at the end of the day, going forward, in order to, the fact that
- **Hedges:** it should be noted, arguably, perhaps, somewhat

Closing instruction: "This is a starter list. Also flag domain-specific jargon and any word a non-expert reader wouldn't understand."

## 10. Output templates

### 10.1 Generative output

```
ROAM target: After reading this, [readers] will realize [objective],
              so they will [action] and think of me as [impression].

[The draft itself, applying the 10 habits and matching format playbook.]
```

For the long tier, before drafting, Claude asks for any missing R/O/A/M elements (e.g., "I have R and M from your message but need O and A — what change in their thinking, and what action?").

### 10.2 Diagnostic output

```
SCORECARD
─────────────────────────────────────────
Meaning ratio: 68%  (target: ≥70%)
30-second check:
  ✓ Reader's time treated as more valuable
  ✗ Subject line carries the main message
  ✓ Conclusion in first 50 words
  ✗ Weasel/passive/jargon cut
  ✓ Nothing further to delete
  ✗ Reader's next action stated
ROAM (inferred): R=hiring managers · O=approve req ·
                 A=sign by Friday · M=organized analyst

ISSUES (mapped to habits)
─────────────────────────────────────────
1. [#5 Weasel words] "very significant growth" → "29% growth"
2. [#3 Passive] "decisions were made" → "we decided"
3. [#10 Title] subject line is "Some thoughts" — make it
   "Need approval on Q2 hiring req by Friday"
…

REWRITE
─────────────────────────────────────────
[Clean version applying every fix above.]
```

The scorecard format is fixed (parseable, scannable). The issue list and rewrite are free-form.

## 11. Distribution

### 11.1 `README.md` for the GitHub repo / skills.sh listing

- One-paragraph hook: what the skill does
- Install instructions: copy `writing-without-bullshit/` into the user's skills directory (or use whatever skills.sh install flow exists at publish time)
- Trigger summary: the frontmatter description plus 2–3 example prompts that activate it
- Attribution: derivative practical summary based on Josh Bernoff's *Writing Without Bullshit* (HarperBusiness, 2016); link to original
- License: MIT for the skill code/structure; methodology credit belongs to Bernoff

### 11.2 Repo metadata

- Repo name: `Writing-without-bullshit-skill`
- Topics/tags: `claude-skill`, `writing`, `editing`, `communication`
- Single-skill repo

## 12. Open questions

None outstanding at design time. All major decisions resolved:

| Decision | Choice |
|---|---|
| Packaging | One skill, progressive disclosure |
| Mode | Both generative and diagnostic |
| ROAM gate | Tiered (infer for short, ask for long) |
| Meaning ratio | Hybrid (starter list + Claude judgment) |
| Format playbooks | Email, blog, report, social-and-press |
| Supplementary sections | None — five core mechanics only |
| Habit summaries | Tight (1–2 lines each) |
| 30-second self-check | Verbatim from source |
| Diagnostic output | Scorecard + issue list + rewrite |

## 13. Attribution

Source: Bernoff, Josh. *Writing Without Bullshit: Boost Your Career by Saying What You Mean.* HarperBusiness, 2016. This skill is a derivative practical tool that operationalizes the methodology; the original book is the canonical reference.
