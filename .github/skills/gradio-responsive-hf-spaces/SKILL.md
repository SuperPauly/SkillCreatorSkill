---
name: gradio-responsive-hf-spaces
description: Create, fix, or restyle Gradio 6.9.0 UIs for Hugging Face Spaces with strong UX across 1080p desktop (16:9) and smartphone portrait (9:16). Use this whenever users mention Gradio layout, responsiveness, CSS/JS customization, custom class-based components, mobile vs desktop parity, or UI/UX tuning for Spaces.
compatibility: Requires Gradio 6.9.0-oriented guidance, Hugging Face Spaces deployment context, and Playwright screenshot tooling for visual verification.
---

# Gradio Responsive HF Spaces (Gradio 6.9.0)

Use this skill when building or fixing Gradio UIs that must look and behave well on both desktop 16:9 and mobile portrait 9:16.

## Core outcomes

1. Deliver component-level UI/UX improvements that hold up at both aspect ratios.
2. Use class-based custom component patterns with custom CSS/JS where needed.
3. Produce visual proof with before/after screenshots for every component-level change.

## Mandatory visual workflow (do this first)

Before changing any UI code:

1. Capture **baseline screenshots** using Playwright at both target viewports.
2. Share those images immediately for early analysis/review.
3. Review those images first, identify layout/UX issues, then begin changes.

After each component change (created, fixed, moved, or restyled):

1. Capture **post-change screenshots** at both target viewports.
2. Compare with baseline and verify spacing, hierarchy, readability, tap-target sizes, and overflow behavior.
3. Include evidence in the PR update so the user can confirm improvements.

Use these viewports unless the user gives better targets:

- Desktop 16:9: `1920x1080`
- Phone portrait 9:16: `1080x1920`

## Standard execution loop

For every UI component touched:

1. Baseline screenshots (16:9 and 9:16)
2. Diagnose UX issues from screenshots
3. Implement one focused change
4. Post-change screenshots (16:9 and 9:16)
5. Compare and record results in a short checklist
6. Move to next component

Do not batch many visual changes before checking screenshots; iterate component-by-component.

## Gradio 6.9.0 research rule

If a Gradio MCP server is available, query it first for API behavior and compatibility details before implementation.
If not available, use official Gradio docs/changelog and clearly state assumptions.

## Design guidance

### Desktop 1080p (16:9)

- Use clear content width constraints and predictable horizontal rhythm.
- Keep primary actions above the fold when possible.
- Prevent oversized line lengths in markdown/text output.
- Avoid crowded control panels; group advanced controls behind accordions/tabs.

### Smartphone portrait (9:16)

- Prioritize single-column flow with vertical reading order.
- Ensure primary CTA and key outputs are visible without horizontal scrolling.
- Increase touch target comfort (roughly >= 44px) and spacing between interactive controls.
- Reduce persistent visual noise; collapse secondary controls.

### Cross-ratio consistency checks

- No clipped labels or controls
- No horizontal scrollbar for primary content
- No overlapping floating elements
- Navigation and status feedback remain discoverable
- Keyboard focus and hover/focus states remain visible

## Custom class-based component workflow

Use the detailed implementation guide in:

- `references/custom-class-components.md`

When building custom components, ensure:

- Stable value schema between Python backend and JS frontend
- Explicit validation on backend inputs
- CSS namespacing to prevent style collisions in larger Spaces
- Event wiring that avoids double-trigger loops

## PR evidence format

When reporting progress, include a compact evidence table for each changed component:

- Component name
- What changed
- 16:9 before/after screenshots
- 9:16 before/after screenshots
- UX verdict (pass/fail + notes)

If any ratio fails UX checks, fix and re-capture before marking done.

## Intended runtime contexts

This skill is written for GitHub Copilot Coding Agent (web), Codex CLI, and Codex web sessions where UI/UX edits are performed with reproducible screenshot evidence.
