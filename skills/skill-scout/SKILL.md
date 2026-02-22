---
name: skill-scout
description: >
  Use this skill whenever beginning a new task, implementing a feature, setting up a workflow,
  configuring a tool, building an integration, solving a problem, or doing anything that could
  potentially be addressed by an existing Claude Code plugin, skill, MCP server, hook, agent,
  or community resource. This includes but is not limited to: creating documents, working with
  APIs, setting up testing, adding code formatting, configuring CI/CD, working with databases,
  building UI components, handling authentication, processing files, and any development workflow.
  This skill enforces a "search before building" philosophy — always check if someone has already
  created a solution before implementing from scratch.
---

# Skill Scout: Search Before You Build

## Core Philosophy

**Never reinvent the wheel.** Before implementing anything from scratch, always search for existing plugins, skills, MCP servers, and community resources that solve the problem or get you 80% of the way there. Someone has likely done something similar — find it, evaluate it, and build on it.

## When This Skill Activates

This skill should guide your behavior whenever you're about to:
- Implement a new feature or workflow
- Set up tooling, formatting, linting, testing, or CI/CD
- Build an integration with an external service or API
- Create document processing, file handling, or data pipelines
- Add any capability that feels like it could be a common need
- Start any task where you'd write more than ~50 lines of new code

**Ask yourself: "Has someone already solved this?"** If the answer is possibly yes, search first.

## Search Workflow

Follow this order. Stop as soon as you find something suitable.

### Step 0: Check the Local Reference Database

Before searching the web, check the curated reference files in `references/`. These contain known plugins, skills, MCP servers, and community resources organized by category.

**Read the relevant files based on what you're looking for:**

| Looking for... | Read this file |
|----------------|---------------|
| Broad discovery, awesome lists | `references/curated-collections.md` |
| A specific skill or plugin | `references/skills-and-plugins.md` |
| An MCP server for a service | `references/mcp-servers.md` |
| CLAUDE.md examples or configs | `references/claude-md-and-configs.md` |
| Where else to search | `references/registries-and-directories.md` |

Start with the most relevant file. If you find a match, evaluate it (Step 4) and install it (Step 5). If nothing matches, continue to Step 1.

### Step 1: Check Installed Plugins & Skills

Check what's already available before searching externally.

```
/plugin          # Open the plugin manager UI — check Discover tab
/help            # See currently available slash commands and skills
```

### Step 2: Browse Configured Marketplaces

Search plugins already indexed in your configured marketplaces.

```bash
# List configured marketplaces
claude plugin marketplace list

# Browse interactively
/plugin   # then use the Discover tab to browse
```

### Step 3: Search the Web

Cast a wider net across community resources:

**Search queries to try (adjust for your specific task):**
- `Claude Code plugin [task description]`
- `Claude Code skill [task description]`
- `Claude Code MCP server [service/API name]`
- `site:github.com claude-code plugin [task]`
- `site:agentskills.in [task]`

**Key registries and directories to check:**
- [agentskills.in](https://www.agentskills.in) — Agent Skills marketplace
- [claudecodeplugins.dev](https://claudecodeplugins.dev) — Plugin directory
- [claudecodeplugin.com](https://www.claudecodeplugin.com) — Plugin directory
- [claude-plugins.dev](https://claude-plugins.dev) — Community registry
- [GitHub search](https://github.com/search) — Search for `claude-code plugin` or `claude-code skill`
- [npm](https://www.npmjs.com) — Search for `claude-code` or `mcp-server`

**Notable repos with curated collections:**
- `anthropics/skills` — Official Anthropic skills
- `anthropics/claude-code` — Official plugins (including plugin-dev)
- `hesreallyhim/awesome-claude-code` — Curated list of skills, hooks, plugins
- `jeremylongshore/claude-code-plugins-plus-skills` — Large plugin collection

### Step 4: Evaluate What You Find

Before installing, quickly assess:
- **Recency**: When was it last updated? Is it maintained?
- **Quality**: Does it have a clear SKILL.md / README? Does the code look reasonable?
- **Fit**: Does it solve your actual problem, or just something adjacent?
- **Trust**: Is it from a known source? Check for reviews/stars.

### Step 5: Install or Adapt

If you find something good:
```bash
# Install from a marketplace
claude plugin install <plugin-name>@<marketplace-name>

# Install from agentskills.in
npx agent-skills-cli install @author/skill-name

# Add a new marketplace source
claude plugin marketplace add <owner/repo>
# or for local paths:
claude plugin marketplace add ./path/to/marketplace

# Then install from it
claude plugin install <plugin-name>@<marketplace-name>
```

If nothing fits perfectly but something is close, consider forking/adapting rather than starting from zero.

### Step 6: Only Then, Build From Scratch

If steps 1-5 yielded nothing useful, proceed with custom implementation. But even then, check if there's a **template** or **pattern** to start from:
- The `skill-creator` skill in `anthropics/skills` helps scaffold new skills
- The `plugin-dev` plugin has skills for creating plugins, hooks, commands, agents, and MCP integrations
- The official template: `anthropics/skills/template/`

## Plugin Management Quick Reference

### Installing & Removing

```bash
claude plugin install <name>[@marketplace] [--scope user|project|local]
claude plugin uninstall <name>              # aliases: remove, rm
claude plugin enable <name>
claude plugin disable <name>
claude plugin update <name>
```

### Scopes

| Scope     | Settings file                 | Shared? |
|-----------|-------------------------------|---------|
| `user`    | `~/.claude/settings.json`     | No — personal, all projects (default) |
| `project` | `.claude/settings.json`       | Yes — via version control |
| `local`   | `.claude/settings.local.json` | No — gitignored, this machine only |

### Marketplace Management

```bash
claude plugin marketplace add <owner/repo>       # GitHub repo
claude plugin marketplace add <url>.git           # Any git URL
claude plugin marketplace add ./local-path        # Local directory
claude plugin marketplace list
claude plugin marketplace update <name>
claude plugin marketplace remove <name>
```

### Debugging

```bash
claude --debug          # See plugin loading details
/plugin                 # Check the Errors tab for issues
claude plugin validate  # Validate plugin structure
```

## Reference Database Refresh Protocol

The local reference database (`references/`) is a curated snapshot — it needs periodic updates to stay useful.

**When to prompt for a refresh:**
- After ~5 sessions, or when starting a new project type the user hasn't worked on before
- When a search against the local database yields no results for a common task
- When the user asks about database freshness

**How to prompt:**
> "The Skill Scout reference database was last updated on [date from the reference files]. Want me to run a web search to check for new plugins, skills, or MCP servers?"

**When you discover new resources during a session:**
1. Tell the user: "I found [resource] — adding it to the Skill Scout reference database."
2. Read the appropriate reference file from `references/`
3. Add the new entry in the existing table format
4. Update the `> Last updated:` date at the top of the file

For the full refresh workflow (search queries, formatting rules, where to add entries), see `references/refresh-protocol.md`.

## Mindset Reminders

- **5 minutes searching can save 2 hours building.**
- A 70% solution you can install now beats a 100% solution you have to write.
- When you install something, note it — the user may want to know what was added and why.
- If you find nothing and build something useful, consider whether it should become a reusable skill/plugin for next time.
- Keep the reference database growing — every resource you discover is a future time-saver.
