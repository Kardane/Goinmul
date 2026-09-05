# Repository and cleanup scope

Use these rules for repository edits, configuration, credentials, deployment/service state, cleanup, purge, or other potentially broad write operations.

- Determine the live write surface from the requested outcome, the files or state actually loaded/used by the target system, and any explicit path constraints. Inspect broadly when needed, but write narrowly.
- Do not turn search results, tracked-file lists, repository-wide grep hits, generated manifests, or dependency inventories directly into edit sets. Review the role of each target before writing.
- Documentation, examples, tests, fixtures, datasets, snapshots, archives, generated results, and history are not universally protected or editable. Their status follows the user's requested target and the governing project rules. Do not use filename heuristics to override explicit scope.
- For cleanup, distinguish present live state from history. Removing a live secret, config value, file, or credential reference does not imply rewriting commits, reflogs, object stores, backups, remote copies, or external storage.
- Treat history rewriting, storage purge, credential revocation, remote deletion, destructive reset, and irreversible publication changes as separate consequential actions. Perform them only when explicitly requested or already authorized and when the target is concrete enough to review.
- For secret cleanup, edit concrete secret material or active references only on surfaces authorized by the task. Preserve required wrappers and syntax. Report residual occurrences outside the authorized write scope rather than silently widening the scope.
- For named non-secret cleanup, edit only the requested class of material. Do not generalize one cleanup request into unrelated stylistic or repository-wide changes.
- Put configuration, build, deployment, policy, storage, auth, publishing, service, or VCS declarations in the canonical scope actually loaded by the target system.
- Prefer proving the least-configured fresh-client path before optional aliases, alternate credentials, sample variants, or convenience modes. Ensure optional secure/named modes are additive when the ordinary default path must remain usable.
- Inspect existing changes before editing. If a protected or unrelated file was changed accidentally, undo only your own changes before final delivery unless the user subsequently expands scope. Preserve pre-existing and concurrent user changes; do not reset an entire file to the repository version when it contains unrelated work. If ownership cannot be distinguished, report the conflict rather than discarding uncertain changes.
