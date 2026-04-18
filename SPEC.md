# Brand Context Protocol — Specification v0.1

*Status: draft. Shipping with Cannes Lions 2026. Breaking changes possible until v1.0.*

## 1. Overview

BCP is a hierarchical file set authored by or on behalf of a brand, published at a well-known location, and read by agents that need to understand brand intent.

The root file (`brand.md`) is always loaded. Daughter files are resolved lazily based on the consuming agent's task.

Stated in two verbs, BCP helps brands **express and protect** themselves across every agent in the stack: the authoring layer (how a brand expresses intent) and the consumption layer (how agents read that intent and act to protect it).

## 2. Publishing a BCP

### 2.1 Canonical location

BCP files are published at `{domain}/.well-known/brand.md` (the root) with daughters at `{domain}/.well-known/brand/{file}.md` and `{domain}/.well-known/brand/{subdirectory}/{file}.md`.

Mirrors the well-known URI conventions of `robots.txt`, `sitemap.xml`, and `security.txt` (RFC 8615).

### 2.2 Source of truth

Brands maintain BCP files in a Git repository they own. GitHub, GitLab, or any Git host is equivalent. The repository's `main` branch is the source of truth; the `/.well-known/` deployment is the consumed artifact.

### 2.3 Distribution

Three valid distribution models:

1. **Direct serving.** The brand serves `/.well-known/brand.md` and daughters from their own domain.
2. **Fork-the-template.** The brand forks this repository, edits their values, and serves from their own infrastructure.
3. **Hosted.** A third party hosts the file tree on the brand's behalf behind a CDN proxy.

All three produce the same consumable artifact at the same URL pattern.

## 3. File format

### 3.1 Markdown with YAML frontmatter

Every BCP file is valid Markdown with YAML frontmatter. Frontmatter holds metadata. Body holds prose and fenced YAML blocks for structured content.

### 3.2 Structured fields

Fields that agents parse programmatically (boundaries, claims, safety signals, adjacency rules) live in fenced YAML blocks. Fields humans read (voice guidance, values, narrative framing) live in prose.

### 3.3 Validation

A JSON Schema describing frontmatter and structured-block requirements is published at `spec/brand-context.schema.json`. v0.1 covers required frontmatter fields and canonical structured-block shapes. Full schema coverage ships with v0.2.

## 4. Hierarchical resolution

### 4.1 Root declares daughters

The root `brand.md` includes a `daughter_files` section listing which daughters exist and where.

### 4.2 Canonical fallback paths

If the root omits the registry, consuming agents MAY attempt canonical paths: `/.well-known/brand/voice.md`, `/.well-known/brand/values.md`, `/.well-known/brand/boundaries.md`, `/.well-known/brand/claims.md`, `/.well-known/brand/representation.md`, `/.well-known/brand/visual.md`, `/.well-known/brand/audiences/{segment}.md`, `/.well-known/brand/products/{sku}.md`, `/.well-known/brand/campaigns/{name}.md`.

### 4.3 Lazy resolution

Agents load only what their task requires. Root is always loaded (target size: under 3KB).

- A copy-generation agent pulls `voice.md`, `values.md`, and one audience file.
- A media-buying agent pulls `boundaries.md` and `claims.md`.
- A creative-generation agent pulls `voice.md` and `visual.md`.
- A consumer-surface agent pulls `representation.md`.

## 5. Versioning

Three-layer versioning model.

1. **`bcp_version`** — spec compliance level. Incremented by spec maintainers.
2. **`tree_version`** — semver on the brand's own published BCP. Brand controls this.
3. **`last_updated`** — ISO 8601 date on each file. Updated per file on edit.

Each file also carries an optional `revision` hash suitable for HTTP ETag-based caching.

## 6. Brand-safety taxonomy

v0.1 aligns `boundaries.md` adjacency signals to:

- **IAB Content Taxonomy 3.0** for category structure.
- **GARM Brand Safety Floor + Suitability Framework** for suitability tiers (Floor, High, Medium, Low risk).

Where the two diverge, follow GARM for suitability tier assignment and IAB for category labeling. Brand-specific fields not in either taxonomy live under a namespaced `extensions:` block.

**Open question (v0.1 → v0.2):** which adjacency edge cases real brand-safety systems route around daily that belong in the standard rather than in extensions. Feedback wanted.

## 7. Representation

`representation.md` specifies how third-party consumer agents should describe the brand when asked. Structure:

- A prose `preferred_framing` paragraph (soft ceiling ~120 words) agents paraphrase for open-ended queries.
- Structured fields: `describe_as`, `do_not_describe_as`, `competitive_frame`, `honest_trade_offs`, `never_say`.

## 8. Localization

Parallel subtrees per locale with inheritance fallback. `/.well-known/brand/ja/voice.md` overrides `/.well-known/brand/voice.md`; missing locale files inherit from default. Root declares `supported_locales` and `default_locale`.

## 9. Open questions in v0.1

1. Taxonomy completeness (Section 6).
2. Whether `products/{sku}.md` should be a standardized daughter type.
3. Whether `campaigns/{name}.md` needs sunset-date semantics in the spec.
4. Signed BCPs for high-assurance use cases.
5. Private BCPs served through authenticated MCP server endpoints — out of scope for v0.1, planned for v0.2.

All tracked as GitHub Issues.
