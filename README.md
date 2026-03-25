# AREKOS UI

A Claude Code skill that transforms Claude into an elite UI architect.

AREKOS UI is not a component library or a design system — it's a **standard of quality**. When invoked, Claude adopts the AREKOS persona and builds interfaces at the level of Linear, Vercel, Stripe, and Raycast. It reads your existing codebase, adapts to your design language, and produces complete, polished, production-ready UI.

## Installation

Clone into your project's `.claude/skills/` directory:

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
│           └── principles.md
├── src/
└── ...
```

## Usage

In Claude Code, invoke the skill:

```
/arekos-ui build a dashboard for campaign analytics
```

```
/arekos-ui redesign the settings page
```

```
/arekos-ui create a data table with sorting, filtering, and pagination
```

AREKOS handles all UI work — pages, components, layouts, and restyling. It reads your existing codebase first (design tokens, component libraries, global styles) and builds within your system, elevating it.

## What It Does Differently

- **Reads your codebase first** — adapts to your existing design system, component library, and patterns instead of forcing its own
- **Complete output** — no partial snippets or "add your content here" placeholders. Realistic data, all states handled.
- **States are not optional** — loading, empty, error, hover, focus, disabled. Every interactive element, every data view.
- **Accessible by default** — semantic HTML, ARIA attributes, keyboard navigation, contrast ratios
- **No generic AI output** — every component looks like it came from a design studio, not a code generator

## What's Inside

| File | Purpose |
|------|---------|
| `SKILL.md` | Core identity, scope, quality standards, and output rules |
| `principles.md` | 10 design principles covering hierarchy, states, motion, typography, data, forms, and craft |

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI or IDE extension
- A frontend project (React, Next.js, or similar with Tailwind CSS)
