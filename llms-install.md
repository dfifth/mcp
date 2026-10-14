# Installing the Kairom MCP server (for AI assistants)

Kairom is a **remote** MCP server. Do not clone, build or run anything.

1. Add a remote MCP server named `kairom` with transport **Streamable HTTP** and URL `https://kairom.world/mcp`.
   - Claude Code: `claude mcp add --transport http kairom https://kairom.world/mcp`
   - JSON-config clients (Cline, Cursor, VS Code and similar):
     ```json
     { "mcpServers": { "kairom": { "type": "streamableHttp", "url": "https://kairom.world/mcp" } } }
     ```
     (Use the field names your client expects for a remote HTTP server: `type: "http"` in some clients.)
2. The first call answers 401 with an OAuth challenge. Let the client run the OAuth 2.1 flow (dynamic client
   registration, PKCE S256). The user signs in on the Kairom page with the public demo link printed in README.md or with
   their own invite link, ticks the permissions and approves.
3. Check the connection by calling `list_layers`; then try `site_dependencies` with `lat`/`lon` of a European site.

No API key or environment variable is needed for the OAuth route. If the user has a workspace key (`kw_...`), the client
can send it instead as `Authorization: Bearer <key>`.
