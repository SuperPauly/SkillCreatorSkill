# Custom Class-Based Gradio Components (Gradio 6.9.0): CSS + JS Guide

This guide is for building reusable custom components in Gradio Spaces while preserving responsive UX on desktop (16:9) and mobile portrait (9:16).

## 1) Component contract first

Define the component's data contract before writing UI code.

- **Python value shape**: decide exact dict/list/scalar schema.
- **Frontend value shape**: keep parity with Python shape.
- **Serialization rules**: explicitly map frontend state to backend payload.
- **Validation rules**: reject malformed payloads early in Python.

Why: Class-based components fail most often at boundary mismatches, not visuals.

## 2) Class structure blueprint

Use a component class with explicit methods for preprocess/postprocess and stable defaults.

Typical pattern:

1. Declare class metadata and accepted value type
2. Implement backend normalization/validation
3. Attach CSS class hooks for scoped styling
4. Attach JS events for UI-only enhancements
5. Expose clear public constructor args

Keep backward-compatible defaults to avoid breaking Spaces demos.

## 3) CSS strategy for responsive behavior

### Namespacing

Always namespace styles to a parent class unique to your component, e.g. `.sp-profile-card`.

- Good: `.sp-profile-card .title { ... }`
- Risky: `.title { ... }`

### Breakpoints

Design desktop first, then add mobile overrides.

Recommended breakpoints:

- >= 1280px for desktop comfort checks
- <= 768px for phone portrait behavior

### Safe responsive rules

- Prefer `max-width: 100%` on media/containers
- Use `flex-wrap` for dense button/control rows
- Prevent text clipping with wrapping and balanced line-height
- Avoid fixed heights unless content is strictly bounded

## 4) JS strategy for UI interactions

Use JS for interface enhancements only; keep source-of-truth logic in Python whenever possible.

Good JS uses:

- Lightweight progressive enhancement (toggles, local previews)
- Keyboard and pointer interactions
- Debounced UI updates for expensive redraws

Avoid:

- Hidden business logic only in JS
- Multiple event bindings to same element per render
- Non-idempotent init routines

### Init safety checklist

- Ensure one-time listener registration
- Guard against re-mount cycles
- Avoid leaking timers/observers

## 5) Example design checklist (per component)

For each component you create or modify:

1. Baseline screenshot at 1920x1080 and 1080x1920
2. Implement one component-level change
3. Post-change screenshot at both sizes
4. Compare:
   - readability
   - spacing/tap targets
   - overflow and clipping
   - hierarchy and CTA visibility
5. Record before/after evidence

## 6) Hugging Face Spaces UX constraints

- Assume variable CPU/network performance; reduce unnecessary rerenders.
- Keep first meaningful UI visible quickly.
- Place expensive optional features behind explicit user action.
- Prefer deterministic loading states and error states.

## 7) Accessibility and interaction quality

- Preserve label/field association and keyboard navigation.
- Verify visible focus indicators in custom CSS.
- Ensure status updates (loading, done, failed) are perceivable.
- Maintain contrast for text and controls across themes.

## 8) Quick review template for PR notes

Use this exact mini-template per component:

- **Component**:
- **Change summary**:
- **Desktop 16:9 result**:
- **Portrait 9:16 result**:
- **Before screenshots**:
- **After screenshots**:
- **Open UX risks**:

## 9) Failure patterns to catch early

- A layout that passes desktop but causes horizontal scroll on portrait
- CSS specificity conflicts with Gradio theme classes
- JS event duplication after rerender
- Backend rejecting values silently due to schema drift
- "Works in screenshot" but poor interaction due to small tap targets

## 10) Invocation reminder

When this skill is invoked for UI/UX work:

- Start with screenshots before edits.
- Re-check after every component-level change.
- Attach visual evidence in PR updates for both 16:9 and 9:16.
