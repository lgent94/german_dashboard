# Wortschatz

German vocabulary from my notebook, as a web page. Click a number to mark a word
known; "Quiz mode" hides the translations until you click them.


## Files

| File | What it is |
|------|------------|
| `index.html` | the web page |
| `vocab.json` | the vocabulary data |

## Adding words

Append to `entries` in `vocab.json`, and extend `pages` with the new range.

```json
{"n": 127, "art": "die", "word": "Übung", "extra": ", -en", "pos": "f.",
 "en": "the exercise", "note": "shown in italics", "flag": "shown in amber"}
```

Only `n` and `word` are required. `art` must be `der`, `die` or `das` — it drives
the gender colour. Leave it out for adjectives and adverbs.

Commit to the default branch and the site updates within a couple of minutes.

## Running it locally

`index.html` fetches `vocab.json`, and browsers block that over `file://`.
Opening the HTML by double-clicking will show an error. Serve it instead:

```
python3 -m http.server
```

then open http://localhost:8000

## Deploying

Settings → Pages → Source: **Deploy from a branch** → branch `main`, folder `/ (root)`.
No workflow file needed; the files are already browser-ready.

Progress marks are stored in each person's own browser, so everyone tracks
their own words. Nothing is shared or synced.
