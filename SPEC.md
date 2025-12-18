# Semantic Frame Pattern Specification
Version: 0.1.0
Status: Draft

## 1. Normative language
The key words MUST, SHOULD, and MAY are to be interpreted as described in RFC 2119 for all normative statements in this document.

## 2. Scope
Semantic Frame Pattern (SFP) defines how to design a frame-based tagging system composed of facets and tags. It does not prescribe any specific tags, domains, or implementation technologies. Implementations claim compatibility by following this pattern while supplying their own domain-appropriate vocabularies.

## 3. Definitions
- **Frame**: A composed set of facet selections that together describe a resource.
- **Facet**: A bounded category of related tags within a frame (e.g., Domain, Object, Action). Each facet constrains how many tags may be chosen from it.
- **Tag**: A human-legible identifier within a facet that carries a short, unambiguous definition.
- **Legend**: A published reference describing the facets, tags, rules, and policies for a specific SFP implementation version.
- **Implementation**: A concrete vocabulary and rule set that follows the requirements of this specification.
- **Extension**: An optional, namespaced addition that refines or augments an implementation without altering the core facet or tag semantics.

## 4. Versioning
SFP follows Semantic Versioning. Implementations MUST publish a version using the MAJOR.MINOR.PATCH format.
- MAJOR versions increment when backward-incompatible changes occur, such as removing a facet, renaming tags without aliases, or altering composition cardinalities.
- MINOR versions increment when backward-compatible capabilities are added, such as introducing new tags or optional facets, or adding optional extension namespaces.
- PATCH versions increment for strictly backward-compatible fixes, clarifications, or documentation updates that do not alter tag meanings or rules.

## 5. Core requirements
Implementations claiming SFP compatibility MUST:
- Define at least **two facets** and document them in the Legend.
- Keep the **core vocabulary bounded**; the Legend MUST document the core size and SHOULD target **20–60** core tags across all facets.
- Use **human-legible identifiers**; implementations SHOULD prefer whole words over abbreviations.
- Provide **short definitions** for each tag that disambiguate it from neighboring tags within the same facet.
- Publish **composition rules** that specify cardinality per facet (e.g., “exactly one from facet X,” “zero or one from facet Y,” “up to two from facet Z”).
- Define a **maximum tags per resource**; implementations SHOULD limit frames to **5–8 tags** total to avoid tag soup.
- Define an **ambiguity policy** describing how to omit a facet or decide between similar tags when uncertainty arises.
- Define a **stability policy** stating that tag meanings MUST NOT drift without an appropriate version bump consistent with the Versioning section.

## 6. Legend format
A Legend is the canonical reference for an SFP implementation.
- A Legend MUST include: implementation identifier, version, and license.
- A Legend SHOULD include: maintainers, created and updated dates, brief tag definitions, and references to any extensions.

Recommended plain-text Legend structure (placeholders only):
```
Implementation: Example-Impl
Version: 1.2.0
License: Apache-2.0
Maintainers: Example Org
Facets:
  Domain.
    Domain.Alpha — short definition
    Domain.Beta — short definition
  Object.
    Object.Report — short definition
    Object.Record — short definition
Composition rules: exactly 1 Domain; exactly 1 Object; max 6 tags total.
Ambiguity policy: prefer most specific tag; omit facet if no safe tag applies.
```

## 7. Extensions
Implementations MAY support extensions.
- Extensions MUST be namespaced to avoid collisions with core tags.
- Extensions MUST declare which facet or tag they refine or extend.
- Core interpretation MUST remain valid without processing any extensions. Frames composed solely of core tags MUST retain their meaning even when extensions are ignored.

## 8. Interoperability
Mappings to external models (e.g., Schema.org, SKOS, domain ontologies) MAY be provided but MUST be additive and MUST NOT replace SFP tags. Implementations SHOULD document mapping completeness and any lossy conversions.

## 9. Litmus tests
The pattern is being followed when:
- Frames fit comfortably into prompts or request payloads without truncation.
- Tagging agreement between reviewers improves because definitions are short and specific.
- Most resources are described with the declared maximum number of tags or fewer.
- Definitions stay brief, with clear distinctions between neighboring tags.
- Removing extensions leaves frames interpretable without re-tagging.
- Version numbers reflect meaningful changes to stability or composition rules.

## 10. Non-goals
- Being exhaustive or universal across all domains.
- Serving as a universal truth model or ontology.
- Replacing search keywords, indexing schemes, or ranking algorithms.
- Dictating storage, transport, or runtime systems.
- Providing a catalogue of tags or full vocabularies within this repository.
