# RICO paper working agreements

Apply the user's global working agreements. Start with [README.md](README.md)
and [the source manifest](references/sources.toml).

- Preserve guided implementation: the learner edits scientific code and runs
  checks unless they explicitly delegate a step.
- Inspect the pinned original implementation before proposing each operation.
  Record provenance for individually copied reference files.
- Keep reusable Python under `src/rico_paper`; use notebooks to inspect and
  explain each operation. Use Pydantic for configuration and persisted metadata,
  and dataclasses for runtime arrays.
- Use Python 3.12 in this repository's `.venv`. Apply the README's formatting,
  Pyrefly, affected-test, and final Ruff sequence after Python changes.
- Preserve downloaded sources and completed measurements. Record inputs,
  configuration, runtime, and digests before scientific comparisons.
- Review every staged public file for credentials, private infrastructure
  locations, third-party licensing, and accidentally included data.
