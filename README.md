# flutter-english-learning-data

This repository defines a scalable, CEFR-aligned data architecture for English language learning applications built with Flutter. It includes modular datasets organized by exercise types and proficiency levels (A1–B2), designed to support dynamic content loading in offline and mobile-first scenarios.

## Directory Structure

```
assets/data/
├── matching/
│   ├── image_word.json
│   ├── idioms.json
│   ├── adjectives.json
│   └── meta.json
├── vocabulary/
│   ├── word_meanings.json
│   ├── pronunciation.json
│   └── meta.json
├── grammar/
│   ├── fill_in_the_blanks.json
│   ├── sentence_order.json
│   └── meta.json
├── translation/
│   ├── listening_translation.json
│   └── meta.json
└── flashcards/
    ├── set_1.json
    └── meta.json
```

Each exercise type is stored in its own file and described by a corresponding `meta.json`, which allows dynamic loading and filtering by CEFR level, topic, or category.

## CEFR Curriculum

The dataset is mapped to a CEFR-aligned curriculum defined in `mufredat.json`, which includes:

- A1–B2 topics (e.g., "Daily routines", "Ordering food")
- Grammar structures (e.g., "Simple Present", "Past Simple")

This mapping supports personalized and level-specific content generation.

## Usage (Flutter)

```dart
final String jsonString = await rootBundle.loadString('assets/data/flashcards/set_1.json');
final List<dynamic> data = json.decode(jsonString);
final flashcards = data.map((e) => Flashcard.fromJson(e)).toList();
```

For each JSON file, a corresponding Dart model (with `fromJson` / `toJson`) must be defined.

## Meta File Example

Each `meta.json` includes:

```json
{
  "category": "grammar",
  "level": "A2",
  "topic": "Past Simple",
  "type": "fill_in_the_blanks",
  "file": "fill_in_the_blanks.json",
  "count": 20
}
```

## Goals

- Structured, modular dataset for Flutter apps
- Curriculum-aligned (CEFR)
- Offline-first support
- Extendable to new exercise types
- Admin panel-ready design (future scope)

## Contributing

To contribute:

- Fork the repository
- Add new datasets using the existing format
- Include a `meta.json` for every new content file
- Submit a pull request with a clear description

## License

MIT License. See LICENSE file for details.
