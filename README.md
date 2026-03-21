# Copilot Skill Creator Template

This repository is a template for creating new skill repositories and using GitHub Copilot Chat (Web) or GitHub Copilot Coding Agent (Web) to build skills.

The canonical specification is:

- `skills/skill-creator/SKILL.md`

When this repository is opened in Copilot, all skill creation and refinement should follow that file.

## Quickstart: Use This Template

1. Click **Use this template** on GitHub.
2. Create your new repository from this template.
3. Open your new repository and start Copilot Chat (Web) or Copilot Coding Agent (Web).
4. Tell Copilot to use `skills/skill-creator/SKILL.md` as the source specification.
5. Ask Copilot to generate your new skill under `skills/<new-skill-name>/`.

## Quickstart: Clone and Use with Copilot

1. Clone this repository.
2. Open it in a Copilot-enabled environment.
3. Start Copilot Chat and request skill creation using `skills/skill-creator/SKILL.md`.
4. Create or improve skills in `skills/<new-skill-name>/`.

## Two Supported Copilot Workflows

### 1) Build from another repository

Provide context from the target repository, then ask Copilot to convert that workflow into a skill:

- important files and folders
- expected inputs and outputs
- edge cases and constraints

### 2) Build from plain instructions

Describe the skill directly, then ask Copilot to interview you for missing details:

- what the skill does
- when it should trigger
- expected output format
- constraints and edge cases

## Required Output Structure

Copilot should generate new skills here:

- `skills/<new-skill-name>/SKILL.md`

Optional folders only when needed:

- `skills/<new-skill-name>/references/`
- `skills/<new-skill-name>/assets/`
- `skills/<new-skill-name>/evals/`

## Start Here Files

- [START_HERE_COPILOT.md](START_HERE_COPILOT.md)
- [.github/copilot-instructions.md](.github/copilot-instructions.md)
- [CHECKLIST.md](CHECKLIST.md)
