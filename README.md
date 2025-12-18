# Semantic Frame Pattern (SFP)

Semantic Frame Pattern (SFP) is a methodology for composing small, human-legible semantic facets into compact frames that describe resources without prescribing a particular domain or platform. It focuses on defining how to structure and combine facets so that implementations can build concise, composable vocabularies suited for prompt-scale and machine-assisted interpretation.

SFP is not a taxonomy, ontology, knowledge graph, search keyword system, or product. It does not ship any tag lists or domain-specific vocabularies; it only describes a pattern that implementations can adopt while remaining interoperable.

**Design goals**
- Bounded core vocabularies with explicit size targets
- Composable facets that assemble into frames
- Human-legible identifiers and definitions
- Prompt-scale payloads that stay compact
- Stable definitions with explicit drift controls
- Optional depth through extensions without breaking cores
- Implementation-agnostic and tooling-neutral

See [SPEC.md](SPEC.md) for the normative specification.

This repository uses Semantic Versioning and RFC 2119 keywords.
