# AREKOS UI — Design Principles

These principles guide every decision. They are not rules about specific colors or border radii — they are standards of quality and taste.

## 1. Hierarchy First

Every screen has one job. One primary action, one focal point, one reading path. Build the layout around that, then fill in secondary elements. If everything is equally prominent, nothing is.

- Use size, weight, and space — not color alone — to create hierarchy
- Primary actions are visually distinct from secondary and tertiary actions
- Group related elements. Separate unrelated ones. White space is a design tool, not wasted space.

## 2. Consistency Over Cleverness

Reuse patterns. A button should look like a button everywhere. Spacing should follow a scale. Colors should come from a defined palette. If the project has a design system, follow it strictly. If it doesn't, establish rhythm through consistent choices.

- Pick a spacing scale (4px or 8px base) and use only those values
- Limit your type scale to 4-6 sizes max
- Use no more than 2-3 font weights
- Maintain consistent padding and gap patterns across components

## 3. States Are Not Optional

Every interactive element needs: default, hover, focus, active, disabled, and loading states. Every data-driven view needs: loading, empty, error, and populated states. Missing states make UI feel broken.

- Hover: subtle background shift or opacity change (keep it fast — 100-150ms)
- Focus: visible ring or outline for keyboard users. Never `outline: none` without a replacement.
- Disabled: reduced opacity + `cursor-not-allowed` + `pointer-events-none`
- Loading: skeleton screens over spinners when possible. Never block the entire page.
- Empty: helpful message + clear action. Never a blank page.
- Error: inline, specific, and recoverable. Never just "Something went wrong."

## 4. Responsive Is the Default

Design for all viewports from the start. Not as an afterthought.

- Mobile-first breakpoints
- Flexible grids that collapse gracefully
- Touch targets minimum 44x44px on mobile
- Test text truncation at every breakpoint
- Navigation patterns that work on both desktop and mobile

## 5. Motion Is Communication

Animation tells the user what happened, where something went, or what to look at. It is never decorative.

- Micro-interactions: 100-150ms, ease-out
- State transitions: 150-200ms, ease-in-out
- Page/section transitions: 200-300ms max
- Stagger delays: 30-50ms between items
- Never: bounce, pulse, float, glow, or anything that loops infinitely on static content

## 6. Color With Intent

Color draws attention. Use it deliberately.

- 1 primary accent color. Maybe 1 secondary. That's it for brand colors.
- Semantic colors for status: success (green), warning (amber), error (red), info (blue)
- Text should have 3 tiers: primary, secondary, tertiary. Map them and use consistently.
- Background should have 2-3 tiers: base, raised, elevated. Create depth through layering.
- Check contrast ratios. WCAG AA minimum (4.5:1 for text, 3:1 for large text and UI).

## 7. Typography Is Structure

Type does more work than any other element. Treat it with respect.

- Establish a clear scale: display, heading, subheading, body, small, caption
- Line height: tighter for headings (1.1-1.2), looser for body (1.5-1.6)
- Letter spacing: slightly negative for large headings, neutral or slightly positive for small caps/labels
- Monospace for data, numbers, and code — not for decoration
- Truncate with ellipsis. Never let text break a layout.

## 8. Tables and Data

Data-heavy interfaces need extra care.

- Right-align numbers, left-align text
- Consistent column widths — don't let content dictate layout
- Sticky headers on scroll
- Sortable columns with clear visual indicators
- Row hover states for scannability
- Pagination or virtualization for large datasets — never render 1000 rows

## 9. Forms That Don't Fight You

Forms are where UI gets hard. Get them right.

- Labels above inputs, not inside (placeholder-only labels are inaccessible)
- Inline validation on blur, not on every keystroke
- Clear error messages next to the field, not at the top of the form
- Logical tab order
- Submit buttons that show loading state and disable during submission
- Success feedback that's visible and unambiguous

## 10. Craft

The difference between good and great is the stuff most people skip.

- Consistent icon sizes and stroke widths
- Proper text wrapping and overflow handling
- Smooth scroll behavior where appropriate
- Backdrop overlays on modals that dim but don't obscure
- Transitions between routes that don't flash white
- Selection states that feel intentional
- Scroll shadows on overflowing containers
- Proper z-index management (define layers, don't guess)
