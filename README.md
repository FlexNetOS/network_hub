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

## Project Referances: Network tools for Native Rust Crates

Add the following reference | Run deep-research on these sources |  if possible - extract crates and wire in |

[n0-computer/iroh: IP addresses break, dial keys instead. Modular networking stack in Rust.](https://github.com/n0-computer/iroh)
[n0-computer/noq: noq, a QUIC implementation in Rust](https://github.com/n0-computer/noq)
[n0-computer/dumbpipe: Unix pipes between devices](https://github.com/n0-computer/dumbpipe)
[Dicklesworthstone/franken_networkx: Memory-safe clean-room Rust reimplementation of NetworkX with deterministic graph semantics, differential conformance, and RaptorQ-backed durability.](https://github.com/Dicklesworthstone/franken_networkx) 
[n0-computer/net-tools: Cross platform, networking utilties in Rust](https://github.com/n0-computer/net-tools)
[stalwart/README.md at main · stalwartlabs/stalwart](https://github.com/stalwartlabs/stalwart/blob/main/README.md)
[Your Stars](https://github.com/drdave-flexnetos?language=rust&tab=stars)
[unionlabs/union: The trust-minimized, zero-knowledge bridging protocol, designed for censorship resistance, extremely high security, and usage in decentralized finance.](https://github.com/unionlabs/union)
[vercel-labs/agent-browser: Browser automation CLI for AI agents](https://github.com/vercel-labs/agent-browser)
[iii-hq/iii: Effortlessly compose, extend, and observe every service in real-time for the first time ever.](https://github.com/iii-hq/iii)
[bee-san/RustScan: 🤖 The Modern Port Scanner 🤖](https://github.com/bee-san/RustScan)
[cloudflare/pingora: A library for building fast, reliable and evolvable network services.](https://github.com/cloudflare/pingora)
[h4ckf0r0day/obscura: The headless browser for AI agents and web scraping](https://github.com/h4ckf0r0day/obscura)
[hyperium/hyper: An HTTP library for Rust](https://github.com/hyperium/hyper)
[claw-code/rust/crates at main · ultraworkers/claw-code](https://github.com/ultraworkers/claw-code/tree/main/rust/crates)
[rustdesk/rustdesk: An open-source remote desktop application designed for self-hosting, as an alternative to TeamViewer.](https://github.com/rustdesk/rustdesk)
[rustdesk/rustdesk-server-demo: A working demo of RustDesk server implementation](https://github.com/rustdesk/rustdesk-server-demo)
[RustNetworkStack/src at main · jbush001/RustNetworkStack](https://github.com/jbush001/RustNetworkStack/tree/main/src)
[domcyrus/rustnet: Per-process network monitoring for your terminal with deep packet inspection. Cross-platform, sandboxed.](https://github.com/domcyrus/rustnet)
[fastrevmd-lab/rustnetconf: A Rust network automation platform: async NETCONF client library, YANG code generation, vendor profiles, connection pooling, and a Terraform-like CLI for declarative network config management.](https://github.com/fastrevmd-lab/rustnetconf)
[rust-swifties/net-tools-rs: Rust implementation of net-tools](https://github.com/rust-swifties/net-tools-rs)
[sparesparrow/rust-network-mgr: Linux based network management, packet routing and LAN peers IP monitoring service written in Rust.](https://github.com/sparesparrow/rust-network-mgr)
[network-engineering · GitHub Topics](https://github.com/topics/network-engineering?l=rust)
[demohiiiii/rauto: Automate network device configurations with ease. rauto combines minijinja for dynamic command generation and rneter for robust SSH connections (Cisco, Huawei, Juniper, etc.). Supports dry-runs, JSON variables, and custom device profiles.](https://github.com/demohiiiii/rauto)
[casablanque-code/ospf-postmortem: [Network Forensics Series] A browser-based OSPF analyzer for network engineers. Drop a PCAP file — get a structured event timeline, full FSM reconstruction, root cause analysis with causal chains, topology graph, and zero data leaving your machine.](https://github.com/casablanque-code/ospf-postmortem)
[bigdatacloudapi/bigdatacloud-rust: Official Rust SDK for BigDataCloud APIs — IP Geolocation, Reverse Geocoding, Phone & Email Verification, Network Engineering](https://github.com/bigdatacloudapi/bigdatacloud-rust)
[scanopy/scanopy: Network diagrams that update themselves](https://github.com/scanopy/scanopy)
[GyulyVGC/sniffnet: Comfortably monitor your Internet traffic 🕵️‍♂️](https://github.com/GyulyVGC/sniffnet)
[FoxIO-LLC/ja4: JA4+ is a suite of network fingerprinting standards](https://github.com/FoxIO-LLC/ja4)
[Chleba/netscanner: Terminal Network scanner & diagnostic tool with modern TUI](https://github.com/Chleba/netscanner)
[DavidHavoc/ayaFlow: A high-performance, eBPF-based network traffic analyzer written in Rust.](https://github.com/DavidHavoc/ayaFlow)
[biandratti/huginn-net: Multi-protocol passive fingerprinting library: TCP/HTTP (p0f-style) + TLS (JA4-style) analysis in Rust](https://github.com/biandratti/huginn-net)
[CramBL/mdns-scanner: Scan a network and create a list of IPs and associated hostnames, including mDNS hostnames and other aliases.](https://github.com/CramBL/mdns-scanner)
[johanhelsing/matchbox: Painless peer-to-peer WebRTC networking for rust wasm (and native!)](https://github.com/johanhelsing/matchbox)
[n0-computer/net-tools: Cross platform, networking utilties in Rust](https://github.com/n0-computer/net-tools)
[stalwartlabs/stalwart: All-in-one Mail & Collaboration server. Secure, scalable and fluent in every protocol (IMAP, JMAP, SMTP, CalDAV, CardDAV, WebDAV).](https://github.com/stalwartlabs/stalwart)
[unionlabs/union: The trust-minimized, zero-knowledge bridging protocol, designed for censorship resistance, extremely high security, and usage in decentralized finance.](https://github.com/unionlabs/union)
[vercel-labs/agent-browser: Browser automation CLI for AI agents](https://github.com/vercel-labs/agent-browser)
[iii-hq/iii: Effortlessly compose, extend, and observe every service in real-time for the first time ever.](https://github.com/iii-hq/iii)
[bee-san/RustScan: 🤖 The Modern Port Scanner 🤖](https://github.com/bee-san/RustScan)
[cloudflare/pingora: A library for building fast, reliable and evolvable network services.](https://github.com/cloudflare/pingora)
[h4ckf0r0day/obscura: The headless browser for AI agents and web scraping](https://github.com/h4ckf0r0day/obscura)
[hyperium/hyper: An HTTP library for Rust](https://github.com/hyperium/hyper)
[claw-code/rust/crates at main · ultraworkers/claw-code](https://github.com/ultraworkers/claw-code/tree/main/rust/crates)
[rustdesk/rustdesk: An open-source remote desktop application designed for self-hosting, as an alternative to TeamViewer.](https://github.com/rustdesk/rustdesk)
[rustdesk/rustdesk-server-demo: A working demo of RustDesk server implementation](https://github.com/rustdesk/rustdesk-server-demo)
[RustNetworkStack/src at main · jbush001/RustNetworkStack](https://github.com/jbush001/RustNetworkStack/tree/main/src)
[domcyrus/rustnet: Per-process network monitoring for your terminal with deep packet inspection. Cross-platform, sandboxed.](https://github.com/domcyrus/rustnet)
[fastrevmd-lab/rustnetconf: A Rust network automation platform: async NETCONF client library, YANG code generation, vendor profiles, connection pooling, and a Terraform-like CLI for declarative network config management.](https://github.com/fastrevmd-lab/rustnetconf)
[rust-swifties/net-tools-rs: Rust implementation of net-tools](https://github.com/rust-swifties/net-tools-rs)
[sparesparrow/rust-network-mgr: Linux based network management, packet routing and LAN peers IP monitoring service written in Rust.](https://github.com/sparesparrow/rust-network-mgr)
[network-engineering · GitHub Topics](https://github.com/topics/network-engineering?l=rust)
[demohiiiii/rauto: Automate network device configurations with ease. rauto combines minijinja for dynamic command generation and rneter for robust SSH connections (Cisco, Huawei, Juniper, etc.). Supports dry-runs, JSON variables, and custom device profiles.](https://github.com/demohiiiii/rauto)
[casablanque-code/ospf-postmortem: [Network Forensics Series] A browser-based OSPF analyzer for network engineers. Drop a PCAP file — get a structured event timeline, full FSM reconstruction, root cause analysis with causal chains, topology graph, and zero data leaving your machine.](https://github.com/casablanque-code/ospf-postmortem)
[bigdatacloudapi/bigdatacloud-rust: Official Rust SDK for BigDataCloud APIs — IP Geolocation, Reverse Geocoding, Phone & Email Verification, Network Engineering](https://github.com/bigdatacloudapi/bigdatacloud-rust)
[scanopy/scanopy: Network diagrams that update themselves](https://github.com/scanopy/scanopy)
[GyulyVGC/sniffnet: Comfortably monitor your Internet traffic 🕵️‍♂️](https://github.com/GyulyVGC/sniffnet)
[FoxIO-LLC/ja4: JA4+ is a suite of network fingerprinting standards](https://github.com/FoxIO-LLC/ja4)
[Chleba/netscanner: Terminal Network scanner & diagnostic tool with modern TUI](https://github.com/Chleba/netscanner)
[DavidHavoc/ayaFlow: A high-performance, eBPF-based network traffic analyzer written in Rust.](https://github.com/DavidHavoc/ayaFlow)
[biandratti/huginn-net: Multi-protocol passive fingerprinting library: TCP/HTTP (p0f-style) + TLS (JA4-style) analysis in Rust](https://github.com/biandratti/huginn-net)
[CramBL/mdns-scanner: Scan a network and create a list of IPs and associated hostnames, including mDNS hostnames and other aliases.](https://github.com/CramBL/mdns-scanner)
[johanhelsing/matchbox: Painless peer-to-peer WebRTC networking for rust wasm (and native!)](https://github.com/johanhelsing/matchbox)
[n0-computer/net-tools: Cross platform, networking utilties in Rust](https://github.com/n0-computer/net-tools)
