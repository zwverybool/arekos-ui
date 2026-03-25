# Component Patterns

Quality standards for common component types. These are not implementations — they are checklists of what "done right" looks like. Adapt to the project's design language.

---

## Buttons

**Variants** (minimum 4):
- **Primary**: Filled background. The main action on any screen. Only one per section.
- **Secondary**: Outlined or muted fill. Supporting actions.
- **Ghost**: Text-only with hover background. Tertiary actions.
- **Destructive**: Red/danger semantic color. Irreversible actions.

**Required states**: default, hover, focus-visible, active (pressed), disabled, loading

**Loading state**: Replace label with spinner + "Processing..." or keep label and add spinner to the left. Disable pointer events. Never let users double-submit.

**Icon placement**: Leading icon (left of text) for most cases. Trailing icon (right) only for directional actions (arrows, external links). Icon-only buttons need `aria-label`.

**Size discipline**: Define 2-3 sizes (sm, default, lg) and use them consistently. Don't create ad-hoc sizes.

---

## Cards

**Structure**: Every card has content hierarchy:
1. Visual indicator or category (badge, overline label, color accent)
2. Title (the scannable element)
3. Supporting information (description, metadata, stats)
4. Actions (if any — bottom or right-aligned)

**Elevation**: Cards should feel like they sit on the surface. Use subtle shadow or border, not both. On hover, increase elevation slightly (shadow change + small translateY).

**Accent techniques**:
- Left border accent (3-4px colored left edge)
- Top border accent (colored top edge)
- Background tint (very subtle color wash)
- Never: full border in accent color (looks like an error state)

**Click targets**: If the entire card is clickable, the whole card is the click target. Use `cursor-pointer` and a visible hover state on the entire card, not just a nested link.

---

## Forms

**Labels**: Always above the input. Never inside (placeholder-only labels are inaccessible and frustrating). Use a small, muted label above and a helpful placeholder inside.

**Validation**:
- Validate on blur (when the user leaves the field), not on every keystroke
- Show errors inline, directly below the field
- Errors are specific: "Email must include @" not "Invalid input"
- Success indication: subtle green checkmark or border color, not a full message
- Required fields: mark optional fields as "(optional)" rather than marking required with asterisks

**Multi-step forms** (wizards):
- Progress indicator at top (step 1 of 3, or a visual stepper)
- Back/Next buttons with clear labels (not just arrows)
- Validate each step before allowing progression
- Preserve state when going back
- Summary step before final submission

**Submit button**:
- Disabled until form is valid (with visual feedback on why)
- Shows loading state during submission
- Success feedback after submission (redirect, toast, or inline message)
- Error recovery if submission fails (don't lose the form data)

---

## Tables / Data Grids

**Alignment**:
- Text: left-aligned
- Numbers: right-aligned
- Status/badges: left-aligned or centered
- Actions: right-aligned, last column

**Headers**: Uppercase or small caps, muted color, smaller font size than body. Sticky on vertical scroll. Never bold the same size as body text.

**Rows**:
- Subtle hover state (background shift)
- Click target is the entire row if rows are navigable
- Alternating row colors OR divider lines, not both
- Selected state if multi-select is supported

**Sorting**: Clear indicator (arrow icon) on the sorted column. Click to toggle asc/desc. Default sort should be the most useful (newest first, alphabetical, etc.).

**Pagination**: Show current range ("1-25 of 847"). Previous/Next buttons. Jump to first/last. Items per page selector if relevant.

**Empty state**: Not a blank table. A centered message with context and a primary action ("No campaigns yet. Create your first campaign.").

**Loading**: Skeleton rows that match the table structure. Not a centered spinner.

---

## Modals / Dialogs

**Focus management**:
- Focus moves to the modal when it opens (first focusable element or the modal itself)
- Focus is trapped inside the modal (Tab cycles within)
- Focus returns to the trigger element when modal closes
- Escape key closes the modal

**Backdrop**: Semi-transparent overlay that dims the background. Clicking the backdrop closes the modal (for non-destructive modals). No backdrop-blur unless the project already uses it.

**Structure**:
1. Header: title + optional close button (X, top-right)
2. Body: content with appropriate padding
3. Footer: action buttons, right-aligned. Primary action on the right, cancel on the left.

**Animation**: Fade in backdrop (150ms). Scale up + fade in dialog (200ms, ease-out). Reverse on close.

**Confirmation dialogs**: For destructive actions, require typing the item name or a confirmation word. Destructive button should be visually distinct (red) and not the default focus.

**ARIA**: `role="dialog"`, `aria-modal="true"`, `aria-labelledby` pointing to the title, `aria-describedby` pointing to the description.

---

## Navigation

**Tabs**:
- Active tab has a clear visual indicator (underline, background, or bold)
- Inactive tabs are muted but readable
- Underline style: 2px bottom border, animated slide on tab change
- Background style: subtle fill on active, transparent on inactive
- Never pill-shaped tab containers
- `role="tablist"`, `role="tab"`, `aria-selected`, keyboard arrow navigation

**Sidebar**:
- Collapsible on desktop (icon-only mode)
- Full overlay on mobile (slide in from left)
- Active item clearly highlighted
- Grouped sections with subtle dividers or headings
- Consistent icon + label alignment

**Breadcrumbs**:
- Separator between items (/ or >)
- Current page is not a link (plain text, slightly bolder)
- Truncate middle items on long paths with "..."
- `aria-label="Breadcrumb"` on the nav, `aria-current="page"` on current

---

## Empty States

Every data-driven view needs an empty state. Never a blank page.

**Structure**:
1. Optional illustration or icon (subtle, not cartoon-y)
2. Headline explaining what goes here ("No campaigns yet")
3. Brief description of what the user should do ("Create your first email campaign to start reaching your audience.")
4. Primary action button ("Create Campaign")

**Tone**: Helpful, not apologetic. Don't say "Oops!" or "Sorry, nothing here."

---

## Error States

**Inline errors** (form fields, failed actions):
- Red/danger color for the message
- Icon + text (not just color — accessibility)
- Specific and actionable ("Could not save. Check your connection and try again.")
- Recovery path (retry button, alternative action)

**Page-level errors** (404, 500, failed data fetch):
- Clear headline ("Page not found" / "Something went wrong")
- Brief explanation
- Primary action ("Go back" / "Try again" / "Go home")
- No technical jargon (no stack traces, no error codes unless useful)

---

## Loading States

**Skeleton screens** over spinners whenever possible. Match the layout of the content being loaded.

**Inline loading**: Small spinner next to the action that triggered it. Don't block the whole page for a single action.

**Progressive loading**: Show what you have, load the rest. Header and navigation render immediately. Content areas show skeletons.

**Never**: Full-page spinner with no context. The user should always know what's happening and what they're waiting for.

---

## Data Display

**Stat blocks**:
- Large number (the value)
- Small label above or below (what it measures)
- Optional trend indicator (up/down arrow with percentage)
- Optional sparkline for context

**Badges / Tags**:
- Small, compact, uppercase or small text
- Semantic colors: success (green), warning (amber), error (red), neutral (gray), info (blue)
- Never more than 2-3 words inside a badge
- Consistent sizing across all badge types

**Progress bars**:
- Show percentage or fraction (23/100 or 23%)
- Animate fill on load (subtle, 300ms)
- Color indicates status (green = healthy, amber = warning, red = critical)
- Never indeterminate unless truly unknown
