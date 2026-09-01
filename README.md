# German Study Notebook

German vocabulary and verb conjugations from my notebook. Use the navigation at
the top of each page to switch between Wortschatz, Verben, and the irregular
verb drill. Click a number to mark an entry known; quiz mode hides answers until
you reveal them.


## Files

| File | What it is |
|------|------------|
| `index.html` | Wortschatz study page |
| `vocab.json` | Wortschatz data |
| `verbs.html` | Verben study page |
| `verbs.json` | Verben data: infinitive, Präteritum, Partizip II, and English |
| `irregular-verbs.html` | Interactive irregular verb drill |
| `irregular-verbs.json` | Drill data: infinitive, present, Präteritum, Perfekt, and English |

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

## Irregular verb drill

`irregular-verbs.html` presents a randomized verb and asks for the third-person
present form, Präteritum, and Perfekt. It accepts umlaut spellings such as
`fährt` or `faehrt`, shows the correct forms after an incorrect answer, and
tracks the score for the current session.

Add a drill verb to `irregular-verbs.json` using all five fields:

```json
{"infinitive": "schreiben", "present": "schreibt", "preterite": "schrieb",
 "perfect": "hat geschrieben", "en": "write"}
```

## Running it locally

The pages fetch their JSON data, and browsers block that over `file://`. Opening
an HTML file by double-clicking will show an error. Serve the repository instead:

```
python3 -m http.server
```

then open http://localhost:8000 for Wortschatz,
http://localhost:8000/verbs.html for Verben, or
http://localhost:8000/irregular-verbs.html for the irregular verb drill.

## Deploying

The included GitHub Actions workflow deploys the site whenever you push to
`staging`. In GitHub, open **Settings → Pages** and set **Source** to
**GitHub Actions** once. The deployment URL appears in the workflow summary.

Progress marks are stored in each person's own browser, so everyone tracks
their own words. Nothing is shared or synced.
