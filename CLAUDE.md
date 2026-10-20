# CLAUDE.md — Project rules for `test_secundaria`

This repository is a **static study-quiz website** for school subjects. It is a
single-page app whose **content lives in JSON data files**, so new subjects and
topics can be added **without changing the code**.

## Golden rule

- **The engine is `index.html`. Do NOT change its logic to add content.**
- **To add content you only create/edit JSON files inside `data/`** and register
  them in `data/subjects.json`.

## Structure

```
/
├── index.html              # The app engine (home + quiz). Do not edit to add content.
├── images/                 # Optional images referenced by questions (img field)
├── data/
│   ├── subjects.json       # Registry: subjects and their topics (units)
│   └── <subjectId>/
│       └── <unitId>.json   # One file per topic (the quiz + matching)
├── README.md
├── LICENSE
└── .gitignore
```

## How to add a NEW TOPIC to an existing subject

1. Create `data/<subjectId>/<unitId>.json` following the schema below.
2. Add an entry to that subject's `units` array in `data/subjects.json`.
3. Do not touch `index.html`.

## How to add a NEW SUBJECT

1. Add a new object to `subjects` in `data/subjects.json` (new `id`, `name`,
   `icon`, `lang`).
2. Create the folder `data/<subjectId>/` and add the first unit JSON there.

## Schema — `data/subjects.json`

```json
{
  "title": "Study Quizzes",
  "subtitle": "Pick a subject and a topic to practise.",
  "subjects": [
    {
      "id": "tecnologia",
      "name": "Technology",
      "lang": "en",
      "icon": "🛠️",
      "units": [
        { "id": "unit-01", "unit": "Unit 1", "title": "…",
          "file": "data/tecnologia/unit-01.json", "count": 25 }
      ]
    }
  ]
}
```

## Schema — a unit file `data/<subjectId>/<unitId>.json`

```json
{
  "subject": "Technology",
  "subjectId": "tecnologia",
  "unitId": "unit-01",
  "unit": "Unit 1",
  "title": "The workshop, the environment and safety",
  "lang": "en",
  "questions": [
    {
      "t": "Safety",
      "q": "Question text?",
      "o": ["option a", "option b", "option c", "option d"],
      "a": 1,
      "e": "Short explanation shown after answering.",
      "svg": "<svg …></svg>",
      "img": "images/example.png"
    }
  ],
  "matching": {
    "title": "Match the safety signs",
    "prompt": "Choose the sign type that matches each icon.",
    "types": [
      { "id": 1, "label": "Warning sign", "svg": "<svg …></svg>" }
    ]
  }
}
```

### Field rules

- `t` = short topic tag (shown as a chip). `q` = question. `o` = 2–4 options.
- `a` = index of the correct option (starts at 0).
- `e` = one-line explanation (optional but recommended).
- `svg` (optional) = inline SVG shown with the question. `img` (optional) = path
  to an image in `images/`. Use one or the other, not both.
- `matching` is **optional**. If present, each `types[]` item shows its `svg`
  icon and the student picks its `label`. Score = questions + matching types.
- Keep `count` in `subjects.json` equal to the number of questions (used only for
  the card label; the score is recalculated from the data at runtime).

## Validation before committing

- Every JSON file must be valid JSON (no trailing commas, double quotes only).
- Each question's `a` must be a valid index of its `o` array.
- The engine loads data with `fetch()`, so the site must be served over HTTP
  (GitHub Pages or a local server). Opening `index.html` by double-click will not
  load the data.

## Commit convention

- Adding a topic: `Add <subject> <unit>: <short title>`
- Fixing content: `Fix <subject> <unit>: <what>`
- **Do not push automatically** unless asked; the owner pushes manually.

## What NOT to do

- Do not hardcode questions inside `index.html`.
- Do not rename or restructure `data/` without updating `subjects.json`.
- Do not remove the offline bootstrap support in `index.html`.
