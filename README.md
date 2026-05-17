# Court Decision Summarizer

Local web application that uses an LLM to summarize court decisions into structured, customizable reports for lawyers.

## MVP overview

- **Run locally** on Windows or Linux with a single script (`run.sh` / `run.bat`)
- **Work on case** — dialog + editable structured summary (configurable blocks)
- **Case history** — resume past cases; auto-delete after 3 days of inactivity
- **Settings** — summary blocks (LLM instructions) and text templates
- **Statistics** — token usage and processing timelines per case and overall
- **Pluggable LLM** — switch model and endpoint via `.env` without changing business logic

**UI chrome** (menus, buttons): English. **Dialog** and **Summary** follow the case: default language is detected from the court decision; if you switch language in chat, the app replies in your language while the summary stays in the case language.

## Documentation

| Document | Description |
|----------|-------------|
| [Problem statement](docs/problem_statement.md) | Business context, current pain, expected impact |
| [Technical specification (MVP)](docs/technical_specification.md) | Full requirements, API contract, acceptance criteria |
| [Architecture](docs/architecture.md) | Implementation design (to be filled during development) |
| [Prompt engineering](docs/prompt_engineering.md) | Prompt versioning and tuning notes |
| [Evaluation](docs/evaluation.md) | Quality evaluation methodology |

## Quick start (planned)

```bash
# Linux
./run.sh start

# Windows
run.bat start
```

Configure LLM access by copying `.env.example` to `.env` and setting your API key and model.

## Project structure

```
prompts/          # LLM prompt templates (validate, summarize, refine)
examples/         # Sample court decision text
docs/             # Specifications and design docs
run.sh / run.bat  # Start/stop scripts
```

## License

See [LICENSE](LICENSE).
