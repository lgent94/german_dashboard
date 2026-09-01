# German Study Notebook

German vocabulary and verb conjugations from my notebook. Use the navigation at the top of either page to switch
between Wortschatz and Verben. Click a number to mark an entry known; quiz mode
hides answers until you reveal them.


## Files

| File | What it is |
|------|------------|
| `index.html` | Wortschatz study page |
| `vocab.json` | Wortschatz data |
| `verbs.html` | Verben study page |
| `verbs.json` | Verben data: infinitive, Präteritum, Partizip II, and English |

## Adding vocabulary

Append to `entries` in `vocab.json`, and extend `pages` with the new range.

```json
{"n": 127, "art": "die", "word": "Übung", "extra": ", -en", "pos": "f.",
 "en": "the exercise", "note": "shown in italics", "flag": "shown in amber"}
```

Only `n` and `word` are required. `art` must be `der`, `die` or `das` — it drives
the gender colour. Leave it out for adjectives and adverbs.

## Adding verbs

Append to `entries` in `verbs.json`, and extend `pages` with the new range.

```json
{"n": 69, "infinitive": "schreiben", "preterite": "schrieb",
 "participle": "geschrieben", "en": "write"}
```

Each verb should include its infinitive, Präteritum, Partizip II, and English
translation. The Verben page supports search, page ranges, shuffling, quiz mode,
CSV export, and browser-local progress marks.

## Running it locally

The pages fetch their JSON data, and browsers block that over `file://`. Opening
an HTML file by double-clicking will show an error. Serve the repository instead:

```
python3 -m http.server
```

then open http://localhost:8000 for Wortschatz or http://localhost:8000/verbs.html
for Verben.

## Deploying

Settings → Pages → Source: **Deploy from a branch** → branch `main`, folder `/ (root)`.
No workflow file is needed; the files are already browser-ready.

Progress marks are stored in each person's own browser, so everyone tracks
their own words. Nothing is shared or synced.
