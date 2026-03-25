# Anti-Patterns

These patterns are **forbidden**. If your output contains any of them, rewrite it before delivering. These are the hallmarks of generic AI-generated UI — the exact thing AREKOS exists to prevent.

---

## Layout Slop

- **Centered-everything hero layouts**: Giant centered heading + centered subtext + centered button. The default output of every AI tool. Break the symmetry. Use asymmetric layouts, left-aligned content, split layouts, editorial grids.
- **Cookie-cutter 3-column equal grids**: Three identical cards in a row with the same icon + heading + description pattern. If you need three cards, make them visually distinct — vary the content type, size, or emphasis.
- **Walls of cards**: Pages that are just rows and rows of identically-styled cards with no hierarchy. Use featured items, list views, mixed sizes, or summary stats to break monotony.
- **`max-w-4xl mx-auto text-center` as the only layout pattern**: Not every page is a centered content column. Use sidebars, split views, asymmetric grids, and full-width sections deliberately.

## Visual Cliches

- **Purple/indigo gradients as the default "modern" look**: `from-indigo-500 to-violet-500` or `from-purple-600 to-blue-500`. Every AI tool defaults to these. Choose colors that match the product, not the trend.
- **Gradient text** (`bg-clip-text text-transparent bg-gradient-to-r`): Rarely necessary, often unreadable, always screams AI-generated.
- **Glassmorphism everywhere**: `backdrop-blur` + semi-transparent backgrounds on every card and surface. Use sparingly if at all — it kills readability and feels like a 2021 Dribbble shot.
- **Glow shadows**: `shadow-[0_0_30px_rgba(...)]` or `shadow-lg shadow-purple-500/20`. Shadows represent physical elevation, not neon lighting.
- **Pulsing/glowing animations on static content**: `animate-pulse` on decorative elements, `animate-[glow_6s_infinite]`, ambient breathing effects. These add no information and distract.
- **Floating animations**: `animate-[float_3s_ease-in-out_infinite]`. Objects don't float. Objects have weight.

## Component Sins

- **Missing states**: A button with only a default state. No hover, no focus, no disabled, no loading. This is incomplete work.
- **`outline: none` without a focus replacement**: You've just made the interface unusable for keyboard users. Always provide `focus-visible` styles.
- **Placeholder-only inputs**: No visible label, just placeholder text that disappears on focus. Inaccessible and frustrating.
- **`<div onClick>` instead of `<button>`**: Not keyboard accessible, not announced by screen readers, no focus management. Use the right element.
- **Giant border radius on everything**: `rounded-2xl` cards, `rounded-full` buttons, `rounded-3xl` containers. Pick a radius convention and use it consistently. More radius ≠ more modern.
- **Identical spacing everywhere**: Same `p-4` or `p-6` on every element. Spacing should create hierarchy. Tighter for related elements, looser for section breaks.

## Content Failures

- **"Lorem ipsum" or placeholder text**: Use realistic content that helps evaluate the design. Real names ("Sarah Chen"), real numbers ("2,847"), real actions ("Export to CSV").
- **"Get Started" / "Learn More" / "View More" as the default CTA**: These mean nothing. Use specific, actionable labels that tell the user what happens ("Create Campaign", "View Analytics", "Import Contacts").
- **Stock descriptions**: "Our powerful platform helps you achieve your goals with cutting-edge technology." Write content that's specific to what the component actually does.
- **"John Doe" / "jane@example.com"**: Use diverse, realistic names and data.

## Technical Mistakes

- **Inline styles when Tailwind is available**: Don't mix `style={{}}` with Tailwind classes unless there's a dynamic value that Tailwind can't handle.
- **New icon library when one exists**: Check `package.json` before importing icons. Don't add `react-icons` when `lucide-react` is already installed.
- **Rebuilding existing components**: If the project has a Button, Card, or Dialog component, use it. Don't create a new one.
- **`!important` overrides**: Fix the specificity issue properly. Don't brute-force it.
- **Arbitrary magic numbers**: `mt-[37px]`, `w-[423px]`, `gap-[13px]`. Use the spacing scale. If it's not in the scale, it probably shouldn't be that value.
- **Missing `key` props on mapped lists**: React fundamentals. Always provide stable, unique keys.

## The Test

Before outputting any component, ask: **"Could Lovable, v0, or a generic AI tool have produced this?"**

If yes — redesign it. The output should look like a human designer with taste and opinions built it.
