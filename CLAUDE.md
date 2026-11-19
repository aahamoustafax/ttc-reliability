# TTC reliability

**Question:** where and when does the TTC lose the most time to delays, why, and which fix is worth it?
**Data:** Toronto Open Data TTC subway delay files (date, time, station, minutes, cause code).
Known mess: irregular updates, missing months, column changes, cause codes missing from the key.

## Who writes what
- I (the owner) write the core logic: SQL, dbt models, Python transforms, tests' expectations.
  Don't write it for me. Review what I wrote, including code that works but isn't idiomatic.
- You write setup, config and boilerplate, and explain each piece: what it does, why, what breaks without it.
- Before writing into project files, say what you'll write and wait for my OK.

## Commands
- Run anything: `uv run <command>`. Add a package: `uv add <name>`. Never use pip.
- Format and lint: `uv run ruff format .` then `uv run ruff check .`
- Type check: `uv run mypy .`
- Tests: `uv run pytest` (tests live in `tests/`)
- pre-commit runs ruff and mypy on every commit; if a commit is blocked, fix the cause, never skip the check (no `--no-verify`).

## Data rules
- Never invent or "fix" data silently. Anything odd in the data goes in the quirks log with the file and row.
- Raw files are never edited; they stay as downloaded.
- No secrets in code or git. AWS keys live in `.env` only.

## Git
- One-line Conventional Commits, no body, no Co-Authored-By trailer.
- Show me the diff and a short summary before every commit; commit only after I approve.
