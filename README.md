# ta-tool

A command line toolkit for teaching assistants, built around an LLM (Anthropic or OpenAI, or a stub provider for testing) to help with the repetitive parts of grading and office hours. Installs as a single `ta` command.

## Commands

- `ta build-rubric <assignment_file>` — generate a structured grading rubric from an assignment description.
- `ta reply "<question>"` — draft a TA reply to a student question pulled from Canvas or email. `--socratic` limits the reply to guiding questions instead of answers.
- `ta triage <submission_folder>` — check a folder of student submissions for completeness, syntax errors, and missing required functions (`--require-fn` can be repeated to check for specific functions).
- `ta office-prep <assignment_file>` — prepare explanations, common confusion points, and a cheat sheet ahead of office hours, optionally informed by a `--weaknesses` file of known weak areas from past cohorts.
- `ta stats <grades_file>` — compute grade statistics and distribution from a CSV of grades.
- `ta debug <code_file>` — point out bugs in a student's Python file with teaching hints, without rewriting their solution.

Every command accepts `--json` for machine-readable output and `--verbose` for LLM call diagnostics.

## Configuration

Copy `ta_config.toml.example` to `ta_config.toml` (or `~/.ta_config.toml`) and set:

- `tone` — friendly, formal, or strict
- `strictness` — grading strictness: low, medium, or high
- `grading_style` — rubric style hint passed to the LLM
- `llm_provider` — anthropic, openai, or stub
- `model` — model ID matching the selected provider
- `cache_ttl` / `cache_dir` — local response caching to cut down on repeat LLM calls
- `max_tokens` — max tokens per LLM response

## Install

```
pip install -e .
```

Requires Python 3.11+.

## License

MIT — see [LICENSE](LICENSE).
