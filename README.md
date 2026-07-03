# fonora-data

Research and optional datasets for [Fonora/fonora](https://github.com/Fonora/fonora).

This repo holds growing JSON artifacts that do not belong in the main codebase:

| File | Purpose |
|------|---------|
| `data/fonoran-llm-evaluations.json` | LLM Compositional Intuition Battery rounds (advisory; outcomes promoted in main repo `compounds.json`) |
| `data/fonoran-playtests.json` | Human Puzzle Conversation playtest rounds |
| `data/fonoran-translation-test-latest.json` | Translation regression snapshot for `/language#gaps` |
| `data/research-notes-store.json` | Research notebook canonical JSON (synced to Postgres on Heroku release) |

## Layout

```
fonora-data/
  manifest.json          # schema version + SHA256 checksums
  data/
    fonoran-llm-evaluations.json
    fonoran-playtests.json
    fonoran-translation-test-latest.json
    research-notes-store.json
```

## Usage with fonora

Clone the main repo, then either:

```bash
git submodule update --init   # vendor/fonora-data
```

Or set in `.env`:

```
FONORAN_DATA_DIR=vendor/fonora-data
```

The main repo pins this data via `data/fonora-data.manifest.json` (commit SHA or release tag).

## Workflow

1. Run LLM intuition or playtests locally — writes append to files here.
2. Commit and push to `fonora-data`.
3. Bump the manifest pin in `Fonora/fonora` when production should ingest a milestone.

## License

MIT — same as Fonora/fonora.
