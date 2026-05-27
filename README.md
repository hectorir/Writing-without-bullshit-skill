# Writing Without Bullshit — a Claude skill

[![skills.sh](https://skills.sh/b/hectorir/Writing-without-bullshit-skill)](https://skills.sh/hectorir/Writing-without-bullshit-skill)

Claude skill for drafting + reviewing business prose using Bernoff's *Writing Without Bullshit*. Auto-triggers for emails, blog posts, reports, social posts, press releases, marketing copy.

## What it does

- **Pre-draft ROAM check** — Readers, Objective, Action, iMpression. Inferred for short, asked for long.
- **10 line-edit habits** applied while drafting (write short, front-load, purge passive, replace jargon, kill weasel words, be direct, use numbers wisely, reveal structure, cut cheery filler, earn every title).
- **Meaning-ratio diagnosis** — built-in low-info word list + Claude judgment for context jargon.
- **30-second self-check** before any draft ships.
- **Format playbooks** for email, blog, report, social/press — loaded when format detected.

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
- "Review this blog post and tighten it." *(paste prose)*
- "Help me write the executive summary for this report."
- "Rewrite this LinkedIn post — it's too long."
- "I need a press release announcing the Series B."

Triggered → skill applies ROAM, 10 habits, matching playbook. Diagnostic → scorecard, issue list (mapped to 10 habits), clean rewrite.

## What it skips

Code, comments, commits, tech specs. Methodology is for prose.

## Attribution

Derivative tool based on Bernoff's *Writing Without Bullshit* (HarperBusiness, 2016). ROAM, 10 habits, meaning ratio, self-check, format playbooks — all Bernoff's. Operationalized for Claude. Original is canonical.

Book: https://www.amazon.com/Writing-Without-Bullshit-Boost-Career/dp/0062477153

## License

MIT (structure + code). Methodology credit: Bernoff.
