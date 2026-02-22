# Skill Scout

A Claude Code skill that enforces a **"search before you build"** philosophy. Before implementing anything from scratch, Skill Scout checks a curated local database of plugins, skills, MCP servers, and community resources — then falls back to web searches only when needed.

## Why

5 minutes searching can save 2 hours building. The Claude Code ecosystem is growing fast — there are thousands of plugins, skills, and MCP servers across dozens of registries and awesome lists. Skill Scout makes sure you check what already exists before writing something new.

## How It Works

Skill Scout activates whenever you're about to implement a feature, set up tooling, build an integration, or start any task that could be addressed by an existing resource. It follows a prioritized search workflow:

1. **Local reference database** — Curated, categorized, instant lookup
2. **Installed plugins & skills** — What's already available in your environment
3. **Configured marketplaces** — Browse the Discover tab
4. **Web search** — Cast a wider net across registries and GitHub
5. **Evaluate & install** — Assess fit, recency, and quality
6. **Build from scratch** — Only as a last resort

## Local Reference Database

The `references/` directory contains categorized resource files that are checked first:

| File | Contents |
|------|----------|
| `curated-collections.md` | Awesome lists, mega-repos, and web directories |
| `skills-and-plugins.md` | Individual skills and plugins by category |
| `mcp-servers.md` | MCP servers organized by domain |
| `claude-md-and-configs.md` | CLAUDE.md examples and configuration collections |
| `registries-and-directories.md` | Where to search when local DB doesn't have it |
| `refresh-protocol.md` | How to keep the database current |

The database is seeded with resources from across the ecosystem and grows organically as new resources are discovered during sessions.

## Self-Maintaining

Skill Scout includes a refresh protocol — after roughly every 5 sessions or when starting a new project type, it prompts to run web searches for new resources and adds discoveries back to the reference files with updated timestamps.

## Install

Clone into your Claude Code skills directory:

```bash
git clone https://github.com/michaelcarwile/claude-skill-skill-scout.git ~/.claude/skills/skill-scout
```

That's it — Claude Code automatically picks up skills from `~/.claude/skills/`.

## License

MIT
