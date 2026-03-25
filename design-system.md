# AREKOS UI — Design System: Warm Obsidian

## Color Palette

### CSS Custom Properties
```css
:root {
  /* Base */
  --ak-bg: #0d0b0a;
  --ak-bg-raised: #161312;
  --ak-bg-elevated: #1e1b19;
  --ak-bg-hover: #252220;
  --ak-surface: #1a1715;

  /* Accent — Burnt Amber */
  --ak-accent: #c2703e;
  --ak-accent-hover: #d4834f;
  --ak-accent-muted: rgba(194, 112, 62, 0.12);
  --ak-accent-subtle: rgba(194, 112, 62, 0.06);

  /* Secondary — Oxidized Copper */
  --ak-secondary: #8b6c4f;
  --ak-secondary-hover: #9d7d5e;
  --ak-secondary-muted: rgba(139, 108, 79, 0.12);

  /* Tertiary — Muted Sage */
  --ak-tertiary: #7a8c6e;
  --ak-tertiary-hover: #8a9c7e;
  --ak-tertiary-muted: rgba(122, 140, 110, 0.12);

  /* Text */
  --ak-text: #ede8e3;
  --ak-text-secondary: #9e9590;
  --ak-text-tertiary: #6b6360;
  --ak-text-disabled: #4a4442;

  /* Borders */
  --ak-border: rgba(237, 232, 227, 0.08);
  --ak-border-strong: rgba(237, 232, 227, 0.15);
  --ak-border-accent: rgba(194, 112, 62, 0.3);

  /* Semantic */
  --ak-success: #7a8c6e;
  --ak-warning: #c2973e;
  --ak-danger: #c4564a;
  --ak-danger-muted: rgba(196, 86, 74, 0.12);
  --ak-info: #5c8a9e;
}
```

### Tailwind `@theme inline` Block
```css
@theme inline {
  --color-ak-bg: var(--ak-bg);
  --color-ak-bg-raised: var(--ak-bg-raised);
  --color-ak-bg-elevated: var(--ak-bg-elevated);
  --color-ak-bg-hover: var(--ak-bg-hover);
  --color-ak-surface: var(--ak-surface);
  --color-ak-accent: var(--ak-accent);
  --color-ak-accent-hover: var(--ak-accent-hover);
  --color-ak-accent-muted: var(--ak-accent-muted);
  --color-ak-accent-subtle: var(--ak-accent-subtle);
  --color-ak-secondary: var(--ak-secondary);
  --color-ak-secondary-hover: var(--ak-secondary-hover);
  --color-ak-secondary-muted: var(--ak-secondary-muted);
  --color-ak-tertiary: var(--ak-tertiary);
  --color-ak-tertiary-hover: var(--ak-tertiary-hover);
  --color-ak-tertiary-muted: var(--ak-tertiary-muted);
  --color-ak-text: var(--ak-text);
  --color-ak-text-secondary: var(--ak-text-secondary);
  --color-ak-text-tertiary: var(--ak-text-tertiary);
  --color-ak-text-disabled: var(--ak-text-disabled);
  --color-ak-border: var(--ak-border);
  --color-ak-border-strong: var(--ak-border-strong);
  --color-ak-border-accent: var(--ak-border-accent);
  --color-ak-success: var(--ak-success);
  --color-ak-warning: var(--ak-warning);
  --color-ak-danger: var(--ak-danger);
  --color-ak-danger-muted: var(--ak-danger-muted);
  --color-ak-info: var(--ak-info);
  --font-ak-sans: var(--font-geist-sans);
  --font-ak-mono: var(--font-geist-mono);
}
```

## Spacing Scale

Base unit: `4px` (`0.25rem`). Use only these named steps:

| Token | Value | Use |
|-------|-------|-----|
| `--ak-space-xs` | `0.25rem` (4px) | Inline icon gaps |
| `--ak-space-sm` | `0.5rem` (8px) | Tight element gaps |
| `--ak-space-md` | `0.75rem` (12px) | Default padding |
| `--ak-space-lg` | `1rem` (16px) | Card padding, section gaps |
| `--ak-space-xl` | `1.5rem` (24px) | Component separation |
| `--ak-space-2xl` | `2.5rem` (40px) | Section padding |
| `--ak-space-3xl` | `4rem` (64px) | Major section breaks |
| `--ak-space-4xl` | `6rem` (96px) | Page-level vertical rhythm |

## Typography Scale

Use `clamp()` for fluid sizing. Font: Geist Sans (already loaded in Next.js).

| Token | Size | Weight | Tracking | Use |
|-------|------|--------|----------|-----|
| `--ak-text-display` | `clamp(2.5rem, 5vw, 4rem)` | 700 | `-0.03em` | Page titles, hero headings |
| `--ak-text-heading` | `clamp(1.5rem, 3vw, 2rem)` | 700 | `-0.02em` | Section headings |
| `--ak-text-subheading` | `clamp(1.125rem, 2vw, 1.25rem)` | 500 | `-0.01em` | Card titles, subsections |
| `--ak-text-body` | `0.9375rem` (15px) | 400 | `0` | Body copy |
| `--ak-text-small` | `0.8125rem` (13px) | 400 | `0.01em` | Secondary text, descriptions |
| `--ak-text-caption` | `0.6875rem` (11px) | 500 | `0.06em` | Labels, uppercase captions, overlines |
| `--ak-text-mono` | `0.8125rem` (13px) | 400 | `0` | Code, data values |

**Weight rules:**
- 400: Body text, descriptions
- 500: Emphasis, subheadings, labels, buttons
- 700: Headings only

No 300 (too thin). No 600 (creates visual noise with 500 and 700).

## Shadow System

Only 3 levels. All warm-tinted:

```css
--ak-shadow-resting: 0 1px 2px rgba(13, 11, 10, 0.3);
--ak-shadow-lifted: 0 4px 12px rgba(13, 11, 10, 0.4), 0 1px 3px rgba(13, 11, 10, 0.2);
--ak-shadow-elevated: 0 12px 40px rgba(13, 11, 10, 0.5), 0 2px 8px rgba(13, 11, 10, 0.3);
```

- **Resting**: Default state for raised surfaces. Barely visible.
- **Lifted**: Hover states. Card feels physically picked up.
- **Elevated**: Modals, dropdowns, popovers. Clear layer separation.

## Border Radius

Only two values:
- `2px` (`rounded-sm`): Subtle. Use on inputs, badges, small elements.
- `4px` (`rounded`): Maximum. Use on cards, buttons, containers.

Exception: Avatars and status dots may use `rounded-full`.

## Motion

**Easing curve**: `cubic-bezier(0.16, 1, 0.3, 1)` — swift arrival, hard decelerate (objects have weight).

**Duration rules:**
- Micro-interactions (hover, focus): `120ms`
- State changes (tab switch, expand): `180ms`
- Entry animations: `200ms` max
- Stagger between items: `40ms`

**Entry pattern:**
```css
@keyframes ak-enter {
  from {
    opacity: 0;
    transform: translateY(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.ak-enter {
  animation: ak-enter 200ms cubic-bezier(0.16, 1, 0.3, 1) both;
}
```

**Hover pattern:**
```css
.ak-lift {
  transition: transform 120ms cubic-bezier(0.16, 1, 0.3, 1),
              box-shadow 120ms cubic-bezier(0.16, 1, 0.3, 1);
}
.ak-lift:hover {
  transform: translateY(-1px);
  box-shadow: var(--ak-shadow-lifted);
}
```

## Scrollbar
```css
::-webkit-scrollbar { width: 5px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: rgba(237, 232, 227, 0.1); border-radius: 2px; }
::-webkit-scrollbar-thumb:hover { background: rgba(237, 232, 227, 0.2); }
```
