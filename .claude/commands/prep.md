Generate a targeted interview prep plan for a specific company.

## Step 1 — Identify the company

The engineer may pass a company name as an argument (e.g. `/prep Stripe`). If no argument is given, read `Interviews.md` and list the companies that have an upcoming interview date — ask which one to prep for.

If the named company doesn't have a file in `companies/`, let the engineer know and ask them to share what they know about the role and interview format so you can still build a plan.

## Step 2 — Gather context

Run the following in parallel:

1. Read `companies/<CompanyName>.md` — full interview history, prep notes, known format, contacts, what round is next.
2. Read `.ai/daily-context.md` — engineer's profile, LeetCode level, language preference, known weak spots, current prep pace, NeetCode 150 progress.
3. Read `Interviews.md` — confirm the next interview date, stage, and any notes.
4. Read the most recent 5 daily notes in `daily/` — understand what's been studied recently, what problems were solved, what felt hard, what's been neglected.

## Step 3 — Build the prep plan

Calculate how many days are left until the interview. Today's date is available from the system. Use this to set the urgency level and the depth of the plan.

Then write a prep plan with the following sections:

---

### Situation

One short paragraph: the interview date, format (phone screen / technical / onsite / system design), time remaining, and the most important thing to know going into this. Be direct — if time is short and there are known weak spots, say so clearly.

### Priority Focus Areas

Based on what's known about the company's interview style (from the company file, any community reports, the role level) and the engineer's current weak spots (from context), list 2–4 specific things to focus on. Each item should explain:
- **What**: the topic or pattern
- **Why**: why this company / this role / this round is likely to test it
- **How**: the specific problems or resources to use

Be concrete. Don't say "practice dynamic programming" — say "LC 139 Word Break and LC 322 Coin Change, because this company has asked DP problems with string inputs in recent phone screens."

### Day-by-Day Study Plan

Break the remaining days into a daily schedule. Each day gets:
- A topic or pattern focus
- 2–3 specific LeetCode problems (with LC number and title) or a system design topic
- Time estimate (assume the engineer's stated daily prep time from their profile)

If there are 6+ days, group the last 1–2 days as review and simulation:
- Day N-1: timed mock problems, no looking anything up
- Day N (day before): light review only, no new material, rest

If there are 3 days or fewer, be ruthless about prioritization — only the highest-signal topics, no breadth.

### Known Weak Spots to Address

Pull from the engineer's coaching notes and recent daily notes. List specific things that have come up as gaps (e.g. "struggled with the heap optimization in Meeting Rooms II" or "hasn't touched backtracking yet"). For each one, give one concrete action.

### Day-Of Checklist

Practical logistics and mental prep:
- [ ] Confirm time, link/phone number, and format (from the company file)
- [ ] Decide on language before sitting down — don't choose in the moment
- [ ] Set up environment: editor, language, any boilerplate ready
- [ ] Clarify before coding: ask about constraints, edge cases, expected output
- [ ] State approach out loud before writing a single line
- [ ] Write a working solution first, then optimize — don't premature-optimize
- [ ] Test with edge cases yourself: empty input, single element, large input, duplicates
- [ ] If stuck: say what you're thinking, ask for a hint gracefully, keep moving

Add any company-specific or round-specific items based on what's in the company file (e.g. "CodeSignal scores testing separately — always write edge case tests" or "this is a recruiter screen — have your 60-second pitch ready").

### Questions to Ask

Generate 4–6 targeted questions based on the company, the role, and the round. These should not be generic — pull from what's known about the company and what the engineer cares about (from their profile: target level, company type preference, comp expectations).

For technical rounds: ask about tech stack, team structure, biggest current challenges.
For recruiter screens: ask about process, timeline, comp range, team size.
For onsites: ask about engineering culture, what success looks like in the first 90 days, how decisions get made.

### After the Interview

Remind them to:
- Send a thank-you note within 24 hours (to recruiter and/or interviewer if they have contact info)
- Run `/daily` the next morning and log everything they remember in the Notes section while it's fresh — what was asked, how it went, what they'd do differently

---

## Step 4 — Save a summary to the company file

Append a `## Prep Plan` section to `companies/<CompanyName>.md` with:
- Date the plan was generated
- Interview date and format
- The priority focus areas (condensed to bullet points)
- The day-of checklist

This way the engineer can reference the checklist without re-running the command.

## Tone

This is a high-stakes moment. Be direct and specific — not reassuring for the sake of it. If there are 2 days left and a known gap, say that clearly and give them the highest-ROI actions, not a comprehensive study plan they can't finish. Confidence comes from preparation, not pep talks.