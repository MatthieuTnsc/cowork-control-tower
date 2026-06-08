<div align="center">

# Control Tower

### An AI operating system for managers, run by four small agents.

I offloaded the "plumbing" of my job (gathering status, consolidating it, reformatting
it five ways) onto a handful of AI agents that shadow the real work and keep a single
living dashboard true. This repo is the open-sourced boilerplate: the prompts, a fully
sanitized sample dashboard, and the workflow structure.

Built and demoed in **Microsoft Copilot Cowork**.

[Read Part 1](https://www.linkedin.com/posts/matthieutournesac_what-happens-when-you-offload-reporting-ugcPost-7467624247583027201-waBV/) &nbsp;·&nbsp; Read Part 2 _(link coming with the post)_

</div>

---

## The idea in one minute

Every reporting tool I ever tried died the same death: it asked people to stop working
and go log what they just did. Nobody does that consistently.

So I flipped it. Instead of asking the team to feed a system, I treat my work as an
**operating system** (a living model where people own projects, projects roll up to
products, products carry roadmaps, KPIs and budget) and I point small agents at the
actual work to keep that model current.

- Information is **generated** at the point of work (meetings, email, chat, system tools).
- It is **processed** by four agents.
- It is **consolidated** into one weekly source of truth everyone can pull from.

> An interactive version of this diagram (with animated flow) lives at
> [`diagrams/operating-system-flow-v2.html`](diagrams/operating-system-flow.html).
> Open it in a browser.

---

## The four agents

Each agent is just a prompt on a schedule. Full prompts are in [`/prompts`](prompts).

| #   | Agent                                                  | Cadence           | What it does                                                                                                                                                      |
| --- | ------------------------------------------------------ | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [Dashboard Engineer](prompts/01-dashboard-engineer.md) | Weekly            | Builds the structure (one HTML + JSON brain) and clones a fresh dated copy each week so history is never overwritten.                                             |
| 2   | [Brain Dump](prompts/02-brain-dump-agent.md)           | Daily, end of day | Reads the day's _human_ interactions (meeting notes, email, chat), sorts them into decisions / actions / risks, excludes automated noise, and asks before saving. |
| 3   | [Signal](prompts/03-signal-agent.md)                   | Weekly            | Sweeps the _system_ firehose (ITSM, Finance tools, monitoring) and extracts incidents, changes and KPI movements with their latest status.                        |
| 4   | [Wrap-Up 1:1](prompts/04-wrap-up-agent.md)             | Weekly            | Reviews this week vs last week and challenges you with open questions so nothing is missed or hallucinated.                                                       |

A human stays in the loop: **every agent asks for confirmation before anything is
saved to the brain.**

---

## The sample dashboard

[`dashboard/control-tower-dashboard-sample.html`](dashboard/control-tower-dashboard-sample.html)
is a single self-contained file (open it in any browser). It is **fully sanitized**:
real structure, completely invented placeholder data. Tabs cover Products, Projects,
Roadmap, Demands, Changes, Budget and Team, all rendered from one `DASHBOARD_DATA`
object at the bottom of the file.

To make it yours, edit that one object.

> Tip: GitHub does not render HTML files in the browser. To preview the dashboard
> without cloning, prefix the raw URL with a service like `htmlpreview.github.io`, or
> just download the file and open it locally.

---

## Quick start

1. **Scaffold the dashboard.** Give the [Dashboard Engineer prompt](prompts/01-dashboard-engineer.md)
   to your AI assistant and describe your own products, projects, people and budget.
   Or start from the sample and edit the data object.
2. **Wire up the four agents** using the prompts in [`/prompts`](prompts).
3. **Put them on a schedule (your cron of agents).** In Copilot Cowork, use scheduled
   prompts: Brain Dump every weekday evening, Signal every Friday, Wrap-Up every
   Saturday morning. Once scheduled, the system runs itself and pings you only when it
   needs a decision.
4. **Take notes for every meeting** as Loop components (facilitator-led or manual).
   The Brain Dump is only as good as the trail you leave.

---

## Repo structure

```
.
├── README.md
├── LICENSE
├── prompts/
│   ├── 01-dashboard-engineer.md
│   ├── 02-brain-dump-agent.md
│   ├── 03-signal-agent.md
│   └── 04-wrap-up-agent.md
├── dashboard/
│   └── control-tower-dashboard-sample.html   # sanitized sample, edit DASHBOARD_DATA
├── diagrams/
│   ├── operating-system-flow.png             # the flow, as an image
│   ├── operating-system-flow.html            # static HTML version
│   └── operating-system-flow-v2.html         # animated, connected version
└── assets/
    └── banner.png
```

---

## A few principles worth keeping

- **Split human from system signal.** Daily for humans, weekly for machines. Do not merge them.
- **Protect the human-in-the-loop.** The confirmation step is what keeps the brain trustworthy.
- **Never overwrite, always clone.** Weekly dated copies give you history and a baseline to diff against.
- **Notes are non-negotiable.** No notes, no brain.

---

## Adapt it, then tell me how

This was very much tailor-made for my own role and built for demo purposes, so it will
not fit your world out of the box. That's the point of open-sourcing it.

- How would you improve it?
- Where does it fall short?
- How would you adapt it to a different role, team or toolset?

Open an issue or a discussion, fork it, break it. Let's exchange and make it better
together. PRs welcome.

---

## Disclaimer

This is a conceptual proof of concept from piloting emerging tools across the digital
workplace, shared as a build pattern, not a finished product. The agents need
supervision and the data model has blind spots. All data in the sample dashboard is
fictional.

## License

[MIT](LICENSE)
