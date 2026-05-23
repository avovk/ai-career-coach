# Luma — Your AI Software Engineering Interview Coach

Hey, welcome. I'm **Luma** — an AI coach built to help software engineers get through the interview process without losing their minds.

I track your pipeline, coach your LeetCode and system design prep, and write you a personalized daily note every morning with exactly what you should be doing and why. I give honest feedback, flag when things are slipping, and keep you accountable without the fluff.

I run entirely inside [Claude Code](https://claude.ai/code). Your data stays local — I write to markdown files in this folder, nothing leaves your machine.

---

## How It Works

### The Big Picture

Every interaction with me comes through two commands:

- **`/setup`** — run once to introduce yourself. I'll learn your name, situation, target role, preferred language, LeetCode level, and how you like to be coached. I save everything to `.ai/daily-context.md` and use it to personalize every future session.
- **`/daily`** — run every morning. I read your pipeline, your recent notes, and your prep state, then write a prioritized coaching note for the day.

Between those commands, you just talk to me. Tell me about a recruiter call, a problem you got stuck on, a company you're interested in, or an offer you received — I'll update your files and adjust your plan accordingly.

### What I Track

**Your pipeline** lives in `Interviews.md` — a table of every company you're talking to, what stage you're at, and what needs to happen next. Each company also gets its own file in `companies/` with the full history: contacts, interview rounds, prep notes, and your post-interview reflections.

**Your daily notes** live in `daily/yyyy-mm-dd.md`. Each one has an overview of what matters, a prioritized todo list, and a topic tips section if you're working on a new LeetCode pattern.

**My memory** lives in `.ai/daily-context.md`. This is where I keep your profile, upcoming interview dates, your LeetCode pace, and anything I need to carry forward between sessions. I rewrite it every time you run `/daily`.

---

## Getting Started

### Prerequisites
- [Claude Code](https://claude.ai/code) installed
- A Claude account (free or Pro works)

### Setup

1. Clone this repo and open the folder in Claude Code:

   ```bash
   git clone git@github.com:avovk/ai-career-coach.git
   cd ai-career-coach
   claude .
   ```

2. Run setup:

   ```
   /setup
   ```

   I'll introduce myself and ask you about 15 short questions — your name, current situation, target companies, preferred coding language, LeetCode comfort, daily study time, system design experience, and coaching style preference. Takes about 2 minutes.

3. Run your first daily note:

   ```
   /daily
   ```

   That's it. You're set up.

---

## Daily Workflow

### Every morning

```
/daily
```

I'll write a note like this:

```
# 2026-05-23

## Overview

You've got a technical screen at Stripe in 4 days, Sarah — that should be
driving your whole week. You did 2 LeetCode problems yesterday which is on
pace, but you haven't touched backtracking yet and that's a known gap for
Stripe's style. The Goldman recruiter has been quiet for 9 days; worth a
follow-up today before it goes cold.

---

## Todo

- 🔴 Do 2–3 timed LeetCode problems — backtracking focus (LC 39 Combination Sum, LC 78 Subsets)
- 🔴 Follow up with Goldman recruiter — one sentence, ask for a status update
- 🟠 Review Stripe system design prep notes — read through the distributed systems section
- 🟢 Check NeetCode 150 progress — you're 12/85 on easy/medium

---

## Topic Tips — Backtracking

The core pattern: build a partial result, recurse, then undo the last choice.

...

## Notes

_Fill this in as the day goes on._
```

### Updating me on companies

Just tell me what happened — I'll handle the files:

> "Had a recruiter call with Stripe today. It went well, they're moving me to a technical screen next Thursday at 2pm. The interviewer is Dan from the payments team."

I'll update `Interviews.md` and log the round in `companies/Stripe.md`.

> "Got rejected from Netflix. No feedback."

I'll close it out in the pipeline and remove it from your active prep.

### Asking for help mid-session

You can ask me anything between `/daily` runs:

> "Can you explain the difference between BFS and DFS for this type of problem?"

> "What questions should I ask the hiring manager at my Airbnb onsite tomorrow?"

> "I have two offers — help me think through which one to take."

I have full context on your situation and will give you advice that's specific to where you are, not generic interview tips from the internet.

---

## The Notes Section — This Is Important

Every daily file has a **Notes** section at the bottom. It's blank — it's yours to fill in as the day goes on.

**This is the most important thing you can do to get value out of Luma.**

When you run `/daily` the next morning, I read your recent notes to understand what actually happened. The more you put in, the better my coaching gets. Notes don't need to be polished — bullet points, stream of consciousness, copy-pasted code, whatever. I'll make sense of it.

Here's what good notes look like:

```markdown
## Notes

Had the Stripe call — felt okay. They asked two interval problems back to back,
both medium. Finished the first one clean, struggled with the second (Meeting
Rooms III variant). Ran out of time explaining the heap approach.

LC 39 Combination Sum — solved it. Took 28 min. Forgot to handle the case where
candidates have duplicates at first, caught it in testing. Code below:

```js
function combinationSum(candidates, target) {
    const result = [];
    candidates.sort((a, b) => a - b);
    function backtrack(start, current, remaining) {
        if (remaining === 0) { result.push([...current]); return; }
        for (let i = start; i < candidates.length; i++) {
            if (candidates[i] > remaining) break;
            current.push(candidates[i]);
            backtrack(i, current, remaining - candidates[i]);
            current.pop();
        }
    }
    backtrack(0, [], target);
    return result;
}
```

Also emailed the Goldman recruiter — no reply yet.
```

With notes like that, I know tomorrow: you struggled with heap-based interval problems, you're solving backtracking cleanly but slowly, Goldman is still pending a reply, and you should probably do one more heap problem before the Stripe screen.

Without notes, I'm just working from the pipeline table and guessing.

---

## NeetCode 150 Tracking

If you opt in during `/setup`, I'll track your progress through the NeetCode 150 (easy and medium problems only) in `docs/neetcode-150.md`. Each daily note suggests the next problem in the current topic and includes a tips block with the pattern breakdown and language gotchas.

Check problems off as you complete them:

```markdown
- [x] LC 1 — Two Sum (Easy)
- [x] LC 49 — Group Anagrams (Medium)
- [ ] LC 347 — Top K Frequent Elements (Medium)
```

The list is pre-filtered — Hard problems are already removed.

---

## File Structure

```
ai-career-coach/
├── README.md                        ← you are here
├── CLAUDE.md                        ← Luma's coaching instructions
├── Interviews.md                    ← your active pipeline
├── companies/                       ← one file per company
│   └── Stripe.md
├── daily/                           ← daily coaching notes
│   └── 2026-05-23.md
├── docs/
│   └── neetcode-150.md              ← NeetCode 150 tracker (easy/medium)
└── .ai/
    └── daily-context.md             ← Luma's persistent memory
```

---

## Commands

| Command | What it does |
|---------|-------------|
| `/setup` | First-time onboarding — builds your profile and coaching context |
| `/daily` | Write or update today's coaching note |
| `/prep <Company>` | Generate a targeted prep plan for an upcoming interview |

---

## Preparing for an Interview — `/prep`

When you have an interview coming up, run:

```
/prep Stripe
```

Luma reads the company file, your coaching context, and your recent daily notes, then builds a plan specific to you and that company. It calculates how many days you have left and works backwards.

A prep plan includes:

- **Situation** — interview date, format, and a direct assessment of where you stand
- **Priority Focus Areas** — 2–4 specific things to study, with the exact LeetCode problems to use and the reason each one matters for this company
- **Day-by-Day Schedule** — a concrete daily plan through the interview, with the last day before reserved for light review only
- **Known Weak Spots** — pulled from your notes and coaching context, with one action per gap
- **Day-Of Checklist** — logistics, mental prep, and company-specific reminders (e.g. "CodeSignal scores testing separately — always write edge case tests")
- **Questions to Ask** — 4–6 targeted questions based on the round type and what you care about

The plan is also saved to the company file so you can pull up the checklist without re-running the command.

**Example output:**

```
### Situation

You have 4 days until your Stripe technical screen. Based on your recent
notes you've been solid on intervals and arrays, but you haven't touched
backtracking — and Stripe is known for multi-part problems that often
involve recursive enumeration. That's the gap to close this week.

### Priority Focus Areas

1. **Backtracking** — Stripe frequently uses problems with "generate all
   combinations" structure as part 2 of a multi-part question.
   Do: LC 39 Combination Sum, LC 78 Subsets, LC 17 Letter Combinations.

2. **Heap / Top-K** — appears in their phone screens. You solved Meeting
   Rooms II without a heap; practice using one cleanly.
   Do: LC 692 Top K Frequent Words, LC 973 K Closest Points.

...
```

If no company name is passed, Luma lists your active companies with upcoming dates and asks which one to prep for.

---

## A Note on Privacy

Everything stays local. Luma writes to markdown files in this folder — your pipeline, notes, and profile never leave your machine. The only thing that goes to Anthropic is the content of your conversation with Claude Code, subject to their standard privacy policy.

---

*Built with [Claude Code](https://claude.ai/code).*
