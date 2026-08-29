# Layer A demo — invisible-Unicode watermark removal

A small, reproducible demo of this project's **Layer A** cleaner
(`service/scripts/clean_text.py`) run on a children's fairy tale.

## Files

| File | What it is |
|------|-----------|
| `story.md` | The clean fairy tale (3,590 characters) |
| `story-marked.md` | Same story with 50 invisible marks injected |
| `story-marked.cleaned.md` | Cleaned output — byte-for-byte identical to `story.md` |
| `stats-marked.json` / `stats-clean.json` | The tool's `--stats` reports |
| `report.html` | Interactive report — reveals every stripped mark in place (open in a browser) |

## Reproduce (from the repo root)

```bash
# marked copy -> 49 removed, 1 exotic space normalized
python3 service/scripts/clean_text.py layer-a-demo/story-marked.md \
        -o layer-a-demo/story-marked.cleaned.md --stats

# clean copy -> all zeros, untouched
python3 service/scripts/clean_text.py layer-a-demo/story.md -o /dev/null --stats
```

## Result

Injected **50** invisible marks (zero-width joiners/spaces, BOM, word joiners,
one thin space). The cleaner removed **49** and normalized **1** exotic space;
the clean copy was left untouched, and the cleaned file is byte-for-byte
identical to the original.
