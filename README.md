# Goinmul

Goinmul is a Codex skill for **lean, verified engineering execution**.

It is designed to make the smallest correct change that satisfies the requested outcome, avoid speculative complexity, fix root causes instead of symptoms, and verify the result through the real consumer whenever possible.

> Lazy means efficient, not careless.

## What it does

Goinmul combines three concerns into one engineering workflow:

- **Minimal implementation** — prefer deletion, reuse, standard-library/native capabilities, and the smallest clear local change before adding abstractions or dependencies.
- **Over-engineering review** — when asked to review rather than modify, identify unnecessary layers, speculative flexibility, duplicate helpers, and deletable complexity.
- **Execution discipline** — bind the requested outcome, authoritative inputs, write scope, and success criteria; then verify using the closest faithful interface.

Goinmul does not optimize away explicit requirements, security controls, accessibility basics, data-loss prevention, compatibility requirements, or required error handling.

## Modes

### Execution mode

The default mode for implementation, fixes, refactors, migrations, cleanup, and simplification.

Goinmul follows a minimalism ladder and stops at the first option that fully satisfies the outcome:

1. Omit genuinely unnecessary work.
2. Reuse an existing helper, type, pattern, or capability.
3. Use the standard library.
4. Use native platform, framework, language, database, browser, or OS features.
5. Use an already-installed dependency.
6. Use the smallest clear local implementation.
7. Add only the minimum custom abstraction or dependency required.

### Review mode

Used when the request is specifically for an over-engineering or simplification review and does **not** ask to apply fixes.

### Minimalism intensity

You can optionally specify an intensity:

- `lite` — implement what was requested and mention a materially simpler alternative if one exists.
- `full` — default; enforce the complete minimalism ladder.
- `ultra` — aggressively challenge optional or speculative scope while preserving explicit requirements and correctness.

## Installation

Clone this repository into your Codex skills directory:

```bash
git clone https://github.com/Kardane/Goinmul.git ~/.agents/skills/goinmul
```

The repository root is the skill root, so `SKILL.md` remains directly inside the `goinmul` directory.

## Usage

This repository disables implicit invocation in `agents/openai.yaml`, so invoke the skill explicitly with `$goinmul`.

```text
$goinmul fix this parser bug and verify the real CLI path
```

```text
$goinmul ultra simplify this implementation without changing behavior
```

```text
$goinmul review this diff for over-engineering only
```

## Structure

```text
Goinmul/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── artifact-fidelity.md
    ├── benchmark-integrity.md
    ├── data-integrity.md
    ├── overengineering-review.md
    ├── repo-and-cleanup.md
    └── verification.md
```

`SKILL.md` contains the core execution contract. Specialized rules are kept in `references/` and are read only when relevant, keeping the default skill context focused.

## License

MIT License. See [LICENSE](LICENSE).
