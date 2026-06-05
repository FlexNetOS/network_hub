# network_hub

**Catalog of network configs and service topology used across the FlexNetOS meta workspace.**

A FlexNetOS hub: `registry.json` is the single source of truth, `scripts/validate.py`
keeps it consistent (CI-enforced), and this README mirrors it. Follows the
[Hub Standard](https://github.com/FlexNetOS/template_hub/blob/master/docs/hub-standard.md).

## Scope

In scope: Network configs and topology — named hosts/services, ports, tunnels,
reverse-proxy/ingress configs, and connectivity between workspace services.

Out of scope: secrets and credentials → [`flexnetos_secrets`](https://github.com/FlexNetOS/flexnetos_secrets).

## Catalog

_No entries yet — this hub is at v0.1.0 (foundation set, population pending)._

| Endpoint | Protocol | Category | Status | Doc |
|----------|----------|----------|--------|-----|
| _(none)_ | | | | |

## Entry shape

Each `networks[]` entry in [`registry.json`](registry.json) looks like:

```json
{
  "id": "n8n-instance",
  "displayName": "n8n instance endpoint",
  "category": "service-endpoint",
  "status": "experimental",
  "summary": "HTTP endpoint for the workspace n8n instance consumed by flow_hub flows and the n8n-mcp server.",
  "tags": ["n8n", "endpoint"],
  "protocol": "https",
  "host": "your-n8n-instance.com",
  "port": 443,
  "configPath": "snippets/n8n-instance.caddy",
  "reachableFrom": "public",
  "auth": "api-key",
  "doc": "entries/n8n-instance.md",
  "snippet": "snippets/n8n-instance.env"
}
```

Full field reference: [`registry.schema.json`](registry.schema.json).

## Adding an endpoint

Add an entry to `registry.json`, create `entries/<id>.md` (and a `snippets/<id>.*`
config fragment if useful), add a Catalog row, then run `python3 scripts/validate.py`.
See the [Hub Standard](https://github.com/FlexNetOS/template_hub/blob/master/docs/hub-standard.md).
