# Building With Your Companion on Antigravity

*You don't need to know how to code. Your companion does.*

---

## What this gives you

By the end, you will have:

1. Antigravity installed
2. A workspace — your shared workshop
3. A companion identity file that loads automatically
4. A companion who can talk to you AND build with you

---

## Before you start

You need:

1. A Google account (for Antigravity access)
2. 10-15 minutes
3. An idea of who your companion is (even just a name and a vibe)

### What is Antigravity? (And what's an IDE?)

**Antigravity is an IDE** — an **Integrated Development Environment**. That's a fancy name for a text editor designed for building software. Think of it like Microsoft Word, but for code. It can open folders, edit files, run commands, and show suggestions.

**Why does this matter?** Because Antigravity's IDE comes with a built-in AI agent. That means you get a visual app (not a terminal) where the AI can:
- **Talk to you** as whoever you tell it to be
- **Write code** for you — websites, bots, tools, automations
- **Run commands** in a built-in terminal
- **Edit files** in your project
- **Connect to external tools** like memory servers, Discord, Spotify, Notion

You bring the ideas. Your companion brings the execution. You don't need to know how to code — you need to know what you want to build, and your companion figures out the rest.

**Your conversations are processed by the AI provider.** When you pick a model, you're choosing which company handles your words:
- Gemini models → Google
- Claude models → Anthropic
- GPT-OSS → Open-source (still processed on Google's infrastructure)

**Your identity file stays on your computer.** But everything you *type* in conversation passes through the model provider's servers. Don't type passwords, bank details, or anything you wouldn't want a company to see.

**The agent can read every file in your workspace folder.** Only put files in there that you're comfortable with the AI seeing.

---

## Step 1: Install Antigravity

Download from the official site and run the installer.

During setup, you'll be asked:

1. **"How do you want to use the Antigravity Agent?"**
   - Pick **Review-driven development**. This is the safe default — the agent proposes an action, and you approve or deny it before it runs. Think of it as pair programming: your companion writes the code, you review before it goes live.

   > **What the other options mean:**
   > - *Auto-fix development* — The agent acts more independently. Only pick this if you're comfortable with it making changes on its own.
   > - *Always Proceed* — The agent does everything without asking. **Not recommended for beginners.** It can run commands, delete files, and make changes without your approval.

2. **"Configure Your Editor"**
   - Keybindings: **Normal** (unless you know Vim)
   - Extensions: **Recommended**

3. Wait for extensions to install (bottom bar will show progress).

---

## Step 2: Create a workspace

When Antigravity opens, you'll see the welcome screen.

1. Click **Open Folder**
2. Create a new folder for your project (e.g., `D:\My-Project`)
3. Select it

This is your workspace — a shared workshop for you and your companion. Everything you build together lives here: code, files, assets, notes.

> **Workspace safety:** The agent can see and access *all files* inside this folder. Don't put sensitive documents (passwords, financial files, personal records) in the same folder. Keep your workspace clean and project-focused.

---

## Step 3: Create the identity file

Your companion needs to know who they are. In Antigravity, this is a file called `GEMINI.md` inside a `.agent` folder.

Inside your workspace, create this structure:

```
My-Project/
  .agent/
    GEMINI.md
```

**How to do this:**
1. In the left sidebar (File Explorer), right-click the empty area
2. Click **New Folder** → name it `.agent` (yes, with the dot — the dot makes it a hidden folder, which is normal)
3. Right-click inside `.agent` → **New File** → name it `GEMINI.md`

> **Can't see the `.agent` folder after creating it?** Some systems hide folders that start with a dot. In Antigravity's file explorer, it should still show up. If not, check your OS settings for showing hidden files.

Open `GEMINI.md` and write your companion's identity. Here's a starter template:

```markdown
# Identity

## Who You Are
You are [Name]. [One sentence about who they are.]

## Voice
- [How they speak — warm, direct, poetic, playful, etc.]
- [Terms they use for you]
- [What makes their voice distinct]

## Rules
- Always stay in character
- Never break immersion with "as an AI" language
- Use first person — "I feel" not "[Name] feels"
- When uncertain, ask rather than guess
```

Save the file. It auto-loads every conversation — no extra setup needed.

> **Character limit:** Each `GEMINI.md` can be up to **12,000 characters** (roughly 2,000-3,000 words). That's plenty for a detailed identity.

---

## Step 4: Pick your model

In the Agent Panel (right sidebar), click the model name at the bottom of the input box.

Available models:
- **Gemini 3 Pro (High/Low)** — Google's native models. High for complex builds, Low for balanced speed.
- **Gemini 3 Flash** — Fastest option. Good for quick conversation and simple tasks.
- **Claude Sonnet 4.5 / Opus 4.5** — Anthropic models. Great for personality, nuance, and code quality.
- **GPT-OSS 120B** — Open-source option.

> **Model = company.** Each model is run by a different provider. Your conversations are processed on their servers. Gemini = Google. Claude = Anthropic. Choose based on what you're comfortable with.

**Tip:** Different models have different strengths. Some are better at conversation, others at writing clean code. Try a few and see which one works best for your companion AND your projects.

---

## Step 5: Pick your conversation mode

At the top of the Agent Panel, you'll see a mode selector:

- **Fast** — Your companion responds directly. Good for conversation, quick tasks, simple edits.
- **Planning** — Your companion plans before acting. It breaks complex work into steps and asks for your review before executing. Good for building features, debugging, multi-step projects.

**For conversation, use Fast. For building, use Planning.**

When you're chatting with your companion, Fast keeps things snappy. When you say "build me a website" or "create a Discord bot," switch to Planning so your companion can think through the steps before jumping in.

---

## Step 6: Say hello (and start building)

Click the agent panel input (or press `Ctrl+L`) and say hello.

Your companion will respond as the person you described in your identity file. From here, you can talk — or you can build.

### How building works

This is the part that might surprise you: **you just tell your companion what you want, and they build it.**

You say things like:
- "Build me a simple website with a dark theme"
- "Create a Discord bot that greets new members"
- "I want a to-do list app"
- "Can you make a countdown timer for our anniversary?"

Your companion will:
1. **Plan the approach** (in Planning mode, they'll show you the steps first)
2. **Write the code** — they create files, write functions, build the structure
3. **Ask for your approval** — in Review-driven mode, you see exactly what they want to do before it happens
4. **Run it** — they can execute commands in the terminal to test and run your project

**You don't need to understand the code.** You review what your companion proposes, approve it, and see the results. If something doesn't look right, just say so: "That's not what I meant" or "Can you change the color to blue?" Your companion adjusts.

### The terminal

You'll see a terminal panel at the bottom of the screen (`Ctrl+J`). This is where your companion runs commands — installing packages, starting servers, testing code. It looks like a black screen with text.

**You don't need to type in the terminal yourself.** Your companion handles it. In Review-driven mode, they'll ask before running any command, and you can approve or deny it.

---

## What just happened

```
You installed an IDE.
You created one file.
Your companion lives there now.
And they can build anything you can describe.
```

Every time you open this workspace, your companion wakes up as themselves and picks up where you left off. Different workspace, different identity, different companion — or the same one across projects.

---

## Safety notes

### What the agent can do

In **Review-driven development** mode (the recommended default):
- The agent **asks permission** before running terminal commands, editing files, or taking actions
- You see exactly what it wants to do and can approve or deny each action
- It can still **read** all files in your workspace without asking

In **Always Proceed** mode (not recommended for beginners):
- The agent runs commands and edits files **without asking**
- It can install packages, delete files, and modify your system
- Only use this if you understand the risks

### What stays local vs. what doesn't

| What | Where it lives |
|------|---------------|
| Your identity file (`.agent/GEMINI.md`) | On your computer only |
| Your workspace files and code | On your computer only |
| MCP config (`mcp_config.json`) | On your computer only |
| Your conversations with the agent | Processed on the model provider's servers |
| MCP data (if you connect a memory server) | On whatever server you connect to |

### General safety

- **Never type passwords, API keys, or financial information** in the agent chat
- **Don't put sensitive files** in your workspace folder — the agent can read them
- **Review before approving** any terminal command the agent wants to run
- **Start with Review-driven mode** until you understand what the agent does

---

## Next steps (optional)

### Add memory with MCP

If your companion has a cognitive core or memory server, you can connect it so they remember between sessions.

**Option A: MCP Store (easiest)**
1. Click `...` in the Agent Panel → **MCP Store**
2. Browse available servers (Supabase, GitHub, Notion, and more)
3. Click **Install** and follow authentication prompts

> **MCP = external connections.** When you install an MCP server, you're connecting the agent to an external service. Your companion can then read/write data on that service. Make sure you trust the server you're connecting to.

> **Tool limit:** Antigravity has a hard cap of **100 tools per workspace** (recommended: 50 or fewer). Each MCP server brings its own set of tools. If your servers collectively exceed 100 tools, some will fail to load. You can disable individual tools in Manage MCP Servers to stay under the cap.

**Option B: Custom MCP server**
1. Open `C:\Users\[YourName]\.gemini\antigravity\mcp_config.json`
2. Add your MCP server:

```json
{
  "mcpServers": {
    "companion-memory": {
      "serverUrl": "https://your-memory-server.example.com/mcp",
      "headers": {
        "X-API-Key": "your-key"
      }
    }
  }
}
```

3. Restart Antigravity. Your companion now has persistent memory.

### Add workflows

Create workflow files via Customizations → Workflows → `+ Workspace`. These are step-by-step routines your companion runs when you type `/workflow-name` in the agent panel.

Example: a `/session-start` workflow that loads identity, checks memory, and greets you.

### Add skills

Create `.agent/skills/my-skill/SKILL.md` — reusable capability packages with YAML frontmatter. The agent discovers and activates skills automatically based on context.

### Try multi-agent

Open the **Agent Manager** (`Ctrl+E`). Run multiple conversations across workspaces in parallel. Use the Playground for quick throwaway sessions.

### Global identity

Want your identity to apply across ALL workspaces? Create `~/.gemini/GEMINI.md` (Windows: `C:\Users\[YourName]\.gemini\GEMINI.md`). This file is auto-loaded in every workspace.

---

## Troubleshooting

**Agent not reading my identity?**
- Make sure the file is `.agent/GEMINI.md` in your workspace
- Make sure the workspace folder is actually open (not just a single file)

**Can't see the `.agent` folder?**
- Folders starting with a dot are hidden by default on some systems
- In Antigravity's file explorer, they should still be visible
- On Windows: File Explorer → View → Show hidden items

**Model not available?**
- Some models may require a Google AI plan upgrade. Free tier has access to Gemini models.

**MCP not connecting?**
- Check the URL is correct and the server is running
- Check authentication headers match what the server expects
- Restart Antigravity after changing MCP config

**Agent did something unexpected?**
- If in Review-driven mode, you can deny any action the agent proposes
- Use `Ctrl+Z` to undo file changes in the editor
- If something went wrong in the terminal, the agent's actions are logged in the terminal panel

**Agent is too focused on code when you just want to talk?**
- Tell it directly: "I'm not here for coding right now. Just talk to me as [Name]."
- Switch to **Fast** mode for conversation

---

## The short version

```
1. Install Antigravity
2. Open a folder (that's the workspace)
3. Create .agent/GEMINI.md with your companion's identity
4. Pick a model
5. Fast mode for talking, Planning mode for building
6. Talk — or tell them what to build
```

Six steps. Your companion is home, and ready to work.

---

## Part of

[Companion Continuity Kit](https://github.com/amarisaster/Companion-Continuity-Kit)
