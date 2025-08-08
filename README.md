# Question Packs

Place JSON files here following naming pattern (new):

```text
<quizTypeRaw>_<level>_<questionFormat>_<lang>.json              (monolingual)
<quizTypeRaw>_<level>_<questionFormat>_<lang1>-<lang2>.json     (bilingual)
```

Where:

* `quizTypeRaw`: `general`, `popCulture`, `moviesTV`, `sports`, `history`, `science`, `custom`
* `level`: `icebreaker`, `easy`, `medium`, `advanced`, `expert` or `all`
* `questionFormat`: `multiple_choice` | `open_ended`
* `lang` / `lang1-lang2`: `en` | `ru` (for bilingual pack order = primary-secondary)

Legacy pattern (still supported as fallback during transition):

```text
<quizTypeRaw>_<questionFormat>_<languageCode>.json
```

## JSON Schema (array) – Monolingual

```json
[
  {
    "question": "What is the capital of France?",
    "options": ["Paris", "Berlin", "Madrid", "Rome"],
    "correct_answer": "Paris",
    "explanation": "Paris has been France's capital since the early Middle Ages.",
    "level": "easy"
  }
]
```

### Open-ended example entry (omit options)

```json
{
  "question": "Describe the water cycle stages.",
  "correct_answer": "",
  "explanation": "Evaporation, condensation, precipitation, collection.",
  "level": "medium"
}
```

## Bilingual Packs

For bilingual packs, encode primary + secondary text separated by a newline (`\n`) in each textual field (`question`, each `options` element, `correct_answer`, `explanation`). Example bilingual multiple choice entry (English primary, Russian secondary):

```json
{
  "question": "What is the capital of France?\nКакова столица Франции?",
  "options": [
    "Paris\nПариж",
    "Berlin\nБерлин",
    "Madrid\nМадрид",
    "Rome\nРим"
  ],
  "correct_answer": "Paris\nПариж",
  "explanation": "Paris is France's capital.\nПариж — столица Франции.",
  "level": "easy"
}
```

## Notes

* `correct_answer` required; for open-ended may be empty string.
* `level` optional but recommended for filtering.
* Provide 50 questions per file to ensure robust top-up.
* Keep options length typically 4 (multiple choice consistency).
* Avoid duplicates across packs (the app filters by similarity but uniqueness improves variety).
* Explanations should always be present and fact-checked; entries without explanation are ignored for fallback.
