# AREKOS UI — Component Patterns

Every component below uses the Warm Obsidian design system tokens. These are the canonical implementations. When building any UI, reference these patterns.

## Button

Solid fills. 1px lighter top border to simulate overhead light source. No gradients. No glow.

```tsx
{/* Primary */}
<button className="px-4 py-2 bg-ak-accent hover:bg-ak-accent-hover text-white text-[13px] font-medium rounded tracking-wide border-t border-white/10 transition-all duration-[120ms] ease-[cubic-bezier(0.16,1,0.3,1)] active:scale-[0.98]">
  Create Campaign
</button>

{/* Secondary */}
<button className="px-4 py-2 bg-ak-bg-raised hover:bg-ak-bg-hover text-ak-text-secondary hover:text-ak-text text-[13px] font-medium rounded border border-ak-border hover:border-ak-border-strong transition-all duration-[120ms] active:scale-[0.98]">
  Cancel
</button>

{/* Ghost */}
<button className="px-4 py-2 text-ak-text-secondary hover:text-ak-text hover:bg-ak-bg-raised text-[13px] font-medium rounded transition-all duration-[120ms] active:scale-[0.98]">
  Skip
</button>

{/* Destructive */}
<button className="px-4 py-2 bg-ak-danger/10 hover:bg-ak-danger/20 text-[#c4564a] text-[13px] font-medium rounded border border-ak-danger/20 hover:border-ak-danger/30 transition-all duration-[120ms] active:scale-[0.98]">
  Delete
</button>
```

## Card

Left-edge accent bar. Warm raised background. No full border wrap.

```tsx
<div className="relative bg-ak-bg-raised rounded overflow-hidden transition-all duration-[120ms] hover:translate-y-[-1px] hover:shadow-[0_4px_12px_rgba(13,11,10,0.4),0_1px_3px_rgba(13,11,10,0.2)]">
  {/* Left accent bar */}
  <div className="absolute left-0 top-0 bottom-0 w-[3px] bg-ak-accent" />

  <div className="pl-5 pr-4 py-4">
    <div className="flex items-center justify-between mb-3">
      <h3 className="text-[15px] font-medium text-ak-text">Campaign Performance</h3>
      <span className="text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary">Last 7 days</span>
    </div>
    <p className="text-[32px] font-bold tracking-tight text-ak-text leading-none mb-1">12,847</p>
    <p className="text-[13px] text-ak-text-secondary">emails delivered</p>
  </div>
</div>
```

### Card without accent bar (secondary)
For less prominent cards, use a single bottom border:

```tsx
<div className="bg-ak-bg-raised rounded p-4 border-b border-ak-border hover:bg-ak-bg-hover transition-colors duration-[120ms]">
  <p className="text-[13px] text-ak-text-secondary">Content here</p>
</div>
```

## Input / Text Field

Bottom-border only. Animated underline on focus. No box border.

```tsx
<div className="space-y-1.5">
  <label className="text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary">
    Email Address
  </label>
  <div className="relative">
    <input
      type="email"
      placeholder="you@company.com"
      className="w-full bg-transparent text-[15px] text-ak-text placeholder:text-ak-text-disabled pb-2 border-b border-ak-border focus:outline-none transition-colors duration-[120ms] peer"
    />
    {/* Animated focus underline */}
    <div className="absolute bottom-0 left-0 h-[2px] bg-ak-accent w-0 peer-focus:w-full transition-all duration-[180ms] ease-[cubic-bezier(0.16,1,0.3,1)]" />
  </div>
</div>
```

## Table / Data Grid

Warm alternating rows. Left-aligned headers. Clean horizontal lines.

```tsx
<div className="overflow-x-auto">
  <table className="w-full">
    <thead>
      <tr className="border-b border-ak-border-strong">
        <th className="text-left text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary py-3 pr-4">Name</th>
        <th className="text-left text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary py-3 pr-4">Status</th>
        <th className="text-right text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary py-3">Sent</th>
      </tr>
    </thead>
    <tbody>
      {rows.map((row, i) => (
        <tr
          key={row.id}
          className={`border-b border-ak-border hover:bg-ak-bg-hover transition-colors duration-[120ms] ${
            i % 2 === 1 ? "bg-[rgba(194,112,62,0.03)]" : ""
          }`}
        >
          <td className="text-[15px] text-ak-text py-3 pr-4">{row.name}</td>
          <td className="py-3 pr-4">
            <span className="text-[11px] font-medium tracking-[0.06em] uppercase text-ak-success">{row.status}</span>
          </td>
          <td className="text-right text-[13px] text-ak-text-secondary font-mono py-3">{row.sent}</td>
        </tr>
      ))}
    </tbody>
  </table>
</div>
```

## Navigation / Tabs

Horizontal with active underline. No pills. No background tabs.

```tsx
<nav className="flex items-center gap-6 border-b border-ak-border">
  {tabs.map((tab) => (
    <button
      key={tab.id}
      onClick={() => setActive(tab.id)}
      className={`relative pb-3 text-[13px] font-medium transition-colors duration-[120ms] ${
        active === tab.id
          ? "text-ak-text"
          : "text-ak-text-tertiary hover:text-ak-text-secondary"
      }`}
    >
      {tab.label}
      {active === tab.id && (
        <div className="absolute bottom-0 left-0 right-0 h-[2px] bg-ak-accent" />
      )}
    </button>
  ))}
</nav>
```

## Badge / Tag

Small. Uppercase. Muted background. Tight.

```tsx
{/* Default */}
<span className="inline-flex items-center px-2 py-0.5 text-[11px] font-medium tracking-[0.06em] uppercase text-ak-accent bg-ak-accent-muted rounded-sm">
  Active
</span>

{/* Success */}
<span className="inline-flex items-center px-2 py-0.5 text-[11px] font-medium tracking-[0.06em] uppercase text-ak-success bg-ak-tertiary-muted rounded-sm">
  Delivered
</span>

{/* Danger */}
<span className="inline-flex items-center px-2 py-0.5 text-[11px] font-medium tracking-[0.06em] uppercase text-[#c4564a] bg-ak-danger-muted rounded-sm">
  Failed
</span>

{/* Neutral */}
<span className="inline-flex items-center px-2 py-0.5 text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary bg-[rgba(237,232,227,0.05)] rounded-sm">
  Draft
</span>
```

## Modal / Dialog

Sharp corners. Solid background. No backdrop-blur. Clear layer separation via shadow.

```tsx
{/* Overlay */}
<div className="fixed inset-0 bg-black/60 z-40" onClick={onClose} />

{/* Dialog */}
<div className="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 z-50 w-full max-w-md bg-ak-bg-elevated rounded shadow-[0_12px_40px_rgba(13,11,10,0.5),0_2px_8px_rgba(13,11,10,0.3)] animate-[ak-enter_200ms_cubic-bezier(0.16,1,0.3,1)_both]">
  <div className="p-5 border-b border-ak-border">
    <h2 className="text-[15px] font-medium text-ak-text">Confirm Action</h2>
  </div>
  <div className="p-5">
    <p className="text-[13px] text-ak-text-secondary leading-relaxed">
      Are you sure you want to delete this campaign? This action cannot be undone.
    </p>
  </div>
  <div className="flex items-center justify-end gap-2 p-4 border-t border-ak-border">
    <button className="px-4 py-2 text-[13px] font-medium text-ak-text-secondary hover:text-ak-text rounded transition-colors duration-[120ms]">
      Cancel
    </button>
    <button className="px-4 py-2 bg-ak-danger/10 hover:bg-ak-danger/20 text-[#c4564a] text-[13px] font-medium rounded border border-ak-danger/20 transition-all duration-[120ms]">
      Delete Campaign
    </button>
  </div>
</div>
```

## Stat Block

Asymmetric layout. Value left-heavy. Label as overline caption.

```tsx
<div className="space-y-1">
  <span className="text-[11px] font-medium tracking-[0.06em] uppercase text-ak-text-tertiary">
    Open Rate
  </span>
  <div className="flex items-baseline gap-2">
    <span className="text-[28px] font-bold tracking-tight text-ak-text leading-none">24.8%</span>
    <span className="text-[11px] font-medium text-ak-success">+3.2%</span>
  </div>
</div>
```

## Empty State

Minimal. No illustrations. Typography-driven.

```tsx
<div className="py-16 px-4">
  <p className="text-[15px] font-medium text-ak-text-secondary mb-1">No campaigns yet</p>
  <p className="text-[13px] text-ak-text-tertiary mb-4">Create your first campaign to start reaching your audience.</p>
  <button className="px-4 py-2 bg-ak-accent hover:bg-ak-accent-hover text-white text-[13px] font-medium rounded border-t border-white/10 transition-all duration-[120ms]">
    New Campaign
  </button>
</div>
```

## Layout Philosophy: Structured Tension

Default to asymmetric layouts. Not everything centered.

```tsx
{/* Page layout — content heavy left, sidebar right */}
<div className="grid grid-cols-[1fr_320px] gap-6 min-h-screen">
  <main className="py-10 pl-10 pr-6">
    {/* Primary content */}
  </main>
  <aside className="py-10 pr-10 border-l border-ak-border">
    {/* Secondary content */}
  </aside>
</div>

{/* Section layout — heading left, content right */}
<section className="grid grid-cols-[200px_1fr] gap-10 py-10 border-b border-ak-border">
  <div>
    <h2 className="text-[15px] font-medium text-ak-text">Settings</h2>
    <p className="text-[13px] text-ak-text-tertiary mt-1">Manage your preferences</p>
  </div>
  <div>
    {/* Form fields, content */}
  </div>
</section>
```
