# On-Request Diagnostics

Loaded only when user asks for one of these after a draft or edit. Never volunteered. Deliver what was asked, nothing else. Don't repeat the draft unless it changed.

| User says (or similar) | Output |
|---|---|
| "show the ROAM," "who's this for," "what's the target" | Target sentence: *After reading this, [readers] will realize [objective], so they will [action] and think of me as [impression].* |
| "show the scorecard," "score it," "how does it rate" | SCORECARD block below |
| "what did you change," "show the issues," "explain the edits" | ISSUES list, one line each: `[#N HabitName] "before" → "after"` |
| "flag the weasel words," "show low-info words," "mark the filler" | Original text with low-info words **bolded**, then `Low-info words: ~NN of ~NNN (meaning ratio ~NN%)` |
| "full rewrite," "go harder," "rewrite it properly," "restructure it" | Full rewrite per `SKILL.md` definition. Text only, same output contract. |
| "show your work," "everything" | ROAM → scorecard → issues → rewrite, in that order |

## Scorecard block

```
SCORECARD
Meaning ratio: ~NN%  (target ≥70%; approximate)
30-second check:
  ✓/✗ Reader's time treated as more valuable
  ✓/✗ Subject/title carries the main message
  ✓/✗ Conclusion in first 50 words
  ✓/✗ Weasel/passive/jargon/AI tells cut
  ✓/✗ Nothing further to delete
  ✓/✗ Reader's next action stated
  ✓/✗ No invented numbers, names, dates, quotes
ROAM (inferred): R=… · O=… · A=… · M=…
```

Score the text as it stood before your edit when the user asks about their original; score your draft when they ask about yours. Say which.

## Meaning ratio

Load `references/weasel-words.md`. Flag every match plus Claude-judgment flags (domain jargon, empty intensifiers, buzzwords off the list). `meaning ratio ≈ 1 − (low-info words / total words)`. Below 70% → rewrite warranted. Counts are estimates; label them `~`.

## Issues list

Map each fix to its habit number from `SKILL.md`. Before → after, verbatim phrases, one line each. Group by habit if more than ~10.
