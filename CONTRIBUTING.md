# Contributing to Encoded / BCP

This spec is pre-v1.0 and evolving. We want real-world feedback from:

- Vendor platforms (brand-safety, creative-generation, ad-tech)
- Brands actually publishing a BCP
- Agent platform builders
- Protocol designers

## How to contribute

**Open an issue** if:
- A field in the spec doesn't cover your real use case
- IAB 3.0 / GARM taxonomy mapping has a gap you work around
- A section is unclear or contradictory
- You think a working hypothesis in `spec/hypotheses.md` is wrong

**Open a pull request** if:
- You have a concrete proposal with rationale
- You're adding to the reference implementation with a generalizable improvement
- You're fixing a typo or a bug in the schema

## Governance

v0.1 through v1.0: benevolent dictator model. Encoded maintains, accepts issues and PRs, and publishes a decision log for spec changes.

Post-v1.0: transition to a published governance model with external spec contributors. Exact structure TBD and will be proposed publicly before v1.0.

## What's in / out of scope

**In scope for v0.1 issues and PRs:**
- Spec clarity and correctness
- Taxonomy alignment and extensions
- Versioning and caching semantics
- Reference implementation quality
- JSON Schema coverage

**Out of scope (for now):**
- Building a formal validator (v0.2)
- Living BCP monitoring layer (v0.2+)
- Forge authoring wizard (separate repo, post-Cannes)
- Native platform integrations (bilateral work with partners)

## Code of conduct

Be direct. Be kind. Disagree with the argument, not the person.
