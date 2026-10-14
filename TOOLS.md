# Kairom MCP tools

Generated from the live tool registry (the same list `tools/list` returns at https://kairom.world/mcp). All 21 tools are read-only.

### Systems and dependencies

| Tool | Scope | What it answers |
|---|---|---|
| `list_layers` | read | The systems Kairom models, as data layers: energy grid, fuel, telecom and digital, cyber, road and rail/ports, trade and supply chains, economy by sector, people and crowd events, calendars, health surveillance, regulation, built… |
| `site_dependencies` | read | What a site depends on, across every system layer: the substation that feeds it and its redundancy, access roads and alternatives, nearest port/rail, telecom redundancy, fuel supply, supplier countries and chokepoints, sector exposure of… |
| `layer_metric` | read | Current value of one system-layer metric for a place, a business sector or a country: e.g. electricity_price_eur_mwh or grid_stress_index (country), fuel_price_eur_l near a site, road_access_closed / road_incident_near for a site,… |
| `layer_map_summary` | read | Compact summary of one system layer's map features in an area (counts by type and category, a few sample features with rounded positions, legend), never the raw GeoJSON: e.g. substations and lines around a site (energy_grid), road… |

### Your projects (and the company map)

| Tool | Scope | What it answers |
|---|---|---|
| `list_projects` | projects:read | The projects of THIS key's workspace (never another workspace): id, name, type, country, number of sites (located, with a profile), what it watches |
| `get_system_map` | projects:read | Its cross-system map: the chains that can HURT it (risks) and the ones that can HELP it (opportunities), each as trigger -> systems -> sector -> the company (e.g. a port strike -> late inputs -> lost output; a price drop in an input ->… |
| `project_summary` | projects:read | What Kairom found for one project, in 2-4 plain sentences plus up to 3 key facts (chips): the top cross-system risk and opportunity chain, the single points of failure several sites share, a watch target's forecast and what is live now |
| `recent_changes` | read | What changed recently around a project or a point: the workspace's own live events for the project (open incidents, rules that fired, changes in its forecasts), road incidents and closures near its sites from the live traffic feeds, and,… |
| `get_project` | projects:read | One project of this key's workspace: type, country, its sites (label, position rounded to about 100 m, what the owner told us: backup power hours, inventory days, staff per shift, value per day, critical routes, supplier countries and lead… |
| `project_dependencies` | projects:read | Dependencies of every located site of a project (up to max_sites, default 5): per site the systems it depends on and its single points of failure, plus what several sites share (e.g. the same substation, port, road corridor or supplier… |

### Watch targets

| Tool | Scope | What it answers |
|---|---|---|
| `list_watch_sources` | read | The signals a watch target can be explained by: each source's id, label, system layer, unit, refresh, scope and whether it has history (power prices, fuel, road incidents, port activity, supplier news, crowd events, calendars, health… |
| `get_watch` | projects:read | The watch targets of one project of this key's workspace: for each target (e.g. daily orders, deliveries late, staff absence, energy cost) the current value, recent series, the forecast band (p10/p50/p90 over its horizon), the drivers that… |

### What-if simulations

| Tool | Scope | What it answers |
|---|---|---|
| `list_simulations` | read | What-if simulations |
| `run_simulation` | simulate | Run one simulation and get a compact answer: headline summary with p10/p50/p90 ranges, key moments in time, peaks of the main series, the loss split by driver where the simulator gives one, the site's own view when a project site has a… |

### Reference

| Tool | Scope | What it answers |
|---|---|---|
| `explain_view` | read | Explain one Kairom view (a project, the map, an incident, a simulation result...) from a compact context you pass: a short summary of what matters for decisions, systems, money and people, through the Kairom assistant |

### Natural hazards (one input among many)

| Tool | Scope | What it answers |
|---|---|---|
| `impact_outlook` | read | Consequences of a hazard in a European region, in one answer: money (economic loss EUR m, p10/p50/p90, split direct / business interruption / indirect), people (excess deaths, hospital pressure, lost working hours) and the likely… |
| `hazard_outlook` | read | Probabilistic hazard outlook for a point in Europe, from the Kairom live engine (51-member ECMWF ensemble plus GloFAS river, CMEMS sea level/waves, CAMS air, EFFIS/FIRMS fire, EDO drought, and `flash_flood`: ensemble rain vs… |
| `site_risk_report` | read | Site risk report for a house or plot: river, coastal and surface flood (with the legal hydraulic zone in Spain), wildfire, heat and other hazards, each with a verdict, Monte Carlo uncertainty ranges split by source, ranked questions that… |
| `engine_track_record` | read | Measured reliability of the Kairom Europe engine: verification scores of its forecasts against observed events (MeteoAlarm warnings, Copernicus EMS flood activations, FIRMS fire detections, station heat/cold) |

### Reference

| Tool | Scope | What it answers |
|---|---|---|
| `who_can_act` | read | Who is legally able or obliged to act (owner, legal basis, who must agree) on a hazard in a European country, from Kairom's decision catalogue (src/europe/decisions): per action the owner (authority or operator), authority level, who must… |
| `sources_and_licences` | read | The data sources behind Kairom and the attribution each requires (ECMWF open data, Copernicus EMS/CAMS/CMEMS/GloFAS/EFAS, EFFIS, NASA FIRMS, MeteoAlarm, national geocoders and others) with their licences |
