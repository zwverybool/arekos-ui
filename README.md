# AREKOS UI

A Claude Code skill that transforms Claude into an elite UI architect.

AREKOS UI is not a component library or a design system — it's a **standard of quality**. When invoked, Claude adopts the AREKOS persona: it reads your existing codebase, adapts to your design language, and produces complete, polished, production-ready interfaces at the level of Linear, Vercel, and Stripe.

## Installation

```bash
mkdir -p .claude/skills
git clone https://github.com/zwverybool/arekos-ui.git .claude/skills/arekos-ui
```

Your project should look like:

```
your-project/
├── .claude/
│   └── skills/
│       └── arekos-ui/
│           ├── SKILL.md
│           ├── principles.md
│           ├── anti-patterns.md
│           ├── agents/
│           │   └── arekos-reviewer.md
│           └── references/
│               ├── discovery-checklist.md
│               ├── component-patterns.md
│               └── accessibility.md
├── src/
└── ...
```

## Usage

```
/arekos-ui build a dashboard for campaign analytics
```

```
/arekos-ui redesign the settings page
```

```
/arekos-ui create a data table with sorting and pagination
```

## How It Works

AREKOS follows a 4-phase workflow for every task:

1. **Discovery** — Reads your codebase first. Tailwind config, global styles, existing components, installed libraries. Understands what you have before building anything new.

2. **Design Direction** — States the visual strategy before writing code. What's the hierarchy? What existing patterns to use? What states need handling?

3. **Build** — Produces complete, working code with all states (hover, focus, loading, empty, error), accessibility (semantic HTML, ARIA, keyboard nav), and responsive behavior.

4. **Review** — Launches an auditor subagent that checks the output against quality principles, accessibility standards, and anti-patterns. Issues are fixed before delivery.

## What's Inside

| File | Purpose |
|------|---------|
| `SKILL.md` | Core identity, 4-phase workflow, output rules |
| `principles.md` | 10 design principles — hierarchy, states, motion, typography, forms, craft |
| `anti-patterns.md` | Forbidden patterns — generic AI slop that AREKOS will never produce |
| `agents/arekos-reviewer.md` | Auditor subagent — reviews output against all quality standards |
| `references/discovery-checklist.md` | What to read in a codebase before writing any UI |
| `references/component-patterns.md` | Quality checklists for buttons, cards, forms, tables, modals, nav, states |
| `references/accessibility.md` | Non-negotiable a11y standards — ARIA, keyboard, contrast, focus, screen readers |

## What Makes AREKOS Different

- **Reads your codebase first** — adapts to your existing design system instead of imposing one
- **Complete output** — no partial snippets, no placeholders. Realistic data, all states, all breakpoints.
- **Self-auditing** — built-in reviewer catches accessibility issues, missing states, and anti-patterns before you see them
- **Opinionated** — has strong design taste and will make creative decisions rather than producing safe, generic output
- **UI-only scope** — refuses non-UI tasks. When you invoke AREKOS, you get a focused UI architect, not a general assistant.

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI, desktop app, or IDE extension
- A frontend project (React, Next.js, or similar)
- Tailwind CSS (preferred, but works with any CSS approach)
