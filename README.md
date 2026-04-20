---

# brand.md

**Express and protect your brand in the age of the agent.**

An open file format for machine-readable brand identity. Maintained by [Encoded](https://encodedbrands.com).

## What brand.md is

A file format, not a service. A hierarchical set of markdown files that encode a brand's strategy, voice, judgment, boundaries, claims, and representation preferences — readable by every agent in the stack.

Published at `{domain}/.well-known/brand.md`. Same convention as `robots.txt` and `sitemap.xml`.

Not an MCP server. Not a runtime. Not a SaaS. A file tree a brand authors once that every agent reads before it acts.

## Status

Pre-v0.1 working draft. The spec will change. If you're reading this before June 15, 2026, you're early.

## File structure

```text
.well-known/
├── brand.md              # root — identity, positioning, tagline (<3KB)
└── brand/
    ├── voice.md          # tone, register, vocabulary, prefer/avoid
    ├── values.md         # priority-ordered, observable
    ├── visual.md         # color, typography, imagery direction
    ├── boundaries.md     # brand safety — IAB 3.0 + GARM aligned
    ├── claims.md         # legal-reviewed, evidenced
    ├── representation.md # how third-party consumer agents describe the brand
    ├── audiences/       # per-segment voice and positioning
    ├── products/        # per-SKU overrides
    └── campaigns/       # campaign-scoped overrides with sunset dates
```

Root declares what daughters exist. Agents resolve lazily by task — a media-buying agent pulls boundaries and claims, a copy agent pulls voice and audience, a creative-gen agent pulls visual and voice.

## Three consumption surfaces

**Inside** — the brand's own agents (copy, creative, media, compliance). brand.md preserves senior-strategist judgment at machine scale.

**Across** — vendor platforms (Zefr, Canva, Adobe, Meta, DSPs). Their agents read brand.md to make better decisions on the brand's behalf.

**Beyond** — third-party consumer agents (ChatGPT, Claude, Perplexity, Gemini). brand.md is the first time a brand gets input into how consumer agents describe it.

## The formal spec

The full specification — file discovery, resolution model, versioning, taxonomy alignment, localization — is documented as the Brand Context Protocol in [SPEC.md](SPEC.md). brand.md is the file. The Brand Context Protocol defines how it works.

## How to read this repo with an agent

Start at `SPEC.md`, then `spec/hypotheses.md`, then walk `reference/.well-known/brand.md` and its daughter files. The reference implementation is Encoded's own brand.md — we dogfood.

## Get your brand.md

The fastest path: copy the [authoring prompt](https://encodedbrands.com/start), paste it into any capable AI, answer 18 questions, publish the output at your domain. Free forever.

Need senior-strategist quality: [encodedbrands.com/encode](https://encodedbrands.com/encode).

## License

- **Spec:** Creative Commons Attribution 4.0 — [LICENSE-SPEC](LICENSE-SPEC)
- **Code:** MIT — [LICENSE-CODE](LICENSE-CODE)

Same pattern as schema.org, W3C, and MCP.

## Maintained by

[Encoded](https://encodedbrands.com) — a brand consultancy and protocol company.
