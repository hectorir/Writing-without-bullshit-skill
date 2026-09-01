# Writing Without Bullshit — a Claude skill

[![skills.sh](https://skills.sh/b/hectorir/Writing-without-bullshit-skill)](https://skills.sh/hectorir/Writing-without-bullshit-skill)

Claude skill for drafting + reviewing business prose using Bernoff's *Writing Without Bullshit*. Auto-triggers for emails, replies, blog posts, reports, social posts, press releases, marketing copy.

## What you get

Ask for a draft → you get the draft. Paste prose and say "tighten" → you get the tightened prose. No preamble, no scorecard, no "here's what I changed," no closing offer. Diagnostics exist, but only when you ask.

Under the hood, every draft passes through:

- **ROAM** — Readers, Objective, Action, iMpression. Inferred silently for short pieces. For long pieces (blog, report, press release) the skill asks once for anything missing, with a best guess for each so you can answer "yes."
- **10 line-edit habits** — write short, front-load, purge passive, replace jargon, kill weasel words, be direct, use numbers wisely, reveal structure, cut cheery filler and AI tells, earn every title.
- **No invented facts.** Missing number, date, name, or quote → `[placeholder]` in the draft. Never a plausible fake.
- **30-second self-check** before anything ships.
- **Format playbooks** for email, blog, report, social/press. Loaded when the format is detected.

## Two edit strengths

| You say | You get |
|---|---|
| tighten, trim, edit, fix, shorten, clean up, polish, proofread, any other review verb, or paste with no verb | **Light edit.** Your voice, paragraph order, and word choices stay. Weasel words, filler, passives, buried leads, and AI tells go. Never longer than the original. |
| rewrite, redo, overhaul, restructure, go harder | **Full rewrite.** Every habit plus the format playbook. Restructured, re-titled, front-loaded. Your facts stay yours. |

Start with a light edit. Say "go harder" if you want the full treatment.

## Diagnostics on request

After any draft or edit:

| Say | Get |
|---|---|
| "show the ROAM" | The target sentence: *After reading this, [readers] will realize [objective], so they will [action] and think of me as [impression].* |
| "show the scorecard" | Approximate meaning ratio + the 30-second check as ✓/✗ + inferred ROAM |
| "what did you change" | Every edit mapped to its habit: `[#5 Weasel Words] "significant" → "29%"` |
| "flag the weasel words" | Your original with low-info words bolded, plus a count |
| "full rewrite" / "go harder" | The full rewrite |
| "show your work" | All of the above, in order |

## Install

`skills` CLI places skill in right directory for any compatible agent:

```bash
npx skills add hectorir/Writing-without-bullshit-skill
```

Or manually:

```bash
git clone https://github.com/hectorir/Writing-without-bullshit-skill.git \
  ~/.claude/skills/writing-without-bullshit
```

Auto-triggers from frontmatter; no config needed.

## Example prompts that activate it

- "Draft an email to my manager about the Q3 hiring freeze."
- "Tighten this." *(paste prose)*
- "Help me write the executive summary for this report."
- "Rewrite this LinkedIn post — it's too long."
- "I need a press release announcing the Series B."
- "Reply yes and say I'll send the deck Thursday."

## What it skips

Code, code comments, commit messages, tech specs. Methodology is for prose.

## Files

```
SKILL.md                       entry point: output contract, ROAM, habits, self-check
references/email.md            email anatomy, replies, cold email
references/blog.md             hook, structure, ending
references/report.md           exec summary, story arc, recommendations
references/social-and-press.md social, press release, marketing page
references/weasel-words.md     qualifiers, filler, hedges, AI tells
references/diagnostics.md      scorecard, issues list, meaning ratio (on request only)
```

## Attribution

Derivative tool based on Bernoff's *Writing Without Bullshit* (HarperBusiness, 2016). ROAM, 10 habits, meaning ratio, self-check, format playbooks — all Bernoff's. Operationalized for Claude. Original is canonical.

Book: https://www.amazon.com/Writing-Without-Bullshit-Boost-Career/dp/0062477153

## License

MIT (structure + code). Methodology credit: Bernoff.
