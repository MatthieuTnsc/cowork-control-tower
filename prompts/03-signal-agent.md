# Agent 3: The Signal Agent

**Cadence:** Weekly (run once, before the weekly wrap-up)
**Role:** Handles everything *system-generated*. Runs weekly, not daily, precisely
because the volume is so high that a daily pass would just be noise on noise.

It sweeps the firehose (ITSM change records, Finance tool notifications, monitoring
and app dashboards), extracts the facts of the week (incidents, changes, approvals,
KPI movements), and reflects the latest status of each. Same pattern as the Brain
Dump: it asks before it writes.

---

## Prompt

```text
Before my weekly wrap-up, sweep the system-generated noise I skip day to day: ITSM
change records, Finance tool notifications, monitoring and app-dashboard emails in my
inbox.

Summarize what actually matters this week (incidents, changes, approvals, KPI
movements) and for each one, reflect its latest status, not just the first alert. Ask
me anything you're unsure about, then update this week's dashboard with what we agree.
```

## Why "latest status" matters

An incident opened Monday and resolved Thursday should show as resolved, not
lingering. The Signal Agent reconciles a week of noisy notifications into the current
state of each item, not a pile of alerts.
