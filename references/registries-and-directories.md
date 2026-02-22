# Registries & Directories — Where to Search
> Last updated: 2026-02-22

When the local reference database doesn't have what you need, search these sources.

## Web Directories

| Directory | URL | Best For |
|-----------|-----|----------|
| Agent Skills | [agentskills.in](https://www.agentskills.in) | Skills with CLI install (`npx agent-skills-cli install @author/name`) |
| Claude Code Plugins | [claudecodeplugins.dev](https://claudecodeplugins.dev) | Plugin discovery by category |
| Claude Code Plugin | [claudecodeplugin.com](https://www.claudecodeplugin.com) | Plugin directory |
| Claude Plugins | [claude-plugins.dev](https://claude-plugins.dev) | Community registry |
| Awesome Claude | [awesomeclaude.ai](https://awesomeclaude.ai) | Curated resource directory |
| MCP.so | [mcp.so](https://mcp.so) | MCP server search |
| MCP Server Finder | [mcpserverfinder.com](https://mcpserverfinder.com) | MCP server search engine |
| MCP Awesome | [mcp-awesome.com](https://mcp-awesome.com) | Curated MCP servers |

## GitHub Search Patterns

Effective search queries for finding resources on GitHub:

```
# Plugins
claude-code plugin [your-task]
"claude code" plugin [your-task]
"SKILL.md" [your-task]

# Skills
claude-code skill [your-task]
"claude code" skill [your-task]
path:SKILL.md [your-task]

# MCP Servers
mcp-server [service-name]
"mcp server" [service-name]
"Model Context Protocol" [service-name]

# Hooks
claude-code hook [your-task]
"PreToolUse" OR "PostToolUse" [your-task]

# CLAUDE.md examples
filename:CLAUDE.md [framework-or-language]
```

## npm Search Patterns

```
# On npmjs.com or via npm search
claude-code
claude-code-plugin
claude-code-skill
mcp-server-[service]
@anthropic/
```

## agentskills.in CLI

```bash
# Search for skills
npx agent-skills-cli search [query]

# Install a skill
npx agent-skills-cli install @author/skill-name

# Browse categories
npx agent-skills-cli list
```

## Search Strategy (in order)

1. **Local references** — Check the files in this `references/` directory first
2. **Installed plugins** — Run `/plugin` to see what's already available
3. **Configured marketplaces** — Browse the Discover tab
4. **Web directories** — Check the directories listed above
5. **GitHub search** — Use the search patterns above
6. **npm search** — Search for packages
7. **General web search** — Broader search with `Claude Code plugin/skill/MCP [task]`

## Tips

- Combine sources: a skill from agentskills.in might pair well with an MCP server from mcp.so
- Check the awesome lists in `curated-collections.md` — they're regularly updated and often have the best resources
- When searching GitHub, sort by "Recently updated" to find maintained projects
- Star counts aren't everything — a 50-star skill that does exactly what you need beats a 5K-star one that's tangential
