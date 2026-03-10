# 200 — Core Concepts

## The Adaptive Planning Model

Traditional planning tools are static: you write a plan, the world changes, the plan goes stale. northr.ai is designed to be *adaptive* — the plan continuously re-forms around your actual context.

```
You define direction
        │
        ▼
AI generates weekly plan
        │
        ▼
You execute and check in
        │
        ▼
AI adapts next week's plan
        │
        └──────────────────► repeat
```

---

## Key Concepts

### Direction

Your **direction** is the single, stable north star that guides all AI planning decisions. It should be:

- **Outcome-focused** — what you want to achieve, not what you want to do
- **Time-bounded** — with a target date or horizon
- **Singular** — one primary direction at a time (multiple are supported but can dilute focus)

*Good:* "Deliver the security bid by July 15"
*Weak:* "Work on the bid stuff"

---

### Weekly Plan

Each week, the AI generates a structured plan containing:

- **Time blocks** — scheduled slots for focused work
- **Tasks** — concrete actions mapped to your direction
- **Buffers** — protected time for the unexpected

The plan is a *proposal*, not a mandate. You review and adjust it.

---

### Check-in

A **check-in** is how you signal your progress to the AI. It answers:

- What did I complete?
- What is blocked?
- What changed in my context?

Check-ins are the AI's primary feedback signal. The more honestly you check in, the better the adaptive plan becomes.

---

### AI Suggestions

northr.ai surfaces **suggestions** when it detects an opportunity to improve your plan:

- Re-prioritise a task that's been deferred too often
- Protect deep work time that's been eroded by meetings
- Break a large task into smaller steps

You can accept, modify, or dismiss each suggestion.

---

### The Planning Cycle

| Phase | Cadence | Activity |
|---|---|---|
| Direction review | Quarterly or on change | Update your north star |
| Weekly plan | Every Monday (or configured day) | Review and accept AI-generated plan |
| Daily check-in | Daily | Log progress, flag blockers |
| Weekly retrospective | Every Friday | Reflect and signal context changes |

---

## The "Plan Less" Principle

northr.ai's philosophy is that planning itself is a form of overhead. The goal is to get planning out of the way so you can spend time *executing*. The AI absorbs scheduling complexity — you focus on doing.

---

## Next

→ [300 — Defining Your Direction](../300/300-defining-direction.md)
