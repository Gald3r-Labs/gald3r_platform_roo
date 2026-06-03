# gald3r Readiness Report — Roo Code

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full (with one dominant caveat).** Roo Code is one of the most
gald3r-aligned platforms by documented capability — five of the six C.R.A.S.H. mechanisms
land natively (commands, rules, agents, skills, MCP), with only lifecycle hooks missing.
The catch: Roo Code was discontinued on 2026-05-15, so any gald3r investment targets a
frozen/archived tool, not a maintained one.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ✅ | Custom slash commands as markdown in `.roo/commands/` (project) or `~/.roo/commands/` (global); `mode` frontmatter switches mode; agent-invokable via `run_slash_command` | None — gald3r's `@g-*` command set installs as first-class native slash commands |
| **R** | Rules | ✅ | Directory `.roo/rules/` (all modes) + `.roo/rules-{mode}/` (per-mode), recursive alpha-ordered load; reads `.clinerules`; `AGENTS.md` auto-loaded | None — gald3r rules load here as first-class instruction files |
| **A** | Agents | ✅ | Built-in + custom modes in `.roomodes` (slug/roleDefinition/groups/whenToUse); Orchestrator boomerang auto-delegates subtasks | None — gald3r's `g-agnt-*` personas map cleanly to custom modes (no separate `agents/` folder) |
| **S** | Skills | ✅ | `SKILL.md` packages in `.roo/skills/{name}/` and cross-agent `.agents/skills/{name}/`; auto-discovered, progressive-disclosure on-demand load | None — gald3r `g-skl-*` skills install natively; feature is recent (docs dated 2026-05-15) |
| **H** | Hooks | ❌ | — | No native lifecycle/event hooks; gald3r's `g-hk-*` session-start / pre-tool / pre-commit wiring has no auto-fire host (only community proposals, never shipped) |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** First-class Model Context Protocol support — committable
`.roo/mcp.json` (project, auto-detected) and global `mcp_settings.json` (project wins on
collision); `use_mcp_tool` / `access_mcp_resource` over STDIO and SSE/HTTP. gald3r's MCP
backend connects natively.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| `run_slash_command` tool (agent chains `/init`, `/review`, etc.) | ✅ present | Lets gald3r `@g-*` commands compose into model-driven workflows |
| Orchestrator / boomerang sub-task delegation | ✅ present | Nearest analog to gald3r pipelines — model-driven, not a hook system |
| Experimental Custom Tools (TS/JS, called like `read_file()`) | ⚙️ needs customization | Model-invoked tools, not deterministic hooks; could host bespoke gald3r actions |
| `.rooignore` access control · settings Import/Export | ✅ present | Scopes agent file access and shares config; no gald3r work required |

## The honest ceiling

gald3r adapts to this platform the way any third-party layer must — by mapping our commands, rules, agents, skills, and hooks onto whatever extension points the platform happens to expose. Where those points exist, the fit is clean. Where they don't, adaptation can only *approximate* the real thing — a stand-in that covers the common case but not the edges.

That isn't a knock on the platform. It's the ceiling of bolting *any* framework onto a surface that was never built to host it.

Full functional parity isn't something we can reach from the outside. It lives in the native build — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where commands, rules, agents, skills, and hooks aren't *adapted* to the platform, they *are* the platform.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
