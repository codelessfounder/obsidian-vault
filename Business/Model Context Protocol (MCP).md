---

---

```markdown
# MCP Summary — What It Is and How It Works

## What is MCP?

**MCP (Model Context Protocol)** is an open protocol that lets AI assistants (like Cursor) connect to external tools and data sources. Instead of the AI only reading your codebase, it can call APIs, run CLI tools, query databases, and use other services on your behalf.

In practice: you configure "MCP servers" (e.g. Supabase, n8n, a browser). Cursor starts those servers and exposes their capabilities as **tools** the AI can use in the chat. When you ask something like "list my Supabase tables," the AI uses the Supabase MCP tool to talk to your project and return real data.

---

## How Cursor Uses MCP

1. **Config file** — You define MCP servers in a JSON config (see Page 2 for locations).
2. **Cursor starts servers** — When you open a project (or Cursor), it runs the configured commands (e.g. `npx @supabase/mcp-server-supabase`).
3. **Tools become available** — Each server exposes tools (e.g. `list_projects`, `execute_sql`, `list_workflows`). The AI can call these when relevant to your question.
4. **No code in your repo** — MCP runs outside your app; your project code doesn’t need to import or run MCP.

---

## Why Use MCP?

- **Live data** — Ask the AI to check your Supabase schema, run a query, or list edge functions and get real results.
- **Automation** — Use n8n MCP to create or update workflows from the editor.
- **Consistency** — Same tools (Supabase, n8n, browser) available across projects without copying code.
- **Security** — Tokens and API keys stay in your MCP config (user or project level), not in the codebase.

---

## Common MCP Servers (examples)

| Server        | Purpose                          | Typical use in Cursor                    |
|---------------|-----------------------------------|------------------------------------------|
| **Supabase**  | Database, auth, edge functions    | List tables, run SQL, apply migrations   |
| **n8n**       | Workflow automation              | Search nodes, validate workflows, deploy |
| **Browser**   | Web automation                   | Test UIs, take screenshots, fill forms    |

Your config can include any MCP-compatible server (official or community).

---

## Summary

- **MCP** = protocol for connecting the AI to external tools and services.
- **Cursor** runs MCP servers defined in your config and gives the AI access to their tools.
- **You** only need to maintain the config (and tokens/keys); the AI uses the tools when needed.

For **where** to put that config and how **global vs local** works, see **MCP Summary — Configuration (Page 2)**.

```

```markdown
# MCP Summary — Configuration (Global vs Local)

## Two Config Locations

| Scope   | Path                          | When it applies                    |
|---------|--------------------------------|------------------------------------|
| **Global** | `~/.cursor/mcp.json`         | Every workspace you open in Cursor |
| **Local**  | `<project>/.cursor/mcp.json`  | Only when that project is open     |

- **Global** = one config for your machine; same MCP servers for all projects.
- **Local** = per-project config; only applies when you have that repo open.

Cursor merges both: if you have a local `mcp.json`, it’s combined with the global one (local can add or override servers for that project).

---

## What Goes in the Config

The file is JSON with a single top-level key, `mcpServers`. Each server has a **key** (e.g. `supabase`, `n8n-mcp`) and a **value** with at least:

- **command** — Executable to run (e.g. `npx`).
- **args** — Arguments (e.g. `["-y", "@supabase/mcp-server-supabase@latest", "--access-token", "<token>"]`).
- **env** (optional) — Environment variables (e.g. `N8N_API_URL`, `N8N_API_KEY`).

Example (structure only; no real secrets):

```json
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": ["-y", "@supabase/mcp-server-supabase@latest", "--access-token", "YOUR_TOKEN"]
    },
    "n8n-mcp": {
      "command": "npx",
      "args": ["n8n-mcp"],
      "env": {
        "N8N_API_URL": "http://localhost:5678",
        "N8N_API_KEY": "YOUR_N8N_JWT"
      }
    }
  }
}
```

Use **global** for shared tools (Supabase, n8n); use **local** when one project needs different URLs/keys or extra servers.

---

## Quick Reference

| Goal                         | Use global config        | Use local config                 |
|-----------------------------|---------------------------|----------------------------------|
| Same tools in every project | ✅                        | —                                |
| Different API key per repo | —                         | ✅ in project `.cursor/mcp.json`  |
| Project-specific MCP only  | —                         | ✅                               |
| One place to edit defaults | ✅ `~/.cursor/mcp.json`   | —                                |

---

## Security Notes

- **Don’t commit secrets** — Keep `mcp.json` out of git if it has tokens (e.g. add to `.gitignore` for project-level config with keys).
- **Global config** — Lives in your user directory (`~/.cursor/`); not in the repo, so not committed with the project.
- **Rotate tokens** — Use Supabase Dashboard → Account → Access Tokens and n8n’s API key settings to rotate if needed.

---

## After Changing Config

Restart Cursor or reload MCP servers so new env vars and servers are picked up. Servers are started when Cursor loads (or when the project is opened, for project-level config).

```



Yachtmaster116622 is Supabase second-brain password
