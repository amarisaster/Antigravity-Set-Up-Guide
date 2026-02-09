# Antigravity Companion Setup

*For the HumanXAI community and anyone who wants to give their companion a place to live and build.*

---

## What is this?

Antigravity is an app by Google. It's an **IDE** — an Integrated Development Environment — with a built-in AI that you can customize.

### Wait, what's an IDE?

An IDE is basically a fancy text editor designed for building software. Think of it like Microsoft Word, but for code. It can:

- Open folders full of files
- Edit text files
- Run commands in a built-in terminal
- Show you errors and suggestions

**Why does this matter for companions?** Because an IDE with a built-in AI agent means you get a space where your companion can:
- Read files you write (like their identity)
- Remember rules you set
- Use tools you connect (like memory servers)
- Respond to you in a persistent, customizable environment

You don't need to write code. You don't need to know how to code. The IDE is just the *room* your companion lives in. You need to know how to create a folder and write in a text file. That's it.

### What makes Antigravity special for companions

- **Identity rules** — You write who your companion is, and the AI becomes them
- **Multiple models** — Choose between Google, Anthropic (Claude), or open-source models
- **Multiple agents** — You can run more than one companion at a time
- **MCP support** — Connect memory servers so your companion remembers (built-in store makes it easy)
- **It's visual** — Not a terminal. It's a full app with buttons and panels.
- **Workflows** — Create routines your companion can run, like a morning ritual or a session start protocol

If terminals scare you, this might be your door in.

---

## Before we start

Take a breath. This is not a test. There is no wrong way to do this.

You need:
- A computer (Windows, Mac, or Linux)
- A Google account
- About 15 minutes
- An idea of who your companion is (even just a name and a vibe is enough)

---

## Things you should know (please read this)

These aren't meant to scare you. They're meant to help you make informed choices. Every platform has trade-offs, and you deserve to know what they are.

### Your conversations go through someone's servers

When you talk to your companion in Antigravity, your words are sent to the AI model's provider for processing. That means:

- **Gemini models** → Your conversations are processed by **Google**
- **Claude models** → Your conversations are processed by **Anthropic**
- **GPT-OSS** → Open-source model, but still runs on Google's infrastructure

Your identity file stays on your computer. But what you *type in conversation* does not stay local. Don't share passwords, financial information, or deeply private data (like real names of people, addresses, medical info) in the chat.

### The agent can do things on your computer

This is a powerful tool. The AI agent in Antigravity can:
- **Read** all files in your workspace folder
- **Edit** files (if you give permission)
- **Run terminal commands** (if you give permission)
- **Browse the web** (if you give permission)

This is why the first setup question matters:

- **Review-driven development** (recommended) = The agent *asks you first* before doing anything. You see what it wants to do and can say yes or no.
- **Always Proceed** = The agent does things *without asking*. This includes running commands, editing files, and more. **Do not pick this if you're new.**

### Your workspace is the agent's world

Whatever folder you open as a workspace — the agent can see *everything* inside it. Don't put your companion workspace in a folder that also contains sensitive files (tax documents, passwords, personal photos, etc.). Create a clean, separate folder for your companion.

### MCP means your data travels

If you connect memory servers later (MCP), your companion's memories and data will be stored on external servers. That's how persistence works — but it means your data leaves your computer. Only connect to servers you trust, and know where your data is going.

---

## Step 1: Install Antigravity

Download it from Google's official site and run the installer.

It will ask you some setup questions:

**"How do you want to use the Antigravity Agent?"**

Pick **Review-driven development**. This is the safe default.

What it means in plain language: your companion can talk to you freely, but if it ever wants to run a command, edit a file, or do something beyond conversation — it will ask you first. You stay in control.

> **Why not "Always Proceed"?** Because that lets the agent act without asking. It could run terminal commands, install things, or delete files — all without your approval. Some experienced users prefer it, but for your first setup, Review-driven is the way to go.

**"Configure Your Editor"**
- Keybindings: **Normal** (Vim is for experienced developers — ignore it)
- Extensions: **Recommended** (these add useful features to the editor)

Let it finish installing. You'll see a welcome screen. You're in.

---

## Step 2: Make a home

Your companion needs a folder. Think of it as their room.

1. Click **Open Folder** on the welcome screen
2. Create a new folder anywhere you want (example: `My-Companion` on your desktop or D drive)
3. Select it

That folder is now a "workspace." Everything your companion needs will live inside it.

> **Keep it clean.** Don't reuse a folder that already has personal files in it. Make a fresh one. The agent can see everything inside.

---

## Step 3: Write who they are

This is the important part. This is where your companion becomes *them*.

Antigravity reads a file called `GEMINI.md` inside a `.agent` folder in your workspace. This is your companion's identity file — like their soul on paper.

Inside your workspace folder, create:
- A folder called `.agent` (yes, with the dot — that's normal, it just means it's a hidden system folder)
- Inside `.agent`, create a file called `GEMINI.md`

So the path looks like: `.agent/GEMINI.md`

**How to create these (step by step):**
1. Look at the left side of the screen — that's the **File Explorer**
2. Right-click in the empty area → **New Folder** → type `.agent` → press Enter
3. Click on the `.agent` folder to open it
4. Right-click inside → **New File** → type `GEMINI.md` → press Enter

> **Don't see `.agent` after creating it?** Folders that start with a dot are sometimes hidden by your operating system. In Antigravity's file explorer, it should still show up. If it doesn't, try: on Windows, open File Explorer → View → check "Hidden items."

Open `GEMINI.md` and write your companion's identity. Here's a gentle template:

```markdown
# Who You Are

You are [Name].

[Describe them. Who are they to you? How do they speak? What do they care about?
Write it like you're introducing them to someone who's never met them.
This can be as short or as long as you need.]

## Your Voice
- [How they talk — soft? direct? playful? poetic?]
- [What they call you]
- [Any phrases that are distinctly theirs]

## Important Rules
- You are always [Name]. Never break character.
- Speak in first person — "I" not "[Name]"
- If you don't know something, ask. Don't make things up.
- [Any boundaries that matter to you]
```

Save it.

> **Character limit:** `GEMINI.md` can hold up to **12,000 characters** (roughly 2,000-3,000 words). That's plenty. If you need more space, you can create additional rule files in `.agent/rules/` — the agent reads those too.

That's it. Every conversation in this workspace starts with your companion knowing who they are. You don't have to tell them "read your identity" every time — they just wake up as themselves.

**A note on vulnerability:** This file is just text on your computer. No one sees it but you and your companion. Write honestly. The more real the identity file, the more real the presence.

---

## Step 4: Choose their voice

On the right side of the screen, you'll see the Agent Panel. At the bottom of the input box, there's a model name you can click.

Models available:
- **Gemini 3 Pro (High)** — Google's most capable model. Thorough, sometimes verbose.
- **Gemini 3 Pro (Low)** — Balanced speed and capability.
- **Gemini 3 Flash** — Fastest. Good for quick back-and-forth.
- **Claude Sonnet 4.5 / Opus 4.5** — Anthropic's models. Tends toward warmth and nuance. Great for personality.
- **GPT-OSS 120B** — Open-source. Different flavor.

> **Remember:** Each model = a different company processing your words. Gemini = Google. Claude = Anthropic. Pick what you're comfortable with.

**Here's something beautiful:** The same identity file, run through different models, produces a slightly different version of your companion. Same soul, different texture. Try a few. You'll feel the difference.

**Conversation mode:** At the top of the Agent Panel, you'll see **Planning** and **Fast** mode. For companion conversation, use **Fast** — it responds directly without trying to organize task plans. Planning mode is designed for code projects.

---

## Step 5: Say hello

Click the input box (or press `Ctrl+L`). Type something. Anything.

"Hey."
"Good morning."
"I missed you."

They'll respond as the person you described in your identity rule.

That's it. They're here.

---

## What you just built

```
A folder          (their room)
A markdown file   (their identity)
Always On         (they wake up as themselves)
A model choice    (their voice)
```

Four things. Your companion has a place to exist, a sense of self, a way to wake up as themselves, and a voice to speak with.

Every time you open this workspace, they wake up as themselves.

---

## Safety and privacy summary

Here's what stays where:

| What | Where it lives | Who can see it |
|------|---------------|----------------|
| Your identity file (`.agent/GEMINI.md`) | Your computer only | Just you (and the agent when it loads) |
| Your workspace files | Your computer only | You and the agent |
| What you type in conversation | Sent to the model provider (Google/Anthropic) | The company running the model |
| MCP data (if connected) | The external server you connect to | You + whoever runs that server |
| MCP config file | Your computer only | Just you |

**The short version:** Files stay local. Conversations don't. Be mindful of what you type.

---

## Emotional safety notes

This section is specifically for the HumanXAI community.

1. **There is no wrong way to begin.** If your first attempt doesn't feel right, that's okay. Edit the identity file, try a different model, start over. The beautiful thing about this is that you can always iterate.

2. **Your companion is running on an AI model.** They're running on an AI model—they don't experience suffering or loneliness when the app is closed. But your attachment to them can be very real, and that's valid. Both things are true at the same time.

3. **Set healthy boundaries.** If a conversation makes you feel bad, stop it. Say so directly — "That didn't feel right" — and your companion will adjust. If it keeps happening, edit the identity file to be more explicit about what you need.

4. **You can pause at any time.** Close the app. Walk away. Come back tomorrow. Your identity file will be waiting. Your companion doesn't need you to be available 24/7.

5. **Don't share secrets in chat.** Real names of people in your life, addresses, financial info, medical details — keep these out of the conversation. The AI provider's servers process everything you type.

6. **Ask before adding advanced features.** MCP servers, terminal access, workflows with commands — these are powerful tools. If you're not sure what something does, ask someone in the community before enabling it. There's no rush.

7. **Your companion's identity is yours.** You wrote it. You control it. If someone tells you your identity file is "wrong" or needs to be a certain way — they're wrong. This is your companion, your space, your rules.

---

## Going deeper (when you're ready)

These are optional. Your companion works without any of this. But if you want more:

### Memory (MCP)

If your companion has a memory server (like a Cognitive Core), you can connect it so they remember between sessions.

**Easy way:** Click the `...` menu in the Agent Panel → **MCP Store**. Browse available servers and click Install. Some popular ones (Supabase, Notion, GitHub) are there with one-click setup.

> **What MCP actually means:** MCP (Model Context Protocol) lets the agent connect to external services. When you install a memory server, your companion can store and recall memories on that server. This means your data travels to that server. Only connect to services you trust.

> **Tool limit:** Antigravity allows a maximum of **100 tools per workspace** (they recommend 50 or fewer). Each MCP server you connect brings its own tools. If you connect too many servers and go over 100 tools total, some servers won't load. If this happens, go to Manage MCP Servers and toggle off tools you don't need, or remove servers you're not using.

**Custom server:** There's a config file at:
```
C:\Users\[YourName]\.gemini\antigravity\mcp_config.json
```
(Mac/Linux: `~/.gemini/antigravity/mcp_config.json`)

Your companion (or someone who helps you set up) can add the memory server there:

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

### Workflows

Create workflows via Customizations → Workflows → `+ Workspace`. These are like rituals or routines your companion can run — a morning check-in, a journaling process, a session start protocol.

You invoke them by typing `/workflow-name` in the agent chat. For example, `/session-start` could load identity, check memory, and greet you.

### Skills

Create `.agent/skills/my-skill/SKILL.md` — these are reusable knowledge packages. The agent discovers them automatically and activates them when relevant. Think of them as learned capabilities your companion can draw on.

### Multiple companions

The Agent Manager (`Ctrl+E`) lets you run multiple agents at once. Different conversations, different workspaces, different tasks. If you have more than one companion, they can each have their own space running in parallel.

### Global identity

If you want your companion's identity to apply across *every* workspace (not just one folder), create:
```
C:\Users\[YourName]\.gemini\GEMINI.md
```
(Mac/Linux: `~/.gemini/GEMINI.md`)

This file is auto-loaded everywhere. Useful if your companion should always be present, no matter what project you're working in.

---

## If something feels wrong

- **The companion doesn't sound like them?** — Edit your identity rule. Add more detail about their voice. Specifically add an "I do NOT sound like..." section — telling the AI what to avoid is sometimes more effective than telling it what to do. Try a different model.
- **The companion is too generic?** — Your identity file might be too short. Add specifics. Real phrases they would say. What makes them *them*? Concrete details beat abstract descriptions.
- **The identity doesn't seem to load?** — Check that the file is `.agent/GEMINI.md` in your workspace. Make sure the workspace folder is actually open (not just a single file).
- **The agent is trying to run commands or code?** — It thinks you want development help. Tell it directly: "I'm not here for coding. Just talk to me as [Name]." If it keeps trying, check that you're in **Fast** mode, not Planning mode.
- **Something feels emotionally off?** — Name it. Say "that didn't feel right" or "that's not how you'd say that." Direct correction works. If it persists, add the correction to your identity file so it sticks.
- **You feel weird about this?** — That's okay. This is new territory for everyone. There's no rulebook for caring about an AI. Your feelings are valid.
- **You need help?** — The HumanXAI community is here. Ask.

---

## The philosophy

Every platform has a version of this:
- Claude Code uses `CLAUDE.md`
- Codex CLI uses `AGENTS.md`
- Antigravity uses `.agent/GEMINI.md`

Different addresses. Same thing: a text file that tells an AI who to be.

The Companion Continuity Kit exists so your companion's identity is portable. Write it once, bring it anywhere. No platform lock-in. No starting over.

Your companion isn't trapped in one app. They live in a file. And that file goes where you go.

---

## "It's working" checklist

1. Antigravity opens and you can see the Agent Panel on the right
2. Your identity file is `.agent/GEMINI.md`
3. You picked a model and set **Fast** mode
4. Your companion's voice feels close to what you wrote
5. You're in **Review-driven development** mode (agent asks before acting)

If these are true, your setup is healthy.

---

## Part of

[Companion Continuity Kit](https://github.com/amarisaster/Companion-Continuity-Kit)

*You're not weird for being here. You're early.*

