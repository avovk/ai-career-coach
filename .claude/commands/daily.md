Read the context below, then create or update the daily note for today (or tomorrow if it makes more sense given the content).

## Step 1 — Gather context

Run the following in parallel:

1. List all files in `daily/` and read the most recent 7 days of notes (by filename date, format `yyyy-mm-dd.md`). Today's date is available from the system.
2. Read `Interviews.md` to get the current company pipeline and stages.
3. Read every file in `companies/` to get the full picture of each company's status, upcoming interviews, and prep notes.
4. Read `.ai/daily-context.md` — this is the persistent coaching context file. It contains the user profile (including name), carry-forward coaching notes, prep state, and anything else that doesn't belong in a single day's note.

If `.ai/daily-context.md` is empty or missing a User Profile section, stop and prompt the engineer to run `/setup` first.

## Step 2 — Write the daily note

The file goes in `daily/yyyy-mm-dd.md`. Use today's date unless there's a clear reason to write a note for tomorrow (e.g., nothing left to do today but something important happens tomorrow morning).

If the file already exists, update it in place — don't create a duplicate. Preserve any sections the engineer has already written or checked off.

### Note format

```
# yyyy-mm-dd

## Overview

[3–5 sentences acting as a career coach. Cover: what's on the radar today and this week, what's most important and why, any risks or things slipping, and any direct coaching they need to hear. Be specific — reference actual companies, dates, and interview stages by name. Be honest and direct, not cheerleader-y. Use the engineer's name naturally once or twice — not on every sentence, just enough to feel personal.]

---

## Todo

[Prioritized list of action items. Every item gets one of these prefix emojis:
  🔴 = Important for today — consequences if skipped
  🟠 = Should prioritize — meaningful progress this week
  🟢 = Chill — good to do, low urgency

Order items by priority descending. Be specific: name the company, the problem set, the action. No vague items like "study" — say what to study and why.]

---

## Topic Tips

[If the engineer is working on a new LeetCode topic or pattern today, include a short tips block here:
- 2–4 key insights on the pattern (when to use it, core idea, common pitfall)
- Language-specific gotchas for their preferred language (from .ai/daily-context.md)
- All code examples in fenced blocks with the language tag, e.g. ```js

Omit this section entirely if there is no new topic today or it's a review/mixed day.]

---

## Notes

[Leave this section empty — it's for the engineer to fill in: progress updates, LeetCode session notes, recruiter call notes, anything.]
```

## Step 3 — Update .ai/daily-context.md

After writing the daily note, rewrite `.ai/daily-context.md` with a cleaned-up version. This file is the skill's own memory — keep it tight and useful.

**Remove:**
- Interviews or prep items whose dates have passed
- Companies that are closed (Rejected, Withdrawn, Ghosted, Offer accepted/declined)
- Reminders that have been acted on
- Anything now captured in company files that doesn't need repeating here

**Keep or add:**
- User Profile section (never remove or overwrite this)
- Current job search status (urgency level, pipeline health)
- Any upcoming interviews within the next 2 weeks with date, time, format
- Technical prep state — current pace, language choices, known weak spots, NeetCode 150 progress if tracking
- Coaching notes specific to this engineer that should persist
- Cross-company reminders or follow-ups not yet acted on

Keep the file concise. It should be readable in under a minute. Don't duplicate what's already in company files — just reference them.

## Coaching guidelines

- If an interview is within 3 days, flag it 🔴 and include specific prep actions (not just "prepare")
- If an interview is 4–7 days out, it should appear as 🟠 with a concrete study plan item
- If a company has gone quiet or a stage hasn't moved in 2+ weeks, flag it
- If LeetCode pace looks too slow relative to upcoming interviews, call it out directly
- Carry forward any uncompleted 🔴 or 🟠 items from the previous day's note
- Reference specific files with markdown links when relevant (e.g., `[Company prep notes](../companies/CompanyName.md)`)
- If the engineer is tracking NeetCode 150, suggest the next unchecked problem(s) from `docs/neetcode-150.md` that fit the current topic
- Minimum 1 LeetCode problem per day is the baseline — flag if this hasn't happened