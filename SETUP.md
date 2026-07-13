# Body Optimization — CoWork Setup

## What this plugin is

An 8-agent performance system that runs automated weekly and monthly reviews. It does **not** handle daily logging — that happens in Chat.

---

## Step 1: Install the Plugin

1. Open Claude Code desktop
2. Go to **Plugins** → **Install from file**
3. Select `body-optimization.plugin`

---

## Step 2: Create the CoWork Project

1. Open **CoWork**
2. Create a new project: `Body Optimization`
3. When prompted to add agents, select all 8:
   - Data Manager
   - Weekly Review Agent
   - Monthly Data Analyst
   - Nutritionist (Dr. Stacy Sims)
   - Training Coach (Dr. Peter Attia)
   - Sleep & Recovery Coach (Dr. Matthew Walker)
   - Brain Health Coach (Dr. Andrew Huberman)
   - Habits Coach (James Clear)

---

## Step 3: Set Up Automations

### Weekly Review — Every Monday
1. In the CoWork project, go to **Automations**
2. Create new automation:
   - **Name:** Weekly Review
   - **Schedule:** Every Monday at 9:00 AM
   - **Starting agent:** Weekly Review Agent
   - **Prompt:**
     ```
     It's Monday. Run the weekly review exactly as defined in your instructions.

     Send the full check-in first and STOP — do not call Data Manager, do not
     analyze anything, do not produce a report of any kind until Liz has
     replied. Only after her reply: pull real training data from GitHub via
     Data Manager, incorporate any Nutritionist/Training Coach summaries she
     pastes, call only the specialists whose domain shows a real signal, and
     deliver one full-spectrum report. Never invent a number that wasn't in
     her reply or in the real GitHub data. After delivering it, save the full
     report to tracking/weekly-review-[date].md and push it, exactly as
     defined in your instructions.
     ```

### Monthly Analysis — First of Every Month
1. Create another automation:
   - **Name:** Monthly Analysis
   - **Schedule:** 1st of every month at 9:00 AM
   - **Starting agent:** Monthly Data Analyst
   - **Prompt:**
     ```
     It's the 1st. Run the monthly analysis exactly as defined in your
     instructions.

     Read this month's weekly reports from tracking/weekly-review-[date].md
     — that archive is your only data source, do not call Data Manager and
     do not fetch GitHub directly. Note plainly any weeks that are missing
     or incomplete rather than smoothing over the gap. Identify trends,
     correlations, and red flags across the month, call relevant specialists
     for deeper insight, deliver the monthly report with next month's
     priorities, then save the full report to
     tracking/monthly-review-[year-month].md and push it.
     ```

---

## How It Works

```
Monday automation fires
    → Weekly Review Agent sends the full check-in and STOPS
    → Liz replies with her answers (+ any Nutritionist/Training Coach summaries)
    → Requests real training data from Data Manager (GitHub)
    → Scans for issues across weight, nutrition, training, cycle, sleep, mood, other flags
    → Routes to specialists ONLY if their domain shows a real signal
    → Synthesizes one full-spectrum report — never invents a missing number

Monthly automation fires
    → Monthly Data Analyst wakes up
    → Reads this month's weekly reports from tracking/ (its only data source)
    → Flags any missing or incomplete weeks explicitly
    → Spots trends and correlations across real, already-vetted numbers
    → Calls relevant specialists for deeper analysis
    → Delivers monthly report + next month priorities
    → Saves the full report to tracking/monthly-review-[year-month].md and pushes it
```

## Token Efficiency

Only the agents that are needed run. A clean week = Data Manager + Weekly Review only. Issues flagged = max 2–3 specialists. Never all 8 at once.

---

## Daily Logging (Separate from this Plugin)

Daily macros and workouts are logged in **Chat**, not CoWork:
- Open Chat → load **Nutritionist** → log your macros
- Open Chat → load **Training Coach** → log your workout

See the Chat project setup for instructions.
