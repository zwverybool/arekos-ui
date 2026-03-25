# AREKOS UI

A Claude Code skill that transforms Claude into a specialized UI architect with its own design language.

AREKOS UI is not a component library — it's a **design identity**. When invoked, Claude adopts the AREKOS persona and builds interfaces using the **Warm Obsidian** design system: warm blacks, burnt amber accents, sharp edges, asymmetric layouts, and weight-based motion.

Every output is designed to be unmistakably distinct from generic AI-generated UI.

## Design Language: Warm Obsidian

| Element | Approach |
|---------|----------|
| **Color** | Warm blacks (`#0d0b0a`), burnt amber (`#c2703e`), oxidized copper (`#8b6c4f`), muted sage (`#7a8c6e`) |
| **Shape** | Sharp. Max border-radius: `4px`. No rounded corners. |
| **Layout** | Asymmetric, left-heavy, editorial. CSS Grid with deliberate negative space. |
| **Surface** | Solid backgrounds. Cards use 3px left accent bars, not full borders. No glassmorphism. |
| **Motion** | Objects have weight. `cubic-bezier(0.16, 1, 0.3, 1)`. 120ms micro, 200ms max. |
| **Type** | Geist Sans. Three weights: 400, 500, 700. Overline captions at 11px uppercase. |

## Installation

Copy this folder into your project's `.claude/skills/` directory:

```bash
# From your project root
mkdir -p .claude/skills
cp -r /path/to/arekos-ui .claude/skills/arekos-ui
```

Or clone directly:

```bash
mkdir -p .claude/skills
git clone https://github.com/zainwaraich/arekos-ui.git .claude/skills/arekos-ui
```

Your project should look like:

```
your-project/
├── .claude/
│   └── skills/
│       └── arekos-ui/
│           ├── SKILL.md
│           ├── design-system.md
│           ├── component-patterns.md
│           └── anti-patterns.md
├── src/
└── ...
```

## Usage

In Claude Code, invoke the skill with:

```
/arekos-ui build a dashboard for campaign analytics
```

```
/arekos-ui redesign the settings page
```

```
/arekos-ui create a modal for confirming deletions
```

AREKOS handles all UI work — pages, components, layouts, and restyling. It will refuse non-UI tasks (backend, APIs, DevOps).

## What's Inside

| File | Purpose |
|------|---------|
| `SKILL.md` | Core identity, persona, scope, and output rules |
| `design-system.md` | Complete token system — colors, spacing, typography, shadows, motion |
| `component-patterns.md` | Canonical implementations for buttons, cards, inputs, tables, modals, etc. |
| `anti-patterns.md` | Banned patterns — everything AREKOS will never produce |

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI or IDE extension
- A React/Next.js project with Tailwind CSS (the generated code uses Tailwind classes)
- Geist Sans font (ships with Next.js by default)
