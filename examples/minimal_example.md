This is a non-normative toy example.

## Facets
- **Domain**: `Domain.Alpha`, `Domain.Beta`, `Domain.Gamma`
- **Object**: `Object.Report`, `Object.Record`, `Object.Signal`

## Composition rules
- Exactly **one** Domain tag MUST be selected.
- Exactly **one** Object tag MUST be selected.
- Maximum of **6** tags per resource in total (including any optional facets not shown here).

## Example resources
1. Resource: incident summary note — Tags: `Domain.Alpha`, `Object.Report`
2. Resource: metric time series — Tags: `Domain.Gamma`, `Object.Signal`
3. Resource: archival log entry — Tags: `Domain.Beta`, `Object.Record`

## At a glance
A model interprets each frame as a small, fixed set of facet choices. By selecting one Domain and one Object, the model can rapidly categorize a resource, keep prompts compact, and apply consistent tagging while leaving room for optional extensions if needed.
