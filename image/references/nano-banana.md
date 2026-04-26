# Nano Banana — Specific Rules

Nano Banana 2 (Flash, $0.04) и Nano Banana Pro (Gemini 3 Pro, $0.15). «Thinking» модели — понимают намерение, физику, композицию.

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

OFF по умолчанию. Включай только для:
- Невнятные результаты, требующие reasoning
- Сложные инфографики со spatial logic
- Grounding + spatial reasoning одновременно

### Multi-Reference (до 14 картинок)

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

**Workflow:** прогон вариантов на `0.5K` flash → отбор → переген победителя на `2K`/`4K`.

## Когда переключаться NB2 → NBP

- NB2 не справляется со сложным многослойным промптом.
- Нужны 14 референсов одновременно.
- Photoreal с очень тонкой работой по материалам и свету.
