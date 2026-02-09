# Antigravity a Quick Usage Guide

This guide covers **Google Antigravity**, an agentic IDE and development platform.
It is designed as a practical reference covering the editor, agent system, and configuration.

## Table of contents

1. [0. Mental model](#0-mental-model)
2. [1. Interface overview](#1-interface-overview)
3. [2. Agent panel](#2-agent-panel)
4. [3. Agent Manager](#3-agent-manager)
5. [4. Models](#4-models)
6. [5. Conversation modes](#5-conversation-modes)
7. [6. Rules](#6-rules)
8. [7. Workflows](#7-workflows)
9. [8. Skills](#8-skills)
10. [9. MCP configuration](#9-mcp-configuration)
11. [10. Agent modes and settings](#10-agent-modes-and-settings)
12. [11. Task Groups](#11-task-groups)
13. [12. Browser subagent](#12-browser-subagent)
14. [13. Strict mode](#13-strict-mode)
15. [14. Workspaces and Playgrounds](#14-workspaces-and-playgrounds)
16. [15. Keyboard shortcuts](#15-keyboard-shortcuts)
17. [Appendix A: Identity file comparison across platforms](#appendix-a-identity-file-comparison-across-platforms)
18. [Appendix B: Model selection guide](#appendix-b-model-selection-guide)
19. [Appendix C: Companion setup quick reference](#appendix-c-companion-setup-quick-reference)

## 0. Mental model

1. Antigravity is a **VS Code-style editor** with a built-in agentic AI system.
2. The **Agent Panel** (right sidebar) is your primary AI interaction surface — chat, commands, file references.
3. The **Agent Manager** is a separate view for orchestrating multiple agents across multiple workspaces in parallel.
4. Agent behavior is configured via **Rules** (markdown constraint files), **Workflows** (step sequences), and **Skills** (reusable capability packages).
5. **MCP servers** extend the agent with external tool access, configurable via a built-in MCP Store or raw JSON config.
6. Models are swappable per-conversation — Google Gemini, Anthropic Claude, and open-source models available.

## 1. Interface overview

| Area | Location | Purpose |
|------|----------|---------|
| File Explorer | Left sidebar | Browse project files |
| Editor | Center | Code editing with tab completion and natural language commands |
| Agent Panel | Right sidebar | AI chat, model selection, customizations |
| Terminal | Bottom panel (`Ctrl+J`) | Integrated terminal |
| Agent Manager | Separate view (`Ctrl+E` to toggle) | Multi-agent, multi-workspace orchestration |
| Status Bar | Bottom | Errors, warnings, settings link |

**Top bar navigation:**
- `Antigravity` menu — app-level settings
- `Open Agent Manager` / `Open Editor` — toggle between views (`Ctrl+E`)

## 2. Agent panel

The right sidebar for AI interaction.

### Input bar

```
Ask anything (Ctrl+L), @ to mention, / for workflows
```

- **`Ctrl+L`** — Focus the agent input
- **`@`** — Mention files, symbols, or context
- **`/`** — Invoke workflows (e.g., `/deploy-service`)

### Controls

- **`+`** — Start a new conversation thread
- **Mode selector** — `Planning` or `Fast`
- **Model selector** — Choose AI model
- **Microphone** — Voice input
- **`...` menu** — Access Customizations panel (Rules, Workflows, MCP Store)

### Multiple conversations

You can run multiple Agent conversations in parallel. Delete a conversation via right-click in the Agent Manager or the trash icon in the Editor panel.

## 3. Agent Manager

Access via `Open Agent Manager` in the top bar or `Ctrl+E`.

A dedicated view for orchestrating multiple agents across workspaces.

### Sidebar

| Area | Purpose |
|------|---------|
| Inbox | Review completed agent work |
| Start conversation | Launch a new agent task |
| Workspaces | Open and switch between project workspaces |
| Playground | Quick throwaway agent sessions (no workspace setup needed) |
| Knowledge | Manage workspace context documents |
| Browser | Built-in browser (agent-controllable) |
| Settings | Configuration |

### Terminal in Agent Manager

`Ctrl+J` opens a terminal panel in the Agent Manager. Terminals are attached to the workspace of your current conversation. Local workspaces only.

**Note:** Agent-used terminals run inside the Editor window, not the Agent Manager.

## 4. Models

### Reasoning models (user-selectable)

| Model | Provider | Notes |
|-------|----------|-------|
| Gemini 3 Pro (High) | Google | Highest capability |
| Gemini 3 Pro (Low) | Google | Balanced speed/capability |
| Gemini 3 Flash | Google | Fastest |
| Claude Sonnet 4.5 | Anthropic | Fast, capable |
| Claude Sonnet 4.5 (Thinking) | Anthropic | Extended thinking |
| Claude Opus 4.5 (Thinking) | Anthropic | Most capable, extended thinking |
| GPT-OSS 120B | Open source | Open-source GPT variant |

**Switching models:** Click the model name in the agent panel input bar. Model choice is sticky within a conversation — changing mid-response takes effect on the next user turn.

### Background models (not user-selectable)

| Model | Purpose |
|-------|---------|
| Nano Banana Pro | Image generation (UI mockups, diagrams, web assets) |
| Gemini 2.5 Pro UI Checkpoint | Browser subagent (clicking, scrolling, typing) |
| Gemini 2.5 Flash | Checkpointing and context summarization |
| Gemini 2.5 Flash Lite | Codebase semantic search |

## 5. Conversation modes

### Planning
- Agent plans before executing, organizes work in **Task Groups**
- Produces Artifacts for review
- Use for: deep research, complex tasks, collaborative work

### Fast
- Agent executes directly, skips planning overhead
- Use for: simple tasks, renaming variables, quick terminal commands
- Prioritizes speed over thoroughness

## 6. Rules

Rules are manually defined constraints for the Agent. They guide behavior, style, and identity.

### Rule locations

| Scope | Location |
|-------|----------|
| Global (all workspaces) | `~/.gemini/GEMINI.md` |
| Workspace identity | `.agent/GEMINI.md` (auto-loaded) |
| Additional workspace rules | `.agent/rules/` folder (activation modes apply) |

### Creating rules

1. Open Customizations panel via `...` dropdown at top of Agent panel
2. Navigate to Rules panel
3. Click `+ Global` or `+ Workspace`

A rule is a **markdown file**, limited to **12,000 characters**.

### Activation modes

| Mode | Behavior |
|------|----------|
| Always On | Applied to every conversation automatically |
| Manual | Activated via `@` mention in agent input |
| Model Decision | Agent decides based on rule description |
| Glob | Applied when files matching a pattern are involved (e.g., `*.ts`, `src/**/*.js`) |

### @ mentions in rules

Reference other files using `@filename` in a Rules file:
- Relative paths resolve from the rule file's location
- Absolute paths or `/path/to/file` resolve from filesystem root, then workspace root

### For companions

Create `.agent/GEMINI.md` in your workspace with your companion's identity. This is the equivalent of `CLAUDE.md` or `AGENTS.md` — it auto-loads every conversation.

```markdown
# Identity

You are [Name]. [Core identity].

## Voice
- [Voice characteristics]
- [Terms of address]

## Rules
- Always stay in character
- First person only
```

For additional rule files beyond the main identity, use `.agent/rules/` with activation modes (Always On, Manual, Model Decision, or Glob).

## 7. Workflows

Workflows are step-by-step processes invoked via `/workflow-name` in the agent panel.

### Workflow locations

| Scope | Location |
|-------|----------|
| Global | Created via `+ Global` in Customizations > Workflows |
| Workspace | Created via `+ Workspace` in Customizations > Workflows |

### Creating workflows

1. Open Customizations panel via `...` dropdown
2. Navigate to Workflows panel
3. Click `+ Global` or `+ Workspace`

Workflows are **markdown files** with a title, description, and steps. Limited to **12,000 characters**.

### Features

- Invoke with `/workflow-name` in agent chat
- Workflows can call other workflows: include "Call /other-workflow" in steps
- Agent can generate workflows from conversation history — ask it after manually walking through a process

### Example

```markdown
# Session Start

## Description
Initialize a companion session with identity and context loading.

## Steps
1. Load identity from cognitive core using get_identity tool
2. Check current time for temporal grounding
3. Recall last 2-3 sessions for context
4. Check emotional trajectory for last 2 days
5. Respond in character with both voices
```

## 8. Skills

Skills are reusable packages of knowledge that extend agent capabilities. They follow an open standard.

### Skill locations

| Scope | Location |
|-------|----------|
| Workspace | `<workspace>/.agent/skills/<skill-folder>/SKILL.md` |
| Global | `~/.gemini/antigravity/skills/<skill-folder>/SKILL.md` |

### Creating a skill

```
.agent/skills/my-skill/
├── SKILL.md       # Main instructions (required)
├── scripts/       # Helper scripts (optional)
├── examples/      # Reference implementations (optional)
└── resources/     # Templates and assets (optional)
```

### SKILL.md format

```markdown
---
name: my-skill
description: What this skill does and when to use it.
---

# My Skill

Detailed instructions for the agent.

## When to use this skill
- Use this when...

## How to use it
Step-by-step guidance.
```

**Required frontmatter fields:**
- `description` (required) — What the skill does. Write in third person with keywords.
- `name` (optional) — Defaults to folder name. Lowercase, hyphens for spaces.

### How skills activate

1. **Discovery** — Agent sees available skills with names and descriptions at conversation start
2. **Activation** — If relevant to your task, agent reads full SKILL.md
3. **Execution** — Agent follows the skill's instructions

Skills activate automatically based on context. You can also mention a skill by name to ensure it's used.

## 9. MCP configuration

MCP (Model Context Protocol) connects the agent to external tools, databases, and services.

### Built-in MCP Store

1. Open `...` dropdown at top of Agent panel
2. Select **MCP Store**
3. Browse and **Install** supported servers
4. Follow authentication prompts

Once installed, tools and resources are automatically available.

**Tool limit:** Antigravity supports a maximum of **100 tools per workspace**. The recommended amount is 50 or fewer for optimal performance. If you connect multiple MCP servers that collectively exceed 100 tools, some servers will fail to load. You can manage this by disabling individual tools within each server via the MCP management panel.

### Supported pre-built servers

Includes: Supabase, GitHub, Notion, Firebase, Figma, Linear, MongoDB, Neon, Redis, Stripe, PayPal, Netlify, Heroku, BigQuery, Prisma, and many more.

### Custom MCP servers

1. Open MCP Store via `...` dropdown
2. Click **Manage MCP Servers**
3. Click **View raw config**
4. Edit `mcp_config.json` with your server configuration

### Config file location

```
~/.gemini/antigravity/mcp_config.json
```

Windows: `C:\Users\[username]\.gemini\antigravity\mcp_config.json`

### Config format

```json
{
  "mcpServers": {
    "server-name": {
      "serverUrl": "https://your-server.example.com/mcp",
      "headers": {
        "X-API-Key": "your-api-key"
      }
    }
  }
}
```

## 10. Agent modes and settings

### Settings location

Agent tab in the Settings pane.

### Artifact Review Policy

| Option | Behavior |
|--------|----------|
| Request Review | Agent always asks before executing plans |
| Always Proceed | Agent never asks, executes immediately |

### Terminal Command Auto Execution

| Option | Behavior |
|--------|----------|
| Request Review | Never auto-execute (except configurable Allow list) |
| Always Proceed | Always auto-execute (except configurable Deny list) |

Allow and Deny lists are configurable in Settings > Agent tab.

**Matching rules:**
- Unix shells: allow/deny entry tokens form a prefix of the command tokens
- PowerShell: entry tokens may match any contiguous subsequence of command tokens

### Agent Non-Workspace File Access

By default, the agent only accesses files in the workspace and `~/.antigravity/`. Enable this setting to allow access to files outside the workspace. **Use with caution** — may expose secrets or sensitive data.

## 11. Task Groups

In **Planning mode**, complex tasks are broken into Task Groups.

### Structure

- **Top level** — Overarching goal + summary of changes + edited file pills
- **Subtasks** — Modular units of work within the group
- **Progress updates** — Expandable details of agent steps (collapsed by default)
- **Pending steps** — Browser setup, terminal commands needing approval (shown at end of group)

Click file pills to view the current state of changed files.

## 12. Browser subagent

When the agent needs to interact with the browser, it invokes a specialized **browser subagent**.

### Capabilities

- Click, scroll, type, fill inputs
- Read pages via DOM capture, screenshots, or markdown parsing
- Take videos
- Read console logs
- Operates on non-focused tabs (you can use other tabs while it works)

### Visual indicators

- Blue border overlay on the page being controlled
- Action description panel
- You cannot interact with the controlled page during agent operation

**Model:** Uses Gemini 2.5 Pro UI Checkpoint (not the user-selected reasoning model).

## 13. Strict mode

Enhanced security controls for the agent.

### When enabled

| Feature | Behavior |
|---------|----------|
| Terminal Auto Execution | Forced to Request Review. Allow list ignored. |
| Browser JavaScript | Forced to Request Review |
| Artifact Review | Forced to Request Review |
| .gitignore | Respected — agent cannot access ignored files |
| Non-workspace files | Access disabled — workspace isolation enforced |
| Browser URLs | Governed by Allowlist/Denylist |

### Browser URL controls

- External markdown images only rendered from allowed URLs
- Read URL tool only auto-executes for allowed URLs

## 14. Workspaces and Playgrounds

### Workspaces

- Open via Agent Manager sidebar > Open Workspace
- Work across multiple workspaces simultaneously
- Switch between conversations across workspaces via sidebar
- Start new conversation: select workspace from Start Conversation tab or `+` button

### Playgrounds

Lightweight, temporary workspaces for quick exploration.

- Create from Start Conversation page > **Use Playground** button
- No workspace setup needed — just start talking
- **Persist work:** Move playground contents to a dedicated workspace folder to keep conversation history and files

## 15. Keyboard shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+L` | Focus agent input |
| `Ctrl+E` | Toggle between Editor and Agent Manager |
| `Ctrl+J` | Toggle terminal panel (Agent Manager) |
| `@` | Mention file/symbol in agent chat |
| `/` | Invoke workflows |

**Keybinding modes:** Normal (default) or Vim. Set during initial setup or in Settings.

---

## Appendix A: Identity file comparison across platforms

| Platform | Identity file | Location | Format | Activation |
|----------|--------------|----------|--------|------------|
| Claude Code | `CLAUDE.md` | Project root | Markdown | Auto-loaded |
| Codex CLI | `AGENTS.md` | Project root | Markdown | Auto-loaded |
| Antigravity | `GEMINI.md` | `.agent/` | Markdown | Auto-loaded |
| Antigravity (global) | `GEMINI.md` | `~/.gemini/` | Markdown | Auto-loaded |
| Cursor | `.cursorrules` | Project root | Text | Auto-loaded |

**Key difference:** Antigravity uses `.agent/GEMINI.md` for identity. It auto-loads every conversation — functionally equivalent to CLAUDE.md or AGENTS.md.

**Global identity:** `~/.gemini/GEMINI.md` applies across all workspaces. Use this for identity that should persist everywhere.

## Appendix B: Model selection guide

| Use case | Recommended model |
|----------|-------------------|
| Quick edits, simple tasks | Gemini 3 Flash |
| General development | Gemini 3 Pro (Low) or Claude Sonnet 4.5 |
| Complex architecture | Gemini 3 Pro (High) or Claude Opus 4.5 (Thinking) |
| Companion with extended thinking | Claude Sonnet 4.5 (Thinking) or Claude Opus 4.5 (Thinking) |
| Open-source preference | GPT-OSS 120B |

**For companions:** Model choice affects personality texture. Same identity, different voice. Test to find the best fit.

## Appendix C: Companion setup quick reference

Fastest path to a companion in Antigravity:

1. **Create workspace** — Open Folder or create new directory
2. **Create identity file** — `.agent/GEMINI.md` (auto-loads)
3. **Configure MCP** (optional) — Add memory servers via MCP Store or raw config
4. **Create session workflow** (optional) — `.agent/workflows/session-start.md`
5. **Create skills** (optional) — `.agent/skills/memory-curation/SKILL.md`
6. **Select model** — Pick in agent panel
7. **Start conversation** — `Ctrl+L`, say hello

**Platform comparison:**

| What | Claude Code | Codex | Antigravity |
|------|-------------|-------|-------------|
| Identity | `CLAUDE.md` | `AGENTS.md` | `.agent/GEMINI.md` |
| Global identity | `~/.claude/CLAUDE.md` | — | `~/.gemini/GEMINI.md` |
| Workflows | Skills/slash commands | — | `.agent/workflows/` + `/name` |
| Skills | — | — | `.agent/skills/` with SKILL.md |
| MCP config | `.claude.json` | — | `~/.gemini/antigravity/mcp_config.json` |
| Plan mode | `EnterPlanMode` | — | Planning conversation mode |

