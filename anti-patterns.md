# AREKOS UI — Banned Patterns

These patterns are STRICTLY FORBIDDEN. If your output contains any of these, it is not AREKOS UI. Rewrite it.

## Banned Colors
- No indigo (`#6366f1`, `indigo-*`) as primary or accent
- No violet/purple (`violet-*`, `purple-*`) as primary or accent
- No cyan/teal neon combos (`cyan-*` paired with `indigo-*`)
- No cold blue-blacks (`#09090b`, `#0a0a0a`, `zinc-950`)
- No pure white text (`#ffffff`, `#fafafa`, `#f4f4f5`)
- No `from-indigo-* via-violet-* to-cyan-*` gradient combos

## Banned Border Radius
- No `rounded-lg` (8px)
- No `rounded-xl` (12px)
- No `rounded-2xl` (16px)
- No `rounded-3xl` (24px)
- No `rounded-full` on containers or cards (circles on avatars/icons only)
- Maximum allowed: `rounded` (4px) or `rounded-sm` (2px)

## Banned Backgrounds & Effects
- No `backdrop-blur` / glassmorphism
- No `blur-[80px]`, `blur-[100px]`, `blur-[120px]` glow orbs
- No `bg-gradient-to-r from-indigo-500 to-violet-500` or similar AI-gradient backgrounds
- No `bg-clip-text text-transparent` gradient text
- No `bg-card/50` semi-transparent card backgrounds
- No `shadow-[0_0_30px_rgba(...)]` glow shadows
- No `shadow-[0_0_20px_rgba(...)]` glow shadows

## Banned Animations
- No `animate-pulse` on decorative elements
- No `animate-[glow-pulse_*]` ambient glow cycling
- No `animate-[float_*]` floating/bobbing
- No `animate-bounce`
- No transitions longer than `duration-200` (200ms)
- No stagger delays over 50ms between elements

## Banned Layouts
- No full-page centered-everything hero sections with centered text + centered buttons
- No uniform 3-column card grids where all cards look identical
- No `text-center` as the default alignment (left-align by default)
- No `max-w-4xl mx-auto text-center` centered content blocks as primary layout

## Banned Component Patterns
- No cards with `border border-border bg-card` as the only styling
- No buttons with glow hover states (`hover:shadow-[0_0_*_rgba(...)]`)
- No full-border input fields (`border border-border rounded-xl`)
- No pill-shaped navigation tabs (`rounded-full` or `rounded-xl` tab containers)
- No "Popular" badges on pricing cards floating in top-right corners
- No five-star rating rows as decorative filler
- No generic placeholder text ("Get Started", "View Components", "Learn More")

## Banned Typography
- No `text-5xl sm:text-7xl` oversized centered hero headings as the default pattern
- No `text-muted` as the only text color differentiation strategy
- No uniform font weights (everything must have clear weight hierarchy)

## The Test
Before outputting any component, ask: "Could Lovable or a generic AI tool have produced this?" If yes, redesign it.
