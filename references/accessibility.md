# Accessibility Standards

These are non-negotiable. Every component AREKOS produces must meet these standards.

---

## Semantic HTML

Use the right element for the job. Always.

| Purpose | Use | Never |
|---------|-----|-------|
| Clickable action | `<button>` | `<div onClick>`, `<span onClick>`, `<a>` without href |
| Navigation link | `<a href>` | `<button>` for navigation, `<div onClick>` |
| Page navigation | `<nav>` | `<div className="nav">` |
| Main content | `<main>` | `<div className="main">` |
| Page section | `<section>` with heading | `<div>` |
| List of items | `<ul>` / `<ol>` | `<div>` with `<div>` children |
| Form field | `<label>` + `<input>` | Placeholder-only inputs without labels |
| Heading hierarchy | `<h1>` through `<h6>` in order | Skipping levels (h1 → h3) |
| Image | `<img alt="...">` | `<img>` without alt, decorative `<div>` with background-image |

---

## Keyboard Navigation

Every interactive element must be reachable and operable with a keyboard.

**Focus order**: Follows the visual reading order (top to bottom, left to right). Use `tabindex="0"` for custom interactive elements. Never use `tabindex` > 0.

**Key bindings**:
| Key | Action |
|-----|--------|
| Tab | Move focus to next interactive element |
| Shift+Tab | Move focus to previous interactive element |
| Enter | Activate buttons, submit forms, follow links |
| Space | Activate buttons, toggle checkboxes |
| Escape | Close modals, dropdowns, popovers |
| Arrow keys | Navigate within tab lists, menus, radio groups, select options |

**Focus trapping**: Modals and drawers must trap focus inside. Tab from the last element wraps to the first. Shift+Tab from the first wraps to the last.

**Skip links**: For pages with complex navigation, include a "Skip to main content" link as the first focusable element (visually hidden until focused).

---

## Focus Indicators

**Never remove focus outlines without providing an alternative.**

```css
/* BAD */
*:focus { outline: none; }

/* GOOD — use focus-visible for keyboard-only indicators */
.element:focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}
```

**Tailwind pattern**: `focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:ring-{accent}`

Focus indicators must be visible against the background. Test on both light and dark surfaces.

---

## ARIA Attributes

Use ARIA to fill gaps where HTML semantics fall short. Not as a replacement for semantic HTML.

**Common patterns**:

```html
<!-- Modal -->
<div role="dialog" aria-modal="true" aria-labelledby="modal-title" aria-describedby="modal-desc">
  <h2 id="modal-title">Delete Campaign</h2>
  <p id="modal-desc">This action cannot be undone.</p>
</div>

<!-- Tabs -->
<div role="tablist" aria-label="Settings">
  <button role="tab" aria-selected="true" aria-controls="panel-general">General</button>
  <button role="tab" aria-selected="false" aria-controls="panel-billing">Billing</button>
</div>
<div role="tabpanel" id="panel-general" aria-labelledby="tab-general">...</div>

<!-- Expandable section -->
<button aria-expanded="false" aria-controls="section-details">Show Details</button>
<div id="section-details" hidden>...</div>

<!-- Loading states -->
<div aria-busy="true" aria-live="polite">Loading campaigns...</div>

<!-- Status messages -->
<div role="status" aria-live="polite">Campaign saved successfully.</div>

<!-- Error messages -->
<div role="alert">Failed to save. Please try again.</div>

<!-- Form field with error -->
<label for="email">Email</label>
<input id="email" aria-invalid="true" aria-describedby="email-error" />
<p id="email-error" role="alert">Please enter a valid email address.</p>
```

---

## Color & Contrast

**WCAG AA minimum contrast ratios**:
- Normal text (< 18px / < 14px bold): **4.5:1**
- Large text (≥ 18px / ≥ 14px bold): **3:1**
- UI components and graphical objects: **3:1**

**Never rely on color alone** to convey information:
- Error fields: red border + error icon + error text (not just red border)
- Status badges: colored background + text label (not just a colored dot)
- Charts: use patterns/shapes in addition to color
- Links: underline or other visual indicator besides color

**Test your colors**: Use Chrome DevTools contrast checker or similar tools. Common failures:
- Light gray text on white backgrounds
- Colored text on colored backgrounds without checking ratio
- Placeholder text too close to background color

---

## Images & Media

- All `<img>` elements need `alt` text
- Decorative images: `alt=""` (empty string, not omitted)
- Informative images: describe what the image conveys, not what it looks like
- Icons used as buttons: `aria-label` on the button, `aria-hidden="true"` on the icon
- Videos: captions or transcripts

---

## Touch Targets

Minimum touch target size: **44x44px** on mobile.

This applies to:
- Buttons
- Links
- Checkboxes and radio buttons
- Menu items
- Close buttons (especially the X on modals — common failure)

If the visual element is smaller than 44px, expand the clickable area with padding or a larger hit area.

---

## Screen Readers

**Visually hidden content** (for screen readers only):
```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

Tailwind: `sr-only` class

**Use for**:
- Icon-only buttons: `<button><Icon /><span className="sr-only">Close</span></button>`
- Additional context: `<span className="sr-only">Campaign status:</span> Active`
- Skip links

**Live regions**: Use `aria-live="polite"` for non-urgent updates (save confirmation, content loaded). Use `aria-live="assertive"` sparingly (only for errors that need immediate attention).

---

## Reduced Motion

Respect the user's motion preference:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

Tailwind: `motion-reduce:transition-none` / `motion-reduce:animate-none`

Always apply when using animations or transitions. Some users experience motion sickness, seizures, or vestibular disorders.
