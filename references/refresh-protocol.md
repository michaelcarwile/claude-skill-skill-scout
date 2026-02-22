# Reference Database Refresh Protocol
> Last updated: 2026-02-22

How to keep the Skill Scout reference database current.

## When to Refresh

- Every ~5 sessions, or when starting a new project type
- When you search for something and the local database has no results
- When the user asks about the database freshness
- When you discover new resources during a session

## Refresh Search Queries

Run these web searches to find new resources:

### Skills & Plugins
```
Claude Code plugins 2026
Claude Code skills new
site:github.com claude-code plugin created:>2026-01-01
site:github.com "SKILL.md" created:>2026-01-01
```

### MCP Servers
```
new MCP servers 2026
site:github.com mcp-server created:>2026-01-01
```

### Awesome Lists (check for updates)
```
site:github.com hesreallyhim/awesome-claude-code
site:github.com punkpeye/awesome-mcp-servers
site:github.com travisvn/awesome-claude-skills
```

### Directories
```
site:agentskills.in new
site:claudecodeplugins.dev
site:mcp.so new
```

## How to Add New Entries

### Format

Use the consistent table format from the existing files:

```markdown
| Resource Name | [source/URL](https://...) | Brief description of what it does | stars / active |
```

### Where to Add

| Type | File |
|------|------|
| Awesome list or mega-repo | `curated-collections.md` |
| Individual skill or plugin | `skills-and-plugins.md` — under the appropriate category |
| MCP server | `mcp-servers.md` — under the appropriate domain |
| CLAUDE.md example or config | `claude-md-and-configs.md` |
| New search directory or registry | `registries-and-directories.md` |

### Steps

1. Read the target reference file
2. Find the appropriate section (or create a new one if needed)
3. Add the entry in the table format
4. Update the `> Last updated: YYYY-MM-DD` date at the top of the file
5. Update the date in this file too

## How to Update the "Last Updated" Date

Each reference file has a date on line 2:
```markdown
> Last updated: YYYY-MM-DD
```

Update this to today's date whenever you modify the file.

## Quick-Add During a Session

If you discover a useful resource while helping the user:

1. Note it to the user: "I found [resource] — adding it to the Skill Scout reference database."
2. Read the appropriate reference file
3. Add the entry
4. Update the date
5. Continue with the original task

This keeps the database growing organically as you work.
