# gradio-responsive-hf-spaces

This repository includes a skill named `gradio-responsive-hf-spaces` for creating, fixing, and restyling **Gradio 6.9.0** UIs in **Hugging Face Spaces** so they work well on both:

- Desktop 16:9 (for example `1920x1080`)
- Smartphone portrait 9:16 (for example `1080x1920`)

## What this skill does

The skill guides the agent to:

1. Use a screenshot-first workflow with Playwright (before and after each component-level UI change).
2. Diagnose and fix layout/UX issues across desktop and portrait mobile aspect ratios.
3. Provide PR-ready visual evidence showing before/after comparisons for both target viewports.
4. Apply a detailed custom class-based Gradio component approach, including CSS namespacing and JS event safety patterns.

## How to use this skill

Use this skill when your task mentions any of the following:

- Gradio responsive layout fixes
- Hugging Face Spaces UI/UX tuning
- mobile vs desktop parity issues
- custom CSS/JS styling in Gradio
- custom class-based Gradio components

Typical invocation context:

- “Fix clipping and spacing on mobile portrait while preserving desktop layout.”
- “Create a custom class-based Gradio component with custom CSS/JS.”
- “Restyle this Gradio app and provide before/after screenshots in PR evidence.”

## Where the skill files are in this repository

The skill is stored at:

- `.github/skills/gradio-responsive-hf-spaces/SKILL.md`

Supporting files:

- `.github/skills/gradio-responsive-hf-spaces/references/custom-class-components.md`
- `.github/skills/gradio-responsive-hf-spaces/evals/evals.json`

## Where to install/copy the files

To use this skill in another repository or environment, copy the folder:

- Source: `.github/skills/gradio-responsive-hf-spaces/`
- Destination: `<your-repo>/.github/skills/gradio-responsive-hf-spaces/`

At minimum, keep `SKILL.md`. Include `references/` and `evals/` for full guidance and test prompts.
