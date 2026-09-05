# Verification patterns

Use these rules when normal verification is insufficient, when the task names a specific verifier, or when exact runtime/byte/algorithmic behavior matters.

- Map each required public predicate to one faithful proof mode. Do not stack equivalent proof modes for the same predicate unless the contract requires independent confirmation.
- Byte proof is per surface. Includes, imports, aliases, runtime loading, generated views, or transclusion do not make one file literally contain another file's required bytes.
- Keep proof predicates aligned with allowed exceptions. If a check rejects behavior the governing contract explicitly permits, fix or replace the check rather than changing valid output to satisfy a bad proxy.
- For algorithmic or numeric work, select complexity from the maximum constraints and the actual time/resource budget. Prefer native batch, indexed, object-level, or incremental primitives over replaying the full state per item.
- When a material term has multiple plausible readings, compare those readings against the task examples, invariants, and downstream behavior. Add one boundary, adversarial, or brute-force small-state check when it can cheaply distinguish them.
- For parser, protocol, persistence, configuration, service, or deployment work, prefer a fresh-client or least-configured path that exercises the real public interface rather than an already-warmed internal state.
- If faithful proof is blocked by an ordinary missing runtime dependency and installation is allowed, install only the minimum required runtime component. Do not add broad toolchains merely to obtain redundant evidence.
- Classify failures before changing course. After a concrete failure, inspect only the failed axis first; do not start open-ended sampling, tuning, alternate-source searches, or artifact variants unless the failed axis actually requires them.
- If the named verifier and the visible governing task disagree, preserve the valid output and evidence, explain the conflict, and do not silently weaken either the task or verifier.
