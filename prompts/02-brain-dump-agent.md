# Agent 2: The Brain Dump Agent

**Cadence:** Daily, at the end of the workday
**Role:** The catch-up agent. Feeds the memory system (the brain) with everything
*humans* actually said and decided today.

It reviews every email thread, every IM thread, and most importantly every meeting
note, then sorts the day into decisions, actions and risks. It deliberately ignores
automated noise (that is the Signal Agent's job). Nothing is saved until you confirm.

---

## Prompt

```text
It's the end of my workday. Go through today's human interactions only: my meeting
notes, plus the email and Teams threads where real people are talking. Deliberately
ignore the automated noise: ITSM tickets, change-record emails, monitoring alerts,
system notifications.

Pull out every decision, every action, every risk. Show me one consolidated list and
ask me clarifying questions until you're confident it's accurate. Once I confirm,
update this week's dashboard with the relevant items.
```

## The one discipline that makes or breaks this agent

**Take notes for every discussion.** Capture them as Loop components, either generated
by a meeting facilitator or written by hand. The agent can only be as good as the
trail you leave, and structured notes are a trail it can actually read.
No notes, no brain.

## Why human and system signals are split

Mixing human signal (daily) with the system firehose (weekly) is how every reporting
tool drowns. The Brain Dump handles humans; the [Signal Agent](03-signal-agent.md)
handles machines. Different cadence, different noise profile, different agent.
