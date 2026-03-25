# Discovery Checklist

Before writing any UI code, complete this checklist. Skip nothing.

## 1. Styling Configuration

Search for and read (in order of priority):
- `tailwind.config.ts` / `tailwind.config.js` — custom theme extensions, colors, fonts, spacing
- `globals.css` / `app.css` / `index.css` — CSS custom properties, `@theme` blocks, base styles
- `postcss.config.*` — any PostCSS plugins that affect styling
- `theme.ts` / `tokens.ts` — if the project uses a programmatic design token system

**What to note:**
- Color palette (primary, secondary, accent, semantic colors)
- Font families and type scale
- Spacing scale (if customized beyond Tailwind defaults)
- Border radius conventions
- Shadow definitions
- Animation/transition utilities
- Dark mode strategy (class-based, media query, or CSS variables)

## 2. Existing Components

Scan these directories (adapt to project structure):
- `src/components/ui/` — primitive components (Button, Input, Card, Dialog, etc.)
- `src/components/` — composed components
- `components/` — alternative location
- `app/components/` — if using Next.js app router

**What to note:**
- What primitives already exist (don't rebuild them)
- Naming conventions (PascalCase files? index.ts barrels?)
- Props patterns (variant props? className passthrough? forwardRef?)
- How components handle states (loading, disabled, error)

## 3. Component Libraries

Check `package.json` dependencies for:
- `@radix-ui/*` — Radix primitives (unstyled, accessible)
- `@headlessui/react` — Headless UI (unstyled, accessible)
- `class-variance-authority` + `clsx` + `tailwind-merge` — shadcn/ui pattern
- `@shadcn/ui` or a `components.json` at root — shadcn setup
- `@mui/material` — Material UI
- `@shopify/polaris` — Shopify Polaris
- `@mantine/core` — Mantine
- `@chakra-ui/react` — Chakra UI
- `antd` — Ant Design

**If a library is present, use it.** Don't fight the existing system.

## 4. Icons

Check for:
- `lucide-react` — Lucide icons (most common in modern React)
- `@heroicons/react` — Heroicons
- `react-icons` — Multi-library icon pack
- `@phosphor-icons/react` — Phosphor icons
- `@radix-ui/react-icons` — Radix icons
- Custom SVG icons in `src/icons/` or `public/icons/`

**Use what's installed.** Don't import a new icon library when one exists.

## 5. Animation & Motion

Check for:
- `framer-motion` / `motion` — Framer Motion
- `@formkit/auto-animate` — AutoAnimate
- `react-spring` — React Spring
- CSS animations in globals (keyframes, transition utilities)
- Tailwind animation extensions in config

## 6. Existing Pages

Read 2-3 existing pages to absorb the design language:
- What's the spacing rhythm? (tight 4px, standard 8px, loose 16px?)
- How is color used? (accent sparingly? semantic colors?)
- What's the typography pattern? (size, weight, tracking)
- How are sections separated? (borders, space, background shifts?)
- What's the general density? (compact data-heavy? spacious marketing?)

## 7. Layout Patterns

Look for:
- Root layout structure (`app/layout.tsx`) — sidebar? top nav? both?
- Page-level patterns — full-width? constrained? split?
- Grid vs flexbox conventions
- Responsive breakpoint usage (`sm:`, `md:`, `lg:`)

## 8. Forms

If the task involves forms, also check for:
- `react-hook-form` — form state management
- `zod` / `yup` / `joi` — validation schemas
- Existing form components (FormField, FormLabel, FormMessage patterns)
- How validation errors are currently displayed
