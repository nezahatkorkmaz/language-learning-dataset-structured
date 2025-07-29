# flutter-english-learning-data

This repository defines a scalable, CEFR-aligned data architecture for English language learning applications built with Flutter. It includes modular datasets organized by exercise types and proficiency levels (A1–B2), designed to support dynamic content loading in offline and mobile-first scenarios.

## Directory Structure

```
assets/
├── curriculum/
│   └── mufredat.json                         # Seviye bazlı konu ve grammar listesi (A1-B2)
│
├── data/
│   ├── matching/
│   │   ├── image_word.json                   # Görsel-kelime eşleştirme verileri
│   │   ├── idioms.json                       # Deyim ve anlam eşleştirme
│   │   ├── adjectives.json                   # Sıfat-tanım eşleştirme
│   │   └── meta.json                         # Bu klasördeki dosyaların seviyeleri, konuları vs.
│   │
│   ├── vocabulary/
│   │   ├── word_meanings.json                # Kelime anlam eşleştirme (text tabanlı)
│   │   ├── pronunciation.json                # Telaffuz + anlamlı kart sistemi
│   │   └── meta.json
│   │
│   ├── grammar/
│   │   ├── fill_in_the_blanks.json           # Boşluk doldurma (grammar yapılı)
│   │   ├── sentence_order.json               # Cümle kurma, kelime sıralama
│   │   └── meta.json
│   │
│   ├── translation/
│   │   ├── listening_translation.json        # Sesli çeviri - kelime kutucukları
│   │   ├── listening_mcq.json                # Dinlediğini anla - çoktan seçmeli
│   │   ├── sentence_rebuild_audio.json       # Dinleneni parçalarla oluşturma
│   │   └── meta.json
│   │
│   └── flashcards/
│       ├── set_1.json                        # Flashcard egzersizi için kelime seti
│       └── meta.json
│
├── ui_screens/
│   ├── screen_list.json                      # Tüm UI bileşenlerini ve açıklamalarını içerir
│   └── screens/
│       ├── flashcard.json
│       ├── fill_in_the_blank.json
│       ├── image_word_matching.json
│       ├── idiom_expression_matching.json
│       ├── adjective_definition_matching.json
│       ├── image_selection.json
│       ├── word_selection.json
│       ├── sentence_translation_audio.json
│       ├── sentence_building.json
│       ├── listening_multiple_choice.json
│       ├── listening_sentence_rebuild.json
│       ├── listening_audio_word_build.json
│       └── _template.json                    # Yeni UI'ler için şablon dosya
│
└── config/
    ├── routing_map.json                      # Hangi veri dosyası hangi arayüzle çalışır?
    └── global_settings.json                  # Dil, süre, animasyon ayarları, erişilebilirlik (opsiyonel)

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
