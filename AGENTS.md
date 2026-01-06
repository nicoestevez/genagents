# Repository Guidelines

## Project Structure & Module Organization
- `genagents/`: core package for generative agents; main API is `genagents/genagents.py` with interaction and memory modules in `genagents/modules/`.
- `simulation_engine/`: LLM prompt templates and helpers (`prompt_template/`, `global_methods.py`, `gpt_structure.py`).
- `agent_bank/`: stored agent data, including sample agents under `agent_bank/populations/`.
- `main.py`: simple CLI-style conversation runner for a single agent.
- `static_dir/`: images used by docs.

## Build, Test, and Development Commands
- `pip install -r requirements.txt`: install Python dependencies.
- `cp simulation_engine/example-settings.py simulation_engine/settings.py`: start config (then edit API key and owner).
- `python main.py`: run the sample conversation loop with the sample agent.
- `python -c "from genagents.genagents import GenerativeAgent; print(GenerativeAgent())"`: quick import sanity check.

## Coding Style & Naming Conventions
- Python code uses 2-space indentation in existing files; keep this consistent.
- Use `snake_case` for functions/variables and `PascalCase` for classes (e.g., `GenerativeAgent`).
- Keep functions short and side-effect aware; prefer updating `scratch` via `update_scratch`.
- No formatter or linter is enforced in the repo; avoid introducing new tooling without discussion.

## Testing Guidelines
- No automated test suite is currently present.
- If you add tests, place them under `tests/` and name files `test_*.py` for pytest compatibility.
- When adding new behavior, include a minimal reproducible example in the PR description if tests are not added.

## Commit & Pull Request Guidelines
- Commit history uses short, descriptive messages (e.g., "add protection for empty memory stream"); use present-tense, action-oriented wording.
- Avoid vague messages like "a"; describe the change and scope.
- PRs should include: a brief summary, how to run any new code paths, and links to related issues if applicable.
- If changes affect agent data or prompts, call out the specific paths touched (e.g., `simulation_engine/prompt_template/`).

## Security & Configuration Tips
- Do not commit API keys. Store the OpenAI key only in `simulation_engine/settings.py` (which should be local-only).
- Be mindful that `agent_bank/` may contain sensitive or large data; avoid unnecessary churn in those files.
