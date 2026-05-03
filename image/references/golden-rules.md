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

## World Knowledge Anchors

GPT Image 2 обладает глубокими знаниями о культуре, эпохах и визуальных стилях. Вместо описания каждой детали — дай модели культурный/временной/жанровый якорь, и она сама заполнит аутентичные детали.

### Три типа якорей

**Era anchors** — временной и географический маркер, который вызывает целый визуальный мир:
- "Bethel, NY, August 1969" → Woodstock aesthetic без необходимости описывать тай-дай, грязь, сцены
- "Berlin, November 1989" → падение стены, толпы, граффити, эйфория
- "Tokyo, 1982" → неоновый Shinjuku, аналоговая электроника, ранний cyberpunk

**Cultural anchors** — перенос визуального языка одного культурного объекта на другой контекст:
- "{game_title} in {real_city}" → автоматически применяет визуальный стиль игры к реальной локации (GTA style, Persona style, и т.д.)
- "Soviet constructivism poster about {modern_topic}" → стиль Родченко/Эль Лисицкого на современную тему
- "Ukiyo-e print of {modern_scene}" → японская гравюра с современным содержанием

**Genre anchors** — режиссёр/фотограф/движение как линза:
- "Peter Lindbergh influence" → сильный Ч/Б, минимальная ретушь, raw editorial
- "Wes Anderson palette" → симметричный кадр, пастельная палитра, центрированная композиция
- "Studio Ghibli mood" → мягкое акварельное небо, зелёная листва, тёплый ностальгический свет
- "Roger Deakins lighting" → натуральный свет, глубокие тени, кинематографичный объём

### Правила использования

1. **Используй как HIGH-LEVEL steering** — якорь задаёт настроение и эстетику, а не заменяет весь промпт
2. **Комбинируй с конкретными визуальными деталями** — якорь устанавливает мир, детали устанавливают специфику
3. **Не стакай несколько genre anchors** — выбери один. "Peter Lindbergh + Wes Anderson" = каша
4. **Era/cultural anchors работают лучше с GPT Image 2** (world knowledge). С Nano Banana результат менее предсказуем — NB больше опирается на явные описания

### Примеры

**Era anchor + конкретные детали:**
```
Create an editorial portrait set in Havana, 1957.

Subject: jazz musician leaning against pastel-colored colonial building,
holding trumpet loosely at his side. Linen suit, open collar.
Lighting: harsh Caribbean afternoon sun, deep shadows under awning.
Format: 3:4
```
> "Havana, 1957" вызывает: старые американские машины на заднем плане, облупившаяся штукатурка, кованые балконы, тропическая атмосфера — без необходимости это описывать.

**Cultural anchor + новый контекст:**
```
Create a scene of a quiet Kyoto temple garden, rendered in the visual style
of Studio Ghibli. Morning mist over moss-covered stones, a single monk
sweeping fallen maple leaves. Soft watercolor textures, warm nostalgic palette.
Format: 16:9
```
> "Studio Ghibli" задаёт акварельность, теплоту, ностальгию. Детали (мох, клён, монах) задают конкретную сцену.

**Genre anchor + специфика:**
```
Create a fashion editorial portrait with Peter Lindbergh influence.

Subject: model in oversized men's blazer, no makeup, wind-tousled hair.
Setting: empty winter beach, overcast sky.
Mood: raw, unpolished beauty
Format: 2:3
```
> "Peter Lindbergh influence" даёт: мощный Ч/Б (или desaturated), отсутствие ретуши, raw emotional quality. Детали (пляж, блейзер, ветер) конкретизируют кадр.
