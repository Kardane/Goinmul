# Goinmul

Goinmul is a Codex skill for **lean, verified engineering execution**.

It is designed to make the smallest correct change that satisfies the requested outcome, avoid speculative complexity, fix root causes instead of symptoms, and verify the result through the real consumer whenever possible.

> Lazy means efficient, not careless.

Based on: [Vowline](https://github.com/chojondocho/vowline), [Ponytail](https://github.com/dietrichgebert/ponytail)

## What it does

Goinmul combines three concerns into one engineering workflow:

- **Minimal implementation** — prefer deletion, reuse, standard-library/native capabilities, and the smallest clear local change before adding abstractions or dependencies.
- **Over-engineering review** — when asked to review rather than modify, identify unnecessary layers, speculative flexibility, duplicate helpers, and deletable complexity.
- **Execution discipline** — bind the requested outcome, authoritative inputs, write scope, and success criteria; then verify using the closest faithful interface.

Goinmul does not optimize away explicit requirements, security controls, accessibility basics, data-loss prevention, compatibility requirements, or required error handling.

## Modes

### Execution mode

The default mode for implementation, fixes, refactors, migrations, cleanup, and simplification.

Goinmul uses a minimalism ladder as a search order, not an absolute ranking. It respects project conventions and chooses a complete solution with low change scope, maintenance burden, dependency burden, and verification difficulty:

1. Omit genuinely unnecessary work.
2. Reuse an existing helper, type, pattern, or capability.
3. Use the standard library.
4. Use native platform, framework, language, database, browser, or OS features.
5. Use an already-installed dependency.
6. Use the smallest clear local implementation.
7. Add only the minimum custom abstraction or dependency required.

### Review mode

Used when the request is specifically for an over-engineering or simplification review and does **not** ask to apply fixes.

Findings include evidence, a replacement, and any conditions or checks needed to preserve behavior. Reviews prioritize reduced maintenance burden rather than line counts. Finding no simplification does not establish correctness or release readiness.

### Minimalism intensity

You can optionally specify an intensity:

- `lite` — follow the existing local approach and mention evident alternatives without searching for optional simplifications.
- `full` — default; check relevant alternatives within the touched flow and choose the lowest-burden complete solution.
- `ultra` — additionally inspect optional abstractions and configuration for removal within the authorized scope, preserving explicit requirements and correctness.

## Installation

Clone the repository, then link the skill directory into your Codex skills directory:

```bash
git clone https://github.com/Kardane/Goinmul.git ~/Goinmul
ln -s ~/Goinmul/skills/goinmul ~/.agents/skills/goinmul
```

The actual skill root is `skills/goinmul/`; repository-level documentation and licensing stay outside the runtime skill directory.

## Usage

This repository disables implicit invocation in `skills/goinmul/agents/openai.yaml`, so invoke the skill explicitly with `$goinmul`.

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
├── README.md
├── LICENSE
└── skills/
    └── goinmul/
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

`skills/goinmul/SKILL.md` contains the core execution contract. Specialized rules are kept in `skills/goinmul/references/` and are read only when relevant, keeping the default skill context focused.

## License

MIT License. See [LICENSE](LICENSE).
