# Nano Banana — Specific Rules

Три тира. «Thinking» модели — понимают намерение, физику, композицию.

| Тир | Model ID | Роль |
|-----|----------|------|
| **NB2 Lite** | `gemini-3.1-flash-lite-image` | Самая быстрая и дешёвая ($0.034, ~4 сек), только 1K. Черновики, массовые батчи |
| **NB2** (Flash) | `gemini-3.1-flash-image` | Дефолтный workhorse: Pro-фичи (текст, 4K, grounding, консистентность) на скорости Flash |
| **NBP** (Pro) | `gemini-3-pro-image` | Топ-тир: сложные многослойные сцены, максимум reasoning и контроля |

## Стиль промпта

Натуральный язык, 1-2 параграфа. Структура свободная, но порядок помогает:
**Subject + Action + Location/context + Composition + Style**

```
A cinematic wide shot of a futuristic sports car speeding through a rainy
Tokyo street at night. Neon signs reflect off wet pavement and metallic
chassis. Format: 16:9.
```

## Что НЕ указывать

- Числовые параметры объектива: **50mm, 85mm, f/2.8, ISO 400** — NB игнорит. Используй описание: «shallow depth of field», «wide-angle distortion».
- Tag-soup: «cool, modern, 4k, cinematic» — пишет связным предложением.

## Уникальные возможности

### Image Grounding (NB2 only)
NB2 ищет реальные изображения в интернете до генерации. Архитектурно точные конкретные локации, корректные виды животных/растений.

```
Generate a cinematic, golden-hour photograph of [SPECIFIC REAL PLACE].
Ensure the architectural details, the spire, the surrounding square, and
the landscape are accurate to reality.
```

**Работает:** здания, мосты, площади, виды животных, виды растений, насекомые.
**Не работает:** конкретные люди.

### Extreme Aspect Ratios (NB2 only)

1:8, 8:1, 1:4, 4:1 — для баннеров, скроллов, комикс-стрипов.

```
Create a 4-panel horizontal comic strip (aspect ratio 4:1).
The story follows [CHARACTER] doing [ACTION] that ends with a twist.
Use a vibrant comic book style. Keep character design consistent.
```

Стандартные: 1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 21:9.

### Thinking Mode

Включён по умолчанию; у NBP отключить нельзя (модель рисует до 2 «thought images» в бэкенде, они не тарифицируются как картинки, но thinking-токены платные). У NB2 есть рычаг `thinking_level: minimal | high` (default `minimal`) — поднимай до `high` для:
- Невнятных результатов, требующих reasoning
- Сложных инфографик со spatial logic
- Grounding + spatial reasoning одновременно

### Multi-Reference (лимиты по тирам)

| | NB2 Lite | NB2 | NBP |
|---|---|---|---|
| High-fidelity объекты | до 14 | до 10 | до 6 |
| Character-consistency рефы | нет | до 4 | до 5 |
| Style рефы | нет | нет | до 3 |

```
[Image 1: face]
[Image 2: outfit]
[Image 3: background]
Combine: face from Image 1, outfit style from Image 2, setting from Image 3.
Match lighting and perspective.
```

### JSON для сложных сцен (5+ элементов)

```json
{
  "subject": {"description": "main subject", "expression": "emotion/pose"},
  "photography": {"angle": "eye-level", "shot_type": "waist-up", "aspect_ratio": "16:9"},
  "background": {"setting": "location", "lighting": "soft natural"}
}
```

## Editing у Nano Banana

Conversational, без масок:

```
Remove [OBJECT] from this image.
Fill with [LOGICAL REPLACEMENT] matching surroundings.
Keep [PRESERVED ELEMENTS] exactly the same.
```

После генерации добавляй итеративно:
- «Make it warmer»
- «Increase contrast»
- «Soften background, add blur»
- «Change headline color to #3b82f6»

Interactions API держит контекст сессии — до 3 последовательных правок стэкаются без потери исходника. Правило «Edit, don't re-roll»: картинка верна на 80% — проси точечное изменение, а не новую генерацию.

## Text Rendering

- SOTA по 100+ языкам.
- Font можно называть: «Century Gothic 12px», «Brush Script», «Impact», «Heavy blocky sans-serif».
- Multi-language в одном кадре работает.
- Hack: для сложного текста — сначала попроси модель **написать текст**, потом отдельным промптом «вставь этот текст в картинку».

## Resolution / Cost

| Resolution | Использование |
|------------|---------------|
| 0.5K | Самая дешёвая, batch и А/B варианты |
| 1K | Default |
| 2K | Финальный отбор |
| 4K | Печать, hero-ассеты |

**Workflow:** прогон вариантов на `0.5K` flash (или NB2 Lite на 1K) → отбор → переген победителя на `2K`/`4K`.

В API `image_size` пишется строго с заглавной K (`1K`, `2K`, `4K`) — `1k` отклоняется. `512px` есть только у NB2; Lite — только 1K. Без указания размера модель матчит вход, иначе 1:1.

## Кейфреймы для видео

Nano Banana — image-слой перед motion-слоем. Всё критичное фиксируется на картинке ДО анимации: identity, композиция, aspect ratio, видимый текст, состояние продукта. Видеомодель усиливает любую неоднозначность стилла.

- **Character sheet / hero frame.** Утверди один кадр-эталон персонажа, на него ссылаются все последующие video-промпты.
- **Aspect ratio сразу целевой.** Кампании нужен вертикальный ролик — генери 9:16, а не кропай после анимации (тихая точка отказа).
- **Хэндофф в видеомодель — motion brief, не пересказ.** Движение камеры, движение субъекта, движение фона, длительность, framing lock, запрещённые изменения. Видео-промпт не переописывает то, что уже есть в кадре.
- Downstream любой: Veo 3.1, Kling 3.0, Seedance 2.0/2.5, Gemini Omni Flash (штатная пара Google, 10-сек клипы). Батч картинок → ревью-гейт → в видео уходят только одобренные стиллы.

## Известные фейлы

- Руки и лица всё ещё плывут (пальцы, суставы, дрейф likeness) — явные anatomy-инструкции + рефы + перегенерации. Есть отчёты, что NBP держит лица хуже NB2.
- Мелкий текст мылится на 1K — для плотного текста 2K+ или GPT Image 2.
- Инфографика может содержать фактически неверные данные — цифры проверять всегда, grounding помогает, но не гарантирует.
- Склонность к overcooked HDR / пересату — проси «natural contrast, no HDR look».
- SynthID-водяной знак стоит на всех генерациях (невидимый); на Vertex дополнительно C2PA.

## Когда переключаться NB2 → NBP

- NB2 не справляется со сложным многослойным промптом.
- Нужен максимум референсов с разбивкой по ролям (6 объектов + 5 character + 3 style).
- Photoreal с очень тонкой работой по материалам и свету.
- NBP медленнее и дороже; на лицах иногда проигрывает NB2 — для портретной серии сначала тестируй оба.
