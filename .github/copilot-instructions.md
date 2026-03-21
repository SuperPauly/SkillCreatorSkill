# Copilot Instructions for This Repository

This repository is configured so Copilot Chat (Web) and Copilot Coding Agent (Web) should use `skills/skill-creator/SKILL.md` as the canonical skill-creation specification.

## Default behavior

- When a user asks to create, improve, evaluate, review, package, or debug a skill, read `skills/skill-creator/SKILL.md` first.
- Treat `skills/skill-creator/` as the source of truth for the workflow and supporting resources.
- Do not use any placeholder template SKILL file as the active spec for this repository.

## Authoring output conventions

- Place user-created skills under `skills/<new-skill-name>/`.
- Keep `name` and `description` valid in YAML frontmatter.
- Make descriptions explicit about when the skill should trigger.
- Create `references/`, `assets/`, and `evals/` only when they are needed.

## Web-first workflow

- In GitHub web Copilot sessions, focus on authoring, review, and iterative refinement.
- If users want local quantitative benchmarking, point them to local scripts in `skills/skill-creator/scripts/` as an optional advanced path.
