# 🧠 Copilot Skill Creator Template

> A template repository for building new Copilot skills using **GitHub Copilot Chat (Web)** or the **Copilot Coding Agent (Web)**.

The canonical specification lives at:
📄 `.github/skills/skill-creator/SKILL.md`

When this repository is opened in Copilot, all skill creation and refinement should follow that file.

---

## ⚠️ GitHub Web Only — Not for CLI

> **This template is designed exclusively for use with GitHub Copilot on the GitHub website.**  
>  
> It is **not** compatible with the GitHub Copilot CLI, VS Code Copilot Chat, or any other local/desktop Copilot interface.  
>  
> You must use one of the following on **github.com**:
> - **Copilot Chat (Web)** — via the Copilot icon on your repository page
> - **Copilot Coding Agent (Web)** — via Issues or the Copilot agent interface

---

## 🚀 Quickstart

### Option A — Use This Template (Recommended)

1. Click **Use this template** on GitHub.
2. Create your new repository from this template.
3. Open your new repo and start **Copilot Chat** or **Copilot Coding Agent** (Web).
4. Tell Copilot to use `.github/skills/skill-creator/SKILL.md` as the source specification.
5. Ask Copilot to generate your new skill under `.github/skills/<new-skill-name>/`.

### Option B — Clone and Use Locally

1. Clone this repository.
2. Open it in a Copilot-enabled environment.
3. Start Copilot Chat and request skill creation using `.github/skills/skill-creator/SKILL.md`.
4. Create or improve skills in `.github/skills/<new-skill-name>/`.

---

## 🔌 MCP Servers — Supercharge Your Skill with External Tools

After using this template or cloning the project, you can connect **MCP (Model Context Protocol) servers** to your repository to give Copilot access to external documentation, APIs, and tools relevant to the skill you are building.

### What Are MCP Servers?

MCP servers extend what Copilot can access during skill creation. For example, if you are building a skill around Gradio, HuggingFace, or a documented external library, adding the relevant MCP server means Copilot can pull in live documentation and context while generating your skill.

### How to Add MCP Servers to Your Project

1. Go to your repository on **github.com**.
2. Click **Settings** → **Copilot** → **MCP Servers** (under the Coding agent section).
3. Add your MCP configuration as JSON.

### Example MCP Configuration

The following example adds three useful MCP servers — **DeepWiki** (general repo/wiki knowledge), **Gradio Docs**, and **HuggingFace** (requires an API key secret):

```json
{
  "mcpServers": {
    "gradio": {
      "type": "http",
      "tools": ["*"],
      "url": "https://gradio-docs-mcp.hf.space/gradio_api/mcp/"
    },
    "hf-mcp-server": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@huggingface/hf-mcp-server"],
      "tools": ["*"],
      "env": {
        "HF_TOKEN": "$HF_READ"
      }
    },
    "deepwiki": {
      "type": "http",
      "tools": ["*"],
      "url": "https://mcp.deepwiki.com/mcp"
    }
  }
}
```

### 🔑 HuggingFace API Key (Required for `hf-mcp-server`)

The HuggingFace MCP server requires an API token stored as a repository secret:

1. Go to [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens) and create a **Read** token.
2. In your GitHub repository, go to **Settings** → **Secrets and variables** → **Actions**.
3. Click **New repository secret**.
4. Name it `HF_READ` and paste your HuggingFace token as the value.

> 💡 Tip: Swap out or add MCP servers based on the skill you are building. For example, if your skill is about a specific framework or API, look for an MCP server that provides its documentation — this will significantly improve the quality of Copilot's output.

---

## 🔄 Two Supported Copilot Workflows

| Workflow | Description |
|---|---|
| **Build from a repository** | Point Copilot at an existing repo to convert its workflow into a skill |
| **Build from plain instructions** | Describe the skill in plain language; Copilot will ask clarifying questions |

### 1️⃣ Build from Another Repository

Provide Copilot with context from the target repository:
- Important files and folders
- Expected inputs and outputs
- Edge cases and constraints

### 2️⃣ Build from Plain Instructions

Describe the skill directly and let Copilot interview you for missing details:
- What the skill does
- When it should trigger
- Expected output format
- Constraints and edge cases

---

## 📁 Required Output Structure

Copilot will generate new skills under:

```
.github/skills/<new-skill-name>/
├── SKILL.md          ← Required
├── references/       ← Optional
├── assets/           ← Optional
├── evals/            ← Optional
└── scripts/          ← Optional
```

---

## 🧹 Post-Setup Cleanup

> ⚠️ **Important:** Only run this after your generated skill files are committed and verified.

Once your skill(s) are created, remove the template scaffolding:

1. Go to the **Actions** tab in your repository.
2. Run the **Delete template files only (manual)** workflow.
3. Confirm the workflow completes successfully.

This removes the original `skill-creator/` template files and keeps only the skill content you created under `.github/skills/<your-skill-name>/`.
