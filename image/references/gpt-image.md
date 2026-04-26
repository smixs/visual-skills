# GPT Image 2 — Specific Rules

Production default OpenAI: `gpt-image-2`. Migration-only: `gpt-image-1.5`, `gpt-image-1`. Бюджетный: `gpt-image-1-mini`.

## Структура промпта — 5 slots

GPT Image 2 сильнее всего реагирует на разделение по секциям. Пиши лейблами, не сплошным текстом.

```
Scene: location, time of day, background, environment
Subject: primary focus — who or what is central
Important Details: materials, textures, lighting, camera angle, mood, composition
Use Case: editorial, product mockup, UI, poster, infographic
Constraints: what must NOT change/appear (no watermarks, preserve face, no extra text)
```

> «The fifth slot is where most mediocre prompts fail silently.» Без явных constraints модель дрейфует.

### Минимальный пример

```
Scene: small Lisbon florist storefront at blue hour, wet cobblestones
Subject: woman in navy apron locking the front door, half-turned to camera
Important Details: warm interior glow spilling onto pavement, 50mm feel,
  soft contact shadows, brushed brass door handle, "Florista" hand-painted sign
Use Case: editorial photography
Constraints: no extra signage, no people in background, no text other than the sign
```

## Anti-Slop Rules

GPT Image 2 особенно чувствителен к качеству формулировок. Vague praise = деградация результата.

| ❌ Не пиши | ✅ Пиши |
|-----------|---------|
| stunning, incredible, epic, gorgeous, masterpiece | overcast daylight, brushed aluminum, chipped paint, 50mm feel |
| «minimalist brutalist luxury photoreal» (стиль-теги) | «cream background, heavy black sans-serif, asymmetrical type block, one hero object, generous negative space» |
| «как в Apple-рекламе» | конкретные визуальные факты |
| мудовый язык, в котором тонут функциональные требования | прямое заявление: «image must contain a transit kiosk» |

## Quality Settings — рычаг fidelity / latency

| Setting | Когда |
|---------|-------|
| `quality: low` | High-volume, превью, exploratory, latency-sensitive, draft |
| `quality: medium` | **Default starting point** |
| `quality: high` | Маленький/плотный текст, infographics, портреты, identity-sensitive edits, brand assets |

Стартуй с `low`, апгрейди по необходимости. Часто `low` уже достаточно.

## Размеры (gpt-image-2)

- Max edge: <3840px
- Обе стороны: кратны 16
- Aspect ratio: max 3:1 (long:short)
- Total pixels: 655 360 – 8 294 400
- Reliable upper bound: 2560×1440

**Ходовые:**
- Portrait 1024×1536
- Landscape 1536×1024
- Square 1024×1024
- 2K 2560×1440

> Экстрим вроде 1:8 / 8:1 GPT Image 2 НЕ умеет — иди в Nano Banana.

## Text in Image

- Литеральный текст в `"..."` или ALL CAPS.
- Шрифт, размер, цвет, позиция — явно.
- Сложные слова и бренды: спеллинг по буквам.
- Защита от мусора: «**no extra words, no duplicate text, no watermarks**».
- Для нечитаемого мелкого текста: «**100 percent readable and physically believable**».
- Маленький/плотный/multi-font → `quality: high` обязательно.

## Editing — двухколоночная логика

Endpoint: `openai/gpt-image-2/edit` (на fal.ai) или соответствующий через OpenAI API.

```
Change: [single concrete change]
Preserve: face, identity, pose, lighting, framing, background, geometry, text, layout
Constraints: no extra objects, no redesign, no drift
```

**Правила edit:**
- **Один edit за итерацию.** Не пытайся менять всё разом.
- **Preserve list повторять каждую итерацию.** Иначе дрейф.
- **Surgical edits:** явно перечисли что НЕ трогать (saturation, contrast, layout, arrows, labels, camera angle).
- Опционально: `mask_image_url` для точечных edits.

### Edit-паттерны

**Virtual try-on:** «Change garments only. Preserve exact face, body shape, pose, hair, expression, background, camera angle. Match lighting/shadows so outfit looks naturally worn.»

**Object removal:** «Remove [X]. Do not change anything else. Use `input_fidelity: high` to maintain surrounding context» (только gpt-image-1.5/1, в gpt-image-2 high-fidelity по умолчанию).

**Lighting/weather swap:** «Change ONLY environmental conditions: lighting direction/quality, shadows, atmosphere, precipitation. Preserve identity, geometry, camera angle, object placement.»

**Interior swap:** «Swap [furniture]. Preserve camera angle, lighting, shadows, surrounding context. Photorealistic contact shadows.»

## Multi-Image — до 16 рефов

Индексируй с **ролью**, не только номером:
```
Image 1: base scene
Image 2: jacket reference (apply only the jacket fabric/cut to subject in Image 1)
Image 3: lighting reference (apply golden-hour quality from Image 3)
```

## Style Transfer

Не пиши абстрактно («minimalist», «editorial»). Назови конкретные визуальные свойства референса: палитра, edge treatment, силуэт, обработка теней, plane логика.

## World Knowledge

GPT Image 2 умеет домысливать контекст: «Bethel, NY, August 1969» → выведет Woodstock-эстетику. Используй: дай исторический/культурный анкер, не расписывай каждую деталь.

## Iteration Strategy

- Стартуй с **чистого** базового промпта.
- Один change за раунд. «Make lighting warmer», «remove extra tree», «restore original background».
- При drift — перечисли invariants заново.
- Для длинных промптов — labeled sections, не одна простыня.

## Use-Case Templates

### Photoreal Editorial
```
Scene: [location, time, weather]
Subject: [who, action, framing]
Important Details: [lens feel, light source, surface wear, imperfections, real texture]
Use Case: editorial photograph, looks like a real photo
Constraints: no glamorization, no heavy retouching, no studio gloss
```

### Product Mockup (Clean Background)
```
Scene: plain white opaque background
Subject: [product] centered
Important Details: crisp silhouette, no halos/fringing, light contact shadow,
  preserve label legibility exactly, preserve geometry
Use Case: product mockup
Constraints: no restyling, only background removal + light polish
```

### UI Mockup
```
Scene: [device frame, e.g. iPhone 15 Pro]
Subject: [screen/app name] — describe AS IF IT EXISTS, not concept art
Important Details: layout, hierarchy, real interface elements, exact copy in quotes,
  typography behavior, spacing, state
Use Case: shipped product screenshot
Constraints: no sketch language, no placeholder text, no Lorem Ipsum
Quality: high (for small UI text)
```

### Marketing Creative with Text
```
Scene: [environment]
Subject: [hero element]
Important Details: [composition, palette, mood]
Use Case: ad creative for [audience]
Text: "EXACT HEADLINE" in [font style], [color], [position]
      "exact subhead" in [font style], [color], [position]
Constraints: no extra text, no duplicate text, no watermarks, no unrelated logos
Quality: high
```

### Infographic / Diagram
```
Title: "[TITLE]"
Content flow: [step 1] → [step 2] → [step 3]
Visual format: [layout type — flowchart, pyramid, isometric, etc.]
Use Case: educational infographic for [audience]
Constraints: readable labels at all sizes, clear hierarchy, no clutter,
  no decorative noise, ample whitespace
Quality: high
Size: 1536×1024
```

## Migration from Older GPT-Image

- Промпты в основном переносятся как есть.
- После переноса — посмотри качество, latency, retry-rate; ретюнь.
- `gpt-image-1-mini` — только если главное снизить цену batch'а на низкорисковых задачах.
