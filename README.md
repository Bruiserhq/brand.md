# Tacit — Brand Context Protocol

**Express and protect your brand in the age of the agent.**

An open, machine-readable standard for brand identity in the agentic age.

**Tacit** is the company. **Brand Context Protocol (BCP)** is the open standard Tacit maintains.

## Status

This repo is **private, pre-v0.1 working draft**. Shared with a small number of technical partners by invite ahead of public release. Nothing in this repo should be treated as final.

## What BCP is

BCP encodes a brand's strategy, voice, judgment, boundaries, claims, and representation preferences into a hierarchical file set every agent in the stack can read — internal brand agents, vendor platforms (Zefr, Canva, Adobe, Meta, DSPs), and third-party consumer agents (ChatGPT, Claude, Perplexity, Gemini).

Structurally analogous to AGENTS.md and MCP. Published at `{domain}/.well-known/brand.md`, same convention as `robots.txt` and `sitemap.xml`.

This is **v0.1**. The spec will change. If you're reading this before June 15, 2026, you're early — and your feedback shapes what ships.

## Why this exists

In the next 12 to 36 months, most marketing teams will be staffed with more agents than humans. The tested brand judgment that lives in senior marketers' heads — the "we don't say it that way," the instinct for what's on-brand at the edge, the contextual call on what's acceptable adjacency — has no machine-readable home.

Without one, internal agents produce generic output, vendor platforms make decisions with partial information, and third-party consumer agents describe brands however the model guesses. BCP is the brand-authored source of truth those agents read before they act.

The job is simple, stated in two verbs: **express and protect your brand** across every agent in the stack. BCP is the file format that makes both verbs work at machine scale.

## How to read this repo with an agent

If you're opening this with Claude Code, Cursor, or any agent: start at `SPEC.md`, then `spec/hypotheses.md`, then walk `reference/.well-known/brand.md` and its daughter files. The reference implementation is Tacit's own BCP — we dogfood.

## License (applies on public release)

Dual license.

- **Spec and reference implementation:** Creative Commons Attribution 4.0 (see `LICENSE-SPEC`)
- **Code, validators, SDKs, tooling:** MIT (see `LICENSE-CODE`)

Schema.org and the W3C use this pattern. While the repo is private, license files are included but do not take effect for third parties until the repo goes public.

## v0.1 has

File format, hierarchical resolution model, well-known path convention, reference implementation, JSON Schema stub, draft brand-safety taxonomy alignment to IAB Content Taxonomy 3.0 and GARM Brand Safety Floor + Suitability Framework.

## v0.1 doesn't have yet

Complete formal validator, Living BCP monitoring layer, Forge authoring wizard, native platform integrations. All shipping post-Cannes.

## Feedback wanted

Particularly on:

1. **Brand-safety taxonomy mapping** — where IAB 3.0 and GARM have gaps real systems route around.
2. **Versioning ergonomics** — whether the three-layer model is right for platform caching.
3. **Localization inheritance** — parallel subtrees vs. overrides, which works for editorial workflows.

Open issues or PRs in this repo. Discussion is private to invited collaborators until Cannes.

## Maintained by

Tacit — the company building the standard for brands to express and protect themselves in the age of the agent. Website: pending.
