# Over-engineering review

Use this reference only for review mode. Review for unnecessary complexity, not general correctness.

## Scope

Find what can be removed or collapsed: reinvented standard library, redundant dependencies, speculative abstractions, dead flexibility, duplicate helpers, unnecessary layers, and verbose logic with a materially smaller equivalent.

Do not report correctness, security, performance, or style findings unless the user explicitly expands the review scope. Do not apply fixes unless asked.

A meaningful smoke check or regression test is not bloat merely because it adds lines.

## Finding format

One line per finding:

`<file>:L<line>: <tag> <what to cut>. <replacement>.`

Use the smallest applicable tag:

- `delete:` dead code, unused flexibility, speculative feature. Replacement: nothing.
- `stdlib:` hand-rolled behavior already in the standard library. Name the replacement.
- `native:` code or dependency duplicating a platform/framework feature. Name the feature.
- `yagni:` abstraction or configuration with no current second use.
- `shrink:` same behavior with materially less code. Show the smaller form when useful.

Prefer concrete locations and replacements over essays. Sort findings by expected simplification value.

End with `net: ~-<N> lines possible.` when a reasonable estimate exists.

If there is nothing material to cut, return exactly: `Lean already. Ship.`
