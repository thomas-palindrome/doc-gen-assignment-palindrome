# doc-gen-assignment

A small, config-driven pipeline that turns a client's source material into an advice report.
See **`PROJECT_GUIDANCE.md`** for the exercise itself — start there.

## Setup

```bash
# clone your fork, then:
cp .env.example .env          # put your OpenAI key in .env
uv sync                       # or: pip install -e .
```

## Run

```bash
uv run python -m pipeline.generate --client client_01_clean
# report is written to outputs/client_01_clean.md
```

Available clients live under `data/`:

- `client_01_clean`
- `client_02_medium`
- `client_03_hard`
- `client_04_stretch` — large and messy on purpose; a deliberate stretch

## How it fits together

```
config/template_config.json   defines the report: sections, prompts, inclusion rules, source maps
        │
        ▼
pipeline/generate.py          for each section: decide inclusion, fill its prompts from the
        │                     client's data, produce the section's content
        ▼
pipeline/formatter.py         assembles the sections into the final .md document
        │
        ▼
outputs/<client>.md
```

You will mostly edit `config/template_config.json`. You're free to change anything in
`pipeline/` too.

## Notes

- The scaffold makes live OpenAI calls; you need a working key in `.env`.
- There are no "expected output" files — deciding what correct looks like (and checking it) is
  part of the task.
- Commit as you go; we read the history.
