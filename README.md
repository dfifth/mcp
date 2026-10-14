# Kairom MCP server

Kairom is a complex-systems data, simulation and decision engine for Europe. Ask what a site or a company depends on
(power, fuel, telecom, cyber, roads, rail and ports, suppliers, economy by sector, people and events, health, regulation)
and run what-if shocks through those systems: strikes, supplier failure, power or telecom outages, cyber incidents, price
and regulation shocks, crowd events, and natural hazards as one input among many.

This repository holds the documentation and the registry metadata of the **remote** Kairom MCP server. The server itself is
hosted; there is nothing to install or run.

- **Endpoint:** `https://kairom.world/mcp` (MCP Streamable HTTP, OAuth 2.1 with PKCE)
- **Tools:** 21, all read-only (list in [TOOLS.md](TOOLS.md))
- **API reference:** https://kairom.world/docs (REST: `/api/tools/*`, `/api/v2`, OpenAPI at https://kairom.world/openapi-tools.json)
- **Public demo** (no sign-up, read-only, three fictional companies): https://kairom.world/app/i#OIMI983P1F34O8tFtwct7Ah2MbxHwpwxKppUYakWlKo

## Connect

**Claude** (Free, Pro, Max): Settings → Connectors → *Add custom connector* → `https://kairom.world/mcp` → Add → Connect.
On the Kairom page that opens, paste the demo link above (or your own invite link). One-click:
[Add Kairom to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Kairom&connectorUrl=https%3A%2F%2Fkairom.world%2Fmcp).
Team and Enterprise: an Owner adds it under Organization settings → Connectors.

**ChatGPT** (Plus, Pro, Business, Enterprise): Settings → Apps & Connectors → Advanced settings → turn on *Developer mode* →
*Create* → name "Kairom", URL `https://kairom.world/mcp` → sign in with the demo link.

**Claude Code:**
```
claude mcp add --transport http kairom https://kairom.world/mcp
```

**Any other MCP client** that supports remote servers with OAuth (Cursor, VS Code, Cline, ...): add a remote/HTTP server
with the URL `https://kairom.world/mcp`; the client opens the Kairom sign-in page. See [llms-install.md](llms-install.md).

**API key instead of OAuth:** workspace keys (`Authorization: Bearer kw_...`) are issued from the app's API keys page
for pilot workspaces.

## What to ask

1. What does the plant at Pol. Malpica, Zaragoza depend on, and where are its single points of failure?
2. Run a 5-day strike at the Port of Valencia and show what is hit first.
3. For my company project, which cross-system chains can hurt us and which can help us? (`get_system_map`)
4. What changed this week around my sites? (`recent_changes`)
5. What is the electricity price in Spain today against the last 7 days?

## How to read the answers

Every result carries `status` (validated / screening / experimental), `as_of`, `sources` and `caveats`, and ranges
(p10-p90 or 90 %) where the engine has them. Most layers are *screening* today: orders of magnitude, not validated
forecasts. Simulation results are regional economic output (GVA) over the run, not a company's own accounts. Decision support
only: no tool takes an action, and official warnings and operators' notices take precedence.

## Limits and privacy

- Rate limits per key or connection (HTTP 429 with `Retry-After`); the demo link has a per-visitor limit.
- Each key or connection only ever reads its own workspace. The demo link cannot edit anything or use the AI layer.
- Logs keep the tool name, a key id prefix and positions rounded to about 1 km; never request bodies, addresses or tokens.
- Data comes from open sources with attribution: https://kairom.world/api/v1/attribution

## Contact

Pau, Kairom (Barcelona) · pau@kairom.world · https://kairom.world · Legal and privacy: https://kairom.world/legal

Documentation in this repository: CC BY 4.0.
