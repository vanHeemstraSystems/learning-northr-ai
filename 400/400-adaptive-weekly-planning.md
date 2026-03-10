# 400 — Adaptive Weekly Planning

Adaptive weekly planning is northr.ai’s “living schedule” loop:

- You define **direction(s)** once.
- northr.ai proposes a **weekly plan** (tasks + time blocks) based on your direction(s), constraints, and signals.
- You execute, check in, and the next plan adapts.

---

## Core concepts (plain language)

- **Direction**: your north star outcome (what “good” looks like).
- **Weekly plan**: the AI’s proposed breakdown for the current week (what to do + when).
- **Signals**: what you tell the AI via check-ins (done / not done / blockers / energy / availability).
- **Constraints**: calendar conflicts, working hours, and other immovables that the plan must respect.
- **Adaptation**: next week changes based on what actually happened this week.

---

## The weekly loop (how to use it)

1. **Start with direction(s)** (see `plan/year/README.md`).
2. **Review the weekly plan** in northr.ai (what it suggests and why).
3. **Schedule time blocks** around real constraints.
4. **Execute + check in** (mark outcomes done, note blockers).
5. **Let the next week adapt** based on your signals and results.

This repo mirrors that loop with lightweight artifacts in `plan/week/`.

---

## Example: Week 11 entry → a scheduled time block

You captured a concrete weekly action here:

- `plan/week/2026-wk11.md` (Tue March 10 2026): “Document northr.ai in GitHub”

To make this “adaptive” (not just a note), you want it to become either:

- a **scheduled time block** (on your calendar), or
- a **task** tied to a direction (with a planned time window).

**Recommended flow:**

1. In northr.ai, create/confirm the **direction** this supports.
2. Add the work item (“Document northr.ai in GitHub”) to the weekly plan.
3. Allocate a time block (e.g., 60–90 minutes).
4. After execution, check in with the outcome (done / partial / blocked + why).

---

## Google Calendar + Gmail: will Tuesday activity show up?

**Only if it’s actually scheduled as a calendar event/time block.**

- If you **only recorded the activity in GitHub / this repo**, that does **not** automatically create a Google Calendar event.
- If northr.ai is connected to Google Calendar, it can use your calendar to:
  - **read constraints** (existing events/availability), and
  - (depending on your northr.ai settings) **write scheduled time blocks** into a chosen calendar (you’ve set up a calendar named “Northr” in `GOOGLE_CALENDAR_SETUP.md`).

**How to verify quickly:**

- Open Google Calendar → enable/inspect the **“Northr”** calendar.
- Check the date (Tue 2026-03-10).
- If there’s no event, schedule the block in northr.ai (or directly in Google Calendar) and refresh.
  - Repo shortcut: import `plan/week/2026-03-10-document-northrai-github.ics` into the **Northr** calendar.

### How to import the repo `.ics` into Google Calendar (Northr)

1. Open Google Calendar (web): `https://calendar.google.com/`
2. In the left sidebar, under **Other calendars**, click the **+**
3. Choose **Import**
4. **Select file from your computer**:
   - `plan/week/2026-03-10-document-northrai-github.ics`
5. **Add to calendar**: choose **Northr**
6. Click **Import**

**Verify:** make sure the **Northr** calendar is visible, then check Tue 2026-03-10 for the event.

Gmail connection typically helps northr.ai pull context (e.g., commitments/tasks) depending on what features you’ve enabled, but **it won’t “magically” log work you did** unless you explicitly schedule it or check in.

---

## Repo artifacts (how we’ll keep using Git)

- **Week entries**: `plan/week/YYYY-wkNN.md`
- **Week summary template**: `plan/week/README.md`
- **High-level progress**: `PROGRESS_TRACKER.md`

---

## Next

- If you haven’t yet: complete `500/500-working-with-ai-suggestions.md` next (that’s where “accept/decline time blocks” becomes a skill).
- Then: `600/600-progress-tracking-and-check-ins.md` to make adaptation “stick.”
