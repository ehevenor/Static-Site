<!-- .github/copilot-instructions.md - guidance for AI coding agents -->

# Copilot / AI agent instructions — Static-Site

Short, actionable notes so an AI agent can be productive immediately in this repository.

## Quick summary
- Project is minimal and currently contains source stubs under `src/`.
- Key files discovered: `src/main.py` and `src/textnode.py`.

## Big-picture (what's discoverable)
- `src/main.py` currently contains a single code-line-like reference to `./main.sh` (i.e. the project entry expects a shell script to run). Inspect `src/main.py` first when reasoning about runtime behavior.
- `src/textnode.py` defines a `Textnode` Enum scaffold: changes to content node types belong here.

Examples from the codebase:
- `src/main.py` contains the token: `./main.sh` (treat this as the runtime entry invocation).
- `src/textnode.py` contains: `class Textnode(Enum):` — extend this enum when adding new node types

## What to do when you edit code
- If you add a runtime entry (replace `./main.sh`), update `src/main.py` to show how the project should be invoked and include a short comment explaining the steps.
- When adding new node types or content kinds, add enum members inside `Textnode` in `src/textnode.py` and keep imports minimal (project currently uses only the `enum` standard library).

## Running & debugging (discoverable, minimal)
- No tests or CI workflows were found. Before adding CI, verify local execution manually.
- To try running the referenced entry script from the repo root (run from the `src/` directory):

```bash
cd src
bash ./main.sh   # if present and executable
```

- If you need to run Python files directly, use the system Python:

```bash
python3 -m src.main   # only useful if main.py is a runnable module
```

Note: both commands are suggestions based on what is present; they may be no-ops while this repo is scaffolded.

## Conventions & patterns (repo-specific)
- Source lives under `src/`.
- Small, single-purpose files: `textnode.py` holds a central enum used across content logic.
- Shell-first entry: the presence of `./main.sh` in `src/main.py` suggests the project expects shell orchestration for site generation.

## Integration points & external dependencies
- No external packages, requirements, or CI configurations were found in the current snapshot — treat this as a small, local project until additional manifests are added.

## When creating PRs or edits
- Keep changes small and focused; update `src/main.py` comments to indicate how to run any new entrypoints.
- If you add files or scripts, reference them from `src/main.py` so future agents find the entrypoint quickly.

## If something's unclear
- Ask the repo owner which script is the intended entry (`main.sh`) and whether `src/` should be a package (i.e., add `__init__.py`) before converting `main.py` to an importable module.

---
If you want, I can iterate: (A) expand this with a README or runnable example script, or (B) infer a minimal `main.sh` and a small test harness — tell me which and I will implement it.
