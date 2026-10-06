# Implementation — New-Role Setup Kit

Use this folder at the start of every new role to get the toolkit running and gather context quickly.

| File | Use it for |
|---|---|
| [CHECKLIST.md](CHECKLIST.md) | Phased setup, from before Day 1 through Month 2. This is the source of truth for "where am I on setup?" |
| [day1-intake.md](day1-intake.md) | First conversations with engineering, ops, and UX, and how to synthesize them |
| [Smoke-Test.md](Smoke-Test.md) | Check commands and connectors before you need them |
| [cowork-setup-guide.md](cowork-setup-guide.md) | Prompts for scheduled tasks (Monday briefing, nightly synthesis, KPI pulse, retro prep) and on-demand tasks (exec brief, stakeholder pre-mortem, requirements sharding, data synthesis) |
| [JTBDs.md](JTBDs.md) | The seven jobs this toolkit has to do. Use them to judge whether output is useful |
| [jtbd-stack-mapping.md](jtbd-stack-mapping.md) | Which part of the stack covers each job, and what each one depends on |

## Lessons from the last role (read these first)

1. **Connector approval is the critical path.** Planned automations can sit blocked for months waiting on approval to connect company systems. Ask in week 1 and record the answer.
2. **Keep company content out of this repo from day one.** Filled-in context, avatars of real people, initiative docs, and data exports go in a work repo or on employer systems. Cleaning them out later means rewriting history or starting over.
3. **Write down other people's decisions as they happen.** Chat history expires. `/log-observed` with a confidence level is cheap, and recovering lost context isn't.
4. **Move lessons out of AI memory and into the toolkit.** The most useful rules (analysis rigor, writing style, exec reporting preferences) built up in Claude's memory, not in the repo. Each month, write them into `CLAUDE.md` or `02-Methods-and-Tools/skills/` with company specifics removed.
5. **Keep one copy of each instruction.** Copies of `CLAUDE.md` in other tools' files drifted within weeks. Commands live in `00-Meta/commands/`, and everything else should point to them.
