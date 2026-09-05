# Over-engineering review

Use this reference only for review mode. Review for unnecessary complexity, not general correctness.

## Scope

Find what can be removed or collapsed: reinvented standard library, redundant dependencies, speculative abstractions, dead flexibility, duplicate helpers, unnecessary layers, and verbose logic with a materially smaller equivalent.

Do not report correctness, security, performance, or style findings unless the user explicitly expands the review scope. Do not apply fixes unless asked.

A meaningful smoke check or regression test is not bloat merely because it adds lines.

## Finding format

Keep each finding concise, with room for evidence and behavioral constraints:

`<file>:L<line>: <tag> <what to cut and evidence it is unnecessary>. <replacement>. <conditions or checks needed to preserve behavior>.`

Check actual callers and contracts before recommending removal. If that evidence is unavailable, label the candidate as unconfirmed and state the missing check rather than presenting deletion as safe.

Use the smallest applicable tag:

- `delete:` dead code, unused flexibility, speculative feature. Replacement: nothing.
- `stdlib:` hand-rolled behavior already in the standard library. Name the replacement.
- `native:` code or dependency duplicating a platform/framework feature. Name the feature.
- `yagni:` abstraction or configuration with no current caller, boundary, testing need, or project contract that justifies it; one implementation alone is not sufficient evidence.
- `shrink:` same behavior with materially less code. Show the smaller form when useful.

Prefer concrete locations and replacements over essays. Sort findings by reduced maintenance burden, such as eliminated duplicate paths, dependencies, or configuration, while preserving clarity and behavior.

An estimated line reduction is optional supporting information, not a success criterion.

If there is nothing material to cut, say that no material simplification was found within the inspected scope, using the user's language. State any material inspection limitation. Do not imply correctness, security, or release readiness from a complexity-only review.
