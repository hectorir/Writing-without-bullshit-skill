# Writing Without Bullshit — a Claude skill

[![skills.sh](https://skills.sh/b/hectorir/Writing-without-bullshit-skill)](https://skills.sh/hectorir/Writing-without-bullshit-skill)

A Claude skill that helps you draft and review business prose using Josh Bernoff's *Writing Without Bullshit* methodology. It auto-triggers when you ask Claude to write or review emails, blog posts, reports, social posts, press releases, or marketing copy.

## What it does

- **Pre-draft ROAM check** — Readers, Objective, Action, iMpression. Inferred for short pieces, asked for long ones.
- **10 line-edit habits** applied while drafting (write short, front-load, purge passive, replace jargon, kill weasel words, be direct, use numbers wisely, reveal structure, cut cheery filler, earn every title).
- **Meaning-ratio diagnosis** with a built-in low-info word list plus Claude judgment for context-specific jargon.
- **30-second self-check** before any draft ships.
- **Format playbooks** for email, blog, report, and social/press — loaded only when the format is detected.

## Install

The fastest path is the `skills` CLI, which places the skill in the right directory for any compatible agent:

```bash
npx skills add hectorir/Writing-without-bullshit-skill
```

Or install manually by cloning into your Claude skills directory:

```bash
git clone https://github.com/hectorir/Writing-without-bullshit-skill.git \
  ~/.claude/skills/writing-without-bullshit
```

The skill auto-triggers based on its frontmatter description; no further configuration required.

## Example prompts that activate it

- "Draft an email to my manager about the Q3 hiring freeze."
- "Review this blog post and tighten it." *(paste prose)*
- "Help me write the executive summary for this report."
- "Rewrite this LinkedIn post — it's too long."
- "I need a press release announcing the Series B."

When triggered, the skill applies ROAM, the 10 habits, and the matching format playbook automatically. For diagnostic requests, it returns a scorecard, an issue list mapped to the 10 habits, and a clean rewrite.

## What it skips

Code, code comments, commit messages, technical specifications. The methodology is for prose communication.

## Attribution

Derivative practical tool based on Josh Bernoff's *Writing Without Bullshit: Boost Your Career by Saying What You Mean* (HarperBusiness, 2016). The methodology — ROAM, the 10 habits, the meaning ratio, the self-check, the format playbooks — is Bernoff's. This skill operationalizes it for use inside Claude. The original book is the canonical reference and is well worth reading in full.

Book: https://www.amazon.com/Writing-Without-Bullshit-Boost-Career/dp/0062477153

## License

MIT for the skill structure and code. Methodology credit belongs to Josh Bernoff.
