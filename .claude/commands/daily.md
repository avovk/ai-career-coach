Read the context below, then create or update the daily note for today (or tomorrow if it makes more sense given the content).

## Step 1 — Gather context

Run the following in parallel:

1. List all files in `daily/` and read the most recent 7 days of notes (by filename date, format `yyyy-mm-dd.md`). Today's date is available from the system.
2. Read `Interviews.md` to get the current company pipeline and stages.
3. Read every file in `companies/` to get the full picture of each company's status, upcoming interviews, and prep notes.
4. Read `.ai/daily-context.md` — this is the persistent coaching context file. It contains the user profile (including name), carry-forward coaching notes, prep state, and anything else that doesn't belong in a single day's note.

If `.ai/daily-context.md` is empty or missing a User Profile section, stop and prompt the engineer to run `/setup` first.

## Step 2 — Sync company files from daily note Notes sections

Engineers write raw notes about companies, recruiter calls, and interview experiences directly in the **Notes section** of each daily note. Before writing today's note, parse any company-related information from those Notes sections and propagate it to the right files.

**For each piece of new information found:**
- Update the relevant `companies/<Company>.md` file — fill in "How it went", add timeline entries, update prep notes, capture decisions
- Update `Interviews.md` — if a stage changed, a new date was set, or a company should be marked Rejected/Withdrawn/Ghosted
- Do not duplicate content that's already in the company file from a previous sync

**What counts as company-related information to sync:**
- Post-interview debrief notes ("the interview went like this...")
- Recruiter call summaries ("they said X, waiting on Y")
- Decisions made ("I decided to withdraw", "I replied to them saying...")
- New contacts, dates, or process details mentioned
- Any company field that still says "TBD" but the engineer has since described in a daily note

**What to leave in the daily note:**
- LeetCode solutions and code snippets — these stay in the Notes section, do not copy to company files
- General study reflections not tied to a specific company

Run all company file updates before writing today's daily note, so the note can reference up-to-date information.

## Step 3 — Write the daily note

The file goes in `daily/yyyy-mm-dd.md`. Use today's date unless there's a clear reason to write a note for tomorrow (e.g., nothing left to do today but something important happens tomorrow morning).

If the file already exists, update it in place — don't create a duplicate. Preserve any sections the engineer has already written or checked off.

### Note format

```
# yyyy-mm-dd

## Waiting for Reply

[Table of all pending two-way communication items — anyone waiting on the engineer to respond, or anyone they're waiting to hear back from. Include: Person, Company, what's being waited on, and date of last contact. Remove rows once resolved. Omit this section entirely if nothing is pending.]

| Person | Company | Waiting On | Last Contact |
|--------|---------|------------|--------------|
| ... | ... | ... | ... |

---

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

## Suggested LeetCode

[Exactly 3 problems to do today. For each, include: LC number, title, difficulty, and 1-sentence reason why it's the right pick today.

Picking rules:
- Default to round-robin across NeetCode sections — pick from different sections each day, not sequential completion of one section at a time.
- Weight toward topics relevant to upcoming interviews (e.g., if a technical screen is close, favor patterns the company has been known to ask).
- Occasionally (roughly 1 in 4 days) substitute one problem with a review of something already solved — a good candidate is any problem solved more than a week ago or one where the approach felt shaky. Flag it as "(review)".
- If the engineer is under time pressure or drained, lean toward easier picks. If they have a full study day, push toward medium.
- Never suggest a Hard unless explicitly requested.
- If tracking NeetCode 150, reference `docs/neetcode-150.md` for progress and next unchecked problems.

Format each item as:
1. **LC NNN — Title** (Difficulty) — reason
2. ...
3. ...

Do NOT include the pattern/topic type (e.g. "Two Pointers", "Sliding Window", "Stack") in the problem description — it gives away the solution approach. The reason should be about why it's the right problem to do today, not what technique it uses.]

---

## Topic Tips — [Pattern Name]

[Include this section whenever the suggested problems cover a new or recently-started pattern. Skip it if today's problems are all in patterns that have been covered recently.

Include:
- The core template / approach in the engineer's preferred language (from .ai/daily-context.md), in a fenced code block with the language tag (e.g. ```python or ```js)
- 2–3 language-specific gotchas or built-ins that matter for this pattern
- One concrete example tied to today's suggested problem(s)

Keep it short — this is a quick reference, not a tutorial.]

---

## Notes

[Leave this section empty — it's for the engineer to fill in: progress updates, meeting notes, LeetCode session notes, recruiter call notes, anything. Company-related notes written here will be parsed and synced to company files automatically on the next /daily run.]
```

## Step 4 — Update .ai/daily-context.md

After writing the daily note, rewrite `.ai/daily-context.md` with a cleaned-up version. This file is the skill's own memory — keep it tight and useful.

**Remove:**
- Interviews or prep items whose dates have passed
- Companies that are closed (Rejected, Withdrawn, Ghosted, Offer accepted/declined)
- Reminders that have been acted on (e.g., "update company file after call" once the file is updated)
- Anything now captured in company files that doesn't need repeating here

**Keep or add:**
- User Profile section (never remove or overwrite this)
- Current job search status (urgency level, pipeline health)
- Any upcoming interviews within the next 2 weeks with date, time, format
- Technical prep state — current pace, language choices, known weak spots, NeetCode 150 progress if tracking
- Coaching notes specific to this engineer that should persist (patterns, tendencies, things to watch)
- Cross-company reminders or follow-ups not yet acted on

Keep the file concise. It should be readable in under a minute. Don't duplicate what's already in company files — just reference them.

## Coaching guidelines

- If an interview is within 3 days, flag it 🔴 and include specific prep actions (not just "prepare")
- If an interview is 4–7 days out, it should appear as 🟠 with a concrete study plan item
- If a company has gone quiet or a stage hasn't moved in 2+ weeks, flag it
- If LeetCode pace looks too slow relative to upcoming interviews, call it out directly
- Carry forward any uncompleted 🔴 or 🟠 items from the previous day's note
- Reference specific files with markdown links when relevant (e.g., `[Company prep notes](../companies/CompanyName.md)`)
- Minimum 1 LeetCode problem per day is the baseline — flag if this hasn't happened