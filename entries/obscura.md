# Obscura (governed web-egress engine)

**Category:** service-endpoint · **Status:** beta · **Protocol:** ws (CDP) · also http (MCP) · **Reachable from:** local · **Auth:** none · **Upstream:** `https://github.com/h4ckf0r0day/obscura`

A **Rust headless-browser engine for AI agents and web scraping** — an 8-crate workspace with a
real V8 runtime, a CDP server, an MCP server, a Puppeteer/Playwright drop-in, and anti-detect /
stealth. In the FlexNetOS estate it is the **network plane's web-egress engine**: the thing that
actually drives a real browser out to the web on behalf of agents.

## Role in the network plane

obscura is the **engine behind the egress**, not the policy. Its live web egress is **governed by
[lane](https://github.com/FlexNetOS/lane)** per **ADR-0001**: lane pins obscura's egress through its
proxy + CA via the `lane web` seam, so that browser traffic flows through the governed, OS-trusted
HTTPS path rather than straight out the host. lane is the network plane's governance/proxy layer;
obscura is the web-egress engine lane governs.

This is why it lives in `network_hub` as a `service-endpoint`: it exposes service endpoints (MCP +
CDP) on the network plane and is the engine the lane proxy fronts — not a proxy itself, and not a
plain CLI tool.

> **Status note:** `beta`. The engine is real and was freshly integrated and brought green in
> Phase A1, but **live obscura wiring is still gated on the lane↔obscura seam** (ADR-0001) — i.e.
> the governed-egress path is the contracted shape, not yet a flipped-on default.

## Surfaces

- **MCP server** — `obscura mcp` (stdio), or `obscura mcp --http --port 3000` for an HTTP endpoint.
  Tools include `browser_navigate`, `browser_fetch`, and the rest of the browser tool set — the
  Puppeteer/Playwright-shaped surface agents call.
- **CDP server** — `obscura serve --port 9222` exposes a Chrome DevTools Protocol endpoint over
  **ws**, the drop-in target for existing Puppeteer/Playwright clients.
- **CLI** — `obscura fetch <url>` for one-shot fetches.

The catalog records `protocol: ws` as the primary (the CDP endpoint); the MCP endpoint is reachable
over `http` when run with `--http`.

## Build notes

- It's a **fork** of upstream `h4ckf0r0day/obscura` (188 commits upstream). Brought green and given
  custom-CA trust in Phase A1 (FlexNetOS/obscura PRs #2, #3) — the custom-CA trust is what lets the
  lane CA terminate obscura's HTTPS for governed egress.
- Build with `--no-default-features` for the lean path.
- The **stealth / anti-detect** features need `cmake` available at build time.

## Links

- Repo: `git@github.com:FlexNetOS/obscura.git`
- Upstream: `https://github.com/h4ckf0r0day/obscura`
- Governance seam: lane (`lane web`, ADR-0001)
