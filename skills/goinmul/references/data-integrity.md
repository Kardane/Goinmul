# Data integrity

Use these rules when the outcome depends on structured data, extraction, mapping, classification, joins, aggregates, metrics, or source-backed records.

- Freeze the authoritative entity universe, allowed external references, and relation semantics before emitting structured records. A relation target, raw token, diagnostic, missing value, or decoration is not automatically a first-class record.
- Preserve ontology. A tool capability or broad noun identifies an inspection surface; it does not authorize inventing additional members or categories that the task did not request.
- Enumerate source evidence before accepting mappings, classifications, spans, extracted fields, normalizations, or joins. Accept a value only when support is sufficiently distinctive and non-contradicted for the task. Treat compatible names, ordering, sample position, ranges, or IDs as clues rather than proof when they are ambiguous.
- Emit every supported match required by the contract. Preserve unresolved ties, contradictions, external-only references, and missing values as UNKNOWN/null/diagnostic states when the schema permits them instead of coercing them into fabricated values or zero.
- For joined or multi-view outputs, choose the authoritative entity universe before aggregation. Keep unmatched, subtotal, residual, out-of-domain, and source-only data separate unless the requested schema explicitly merges them.
- Before arithmetic, bind the source-defined metric, grain, period/window, units, denominator, inclusion/exclusion rules, inequalities, tie rules, and missing-value semantics. Do not silently change grain or denominator.
- Duration labels count the periods or intervals defined by the source, not merely the number of endpoint observations, unless the task specifies otherwise.
- Recompute boundary rows and important aggregates independently when a small second calculation can catch off-by-one, filtering, grouping, or unit errors.
- Preserve source labels when they become visible or programmatic identifiers and the distinctive wording is material. Do not replace them with broader synonyms that change meaning or break downstream matching.
