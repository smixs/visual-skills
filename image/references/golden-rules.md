# Golden Rules

Универсальные принципы. Работают для **обеих** семей моделей (Nano Banana и GPT Image 2).
Для модельной специфики см. [nano-banana.md](nano-banana.md), [gpt-image.md](gpt-image.md).

## 1. Start with a Verb

Tell the model the primary operation: "Create", "Generate", "Design", "Transform", "Convert", "Edit". This sets the intent before details.

## 2. Positive Framing

Describe what you WANT, not what you don't want. The model understands presence better than absence.

- ✅ "empty street" → ❌ "street with no cars"
- ✅ "clean background" → ❌ "no clutter"  
- ✅ "solo portrait" → ❌ "no other people"

## 3. Edit, Don't Re-roll

Image 80% correct? Request specific change:
- "Change lighting to sunset"
- "Make text neon blue"
- "Move chart to right third"

## 4. Natural Language

❌ Bad: "Cool car, neon, city, night, 8k"
✅ Good: "A cinematic wide shot of a futuristic sports car speeding through a rainy Tokyo street at night. Neon signs reflect off wet pavement and metallic chassis."

## 5. Be Specific

| Element | Vague | Specific |
|---------|-------|----------|
| Subject | "a woman" | "sophisticated elderly woman in vintage Chanel-style suit" |
| Material | "shiny" | "brushed steel with matte finish" |
| Color | "dark green" | "#0d3d2d deep emerald" |
| Position | "on the right" | "right third, bleeding off edge" |

## 6. Provide Context

Context helps model make logical decisions:
- "for Brazilian gourmet cookbook" → infers professional plating, shallow DOF
- "for executive strategy presentation" → infers corporate aesthetic
- "for children's educational app" → infers friendly, colorful style

## 7. Quote Text Exactly

Any text for rendering goes in quotes:
- "[HEADLINE TEXT]"
- Labels: "[Revenue Growth]", "[Net Income]"
- Specify weight: bold, thin, extra bold
- Specify position: "upper third", "centered"

## Prompt Template

```
Create a [TYPE] for [CONTEXT].

Background: [Description with hex colors]. [Atmospheric effects].

[HERO ELEMENT]:
[Detailed description - position, lighting, angle]

Typography:
Line 1: "[TEXT]" in [weight], [color], [size], [position]
Line 2: "[TEXT]" in [weight], [color], [size], [position]

[ADDITIONAL ELEMENTS]

Mood: [Emotional descriptor]
Format: [ASPECT RATIO]
```

> **Thinking Mode** (NB only), **`quality: low/medium/high`** (GPT Image 2 only) — см. соответствующие references.

## Cost Optimization (Batch Work)

- **Nano Banana:** прогон вариантов на `0.5K` Flash → отбор → переген победителя на `2K`/`4K`.
- **GPT Image 2:** прогон на `quality: low` → отбор → переген на `medium` или `high`.

В обоих случаях: дешёвая разведка → дорогой финал.

## Conversational Refinement

After generation:
- "Change the headline color to #3b82f6"
- "Add subtle drop shadow to text"
- "Increase contrast, make it more dramatic"
- "Soften the background, add blur"

## Reference Images

Multi-image вход: **NB до 14**, **GPT Image 2 до 16**. Индексируй с ролью каждой картинки.

Используй для:

**Вписать в существующий дизайн:**
```
[Attach design/layout image]
Create content following this exact layout and style.
Replace [ELEMENT] with [NEW CONTENT].
Keep colors, typography, composition.
```

**Лицо/персонаж как референс:**
```
[Attach portrait]
Use this person's face. Keep features exactly the same.
Change: [expression/pose/setting]
```

**Продукт/объект как референс:**
```
[Attach product photo]
Place this product in [NEW CONTEXT].
Match lighting and perspective.
```

**Стиль как референс:**
```
[Attach style reference]
Create [NEW CONTENT] in this exact visual style.
Match colors, textures, mood.
```

**Несколько референсов сразу:**
```
[Attach Image 1 - face]
[Attach Image 2 - outfit]
[Attach Image 3 - background]
Combine: face from Image 1, outfit style from Image 2, setting from Image 3.
```
