# Agent 1: The Dashboard Engineer

**Cadence:** Weekly (run once to scaffold, then weekly to clone a fresh copy)
**Role:** Builds and maintains the structure of the operating system. The most
technical agent, used mostly at the start.

It produces a single self-contained HTML file backed by one JSON data object that
models your world as an operating system: products, projects, people and budget,
all connected. Every week it clones last week's file into a new dated copy so you
never overwrite history.

---

## Prompt

```text
You're my dashboard engineer. Build me a single self-contained HTML file backed by
one JSON data object that models my world as an operating system: products,
projects, team members and budget, all connected, so people own projects, projects
roll up to products, and products carry a roadmap and KPIs. Keep it simple and
editable from that one data object.

And here's the important part: every Monday, start from a copy of last week's file,
rename it with the new week's date, and only ever update the new copy, never
overwrite the previous ones. I want a full weekly history I can look back on.
```

## Why the weekly clone matters

Each week is a new dated copy, cloned from the last. The other agents update *this*
week's brain without destroying last week's, so you capture history for free and can
always diff "where were we then vs. now." This is what makes the Wrap-up agent
(agent 4) possible.

## Tips

- One file, one JSON object. No platform, no database server, no integration project.
- Keep the data model interconnected (people -> projects -> products -> roadmap/KPIs)
  so a single update ripples correctly everywhere.
- See [`/dashboard`](../dashboard) for a fully sanitized sample of the output.
