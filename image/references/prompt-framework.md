# Prompt Framework

Универсальный чеклист для построения промпта. Применим к **обеим** семьям моделей. Для отличий смотри:
- [nano-banana.md](nano-banana.md) — NB-специфика (grounding, extreme ratios, thinking mode, JSON)
- [gpt-image.md](gpt-image.md) — GPT Image 2 (5-slot template, anti-slop, quality settings)
- [models.md](models.md) — какую модель когда выбрать

## Task Types (Навыки)

Определи тип задачи - это задаёт стратегию промпта:

| Type | Когда использовать | Ключевые элементы |
|------|-------------------|-------------------|
| **Photorealistic** | Фото людей, продуктов, сцен | Освещение, материалы, атмосфера |
| **Illustration** | Стикеры, иконки, арт | Стиль, контуры, палитра |
| **Product/Commercial** | Продуктовая съёмка | Поверхность, отражения, композиция |
| **Minimalist** | Негативное пространство | Что убрать важнее чем что добавить |
| **Sequential** | Комиксы, сториборды | Панели, переходы, нарратив |
| **Editing** | Изменение существующего | Конкретные инструкции что менять |
| **Style Transfer** | Перенос стиля | Референс + новый контент |
| **Composite** | Объединение элементов | Связность, освещение, масштаб |
| **Text Rendering** | Текст в изображении | Точные кавычки, позиция, вес |

## Universal Elements (Чеклист)

Пройдись по списку - не всё нужно указывать, но полезно проверить:

**Обязательные:**
- **Субъект** - кто/что в центре внимания
- **Контекст** - для чего это (определяет стиль)

**По ситуации:**
- **Действие** - что происходит
- **Окружение** - где это происходит
- **Камера** - крупность плана (close-up, wide shot, etc.)
- **Освещение** - тип света
- **Настроение** - эмоция сцены
- **Материалы** - текстуры поверхностей
- **Палитра** - цвета (лучше hex)
- **Формат** - соотношение сторон

> ⚠️ **Параметры объектива** (50mm, 85mm, f/2.8, ISO):
> - **Nano Banana** — игнорит числа, пиши описательно («shallow depth of field»)
> - **GPT Image 2** — допускает «50mm feel» как high-level look, но не как точную физическую симуляцию

## Detail Modes (Режимы)

**Concise** - одно предложение, для быстрых итераций:
```
Minimalist poster: white background, single red apple, centered, dramatic shadow.
```

**Standard** - 1-2 параграфа, баланс контроля и гибкости:
```
Create a product shot for premium headphones marketing.

Matte black headphones on dark slate surface. Single spotlight from upper left creates dramatic shadow. Background gradient from #1a1a1a to pure black.

Format: 16:9
```

**Verbose** - максимум деталей для сложных сцен:
```
Create a cinematic wide shot for sci-fi film concept art.

Setting: Abandoned space station observation deck. Massive curved window spans entire wall, revealing dying red giant star filling half the frame. Station interior in deep shadow except where crimson light bleeds through.

Subject: Lone astronaut in weathered EVA suit, helmet off, sitting on debris pile. Back to camera, facing the star. Pose suggests exhaustion and acceptance.

Atmosphere: Dust particles float in zero-g, catching red light. Abandoned equipment scattered - coffee cup frozen mid-float, papers suspended. Frost crystals on interior surfaces where life support failed.

Mood: Melancholic beauty, end of an era
Lighting: Volumetric god rays from star through window
Format: 2.39:1 cinemascope
```

## Output Structure

При создании промпта выдавай:

**1. Prompt** - готовый к использованию

**2. Parameters** - если нестандартные:
- Aspect ratio (если не 1:1)
- Resolution (если нужно 2K/4K)

**3. Exclusions** - что исключить (опционально):
> Формулируй позитивно! NBP лучше понимает "clean background" чем "no clutter"

**4. Assumptions** - что додумано, если пользователь не указал

## Quick Decision Tree

```
Что создаём?
├── Фото реального объекта/человека → Photorealistic
├── Рисунок/арт → Illustration  
├── Товар для продажи → Product/Commercial
├── Много пустого места → Minimalist
├── Несколько кадров/история → Sequential
├── Меняем существующее фото → Editing
├── "Как на этой картинке" → Style Transfer
├── Собираем из нескольких элементов → Composite
└── Текст - главный элемент → Text Rendering
```

> Image grounding (поиск реальных мест в интернете) и экстремальные ratio (1:8, 8:1, 4:1) — только Nano Banana. См. [nano-banana.md](nano-banana.md).

## Examples by Type

### Photorealistic
```
Portrait of a weathered fisherman, 60s, deep wrinkles and sun-damaged skin.
Early morning golden hour on wooden dock.
Holding fresh catch, genuine smile of satisfaction.
Background: misty harbor, fishing boats soft focus.
Mood: authentic, documentary style
```

### Product/Commercial
```
Product shot: luxury watch on raw concrete slab.
Single hard light from upper right, creating defined shadow.
Watch face at 10:10 position, metal bracelet draped naturally.
Background: gradient gray, vignette edges.
Style: high-end catalog, editorial
Format: 4:5
```

### Minimalist
```
Single origami crane, red paper, centered.
Pure white infinite background.
Soft diffused light, barely visible shadow.
Extreme negative space - crane occupies <10% of frame.
Format: 1:1
```

### Text Rendering
```
Motivational poster for gym.

Background: dark textured concrete, subtle vignette.

Text:
"DISCIPLINE" in extra bold, white, centered upper third
"beats talent" in thin weight, #808080, centered below

Small icon: minimal dumbbell silhouette, bottom center
Format: 9:16 (stories)
```

## Parameterized Templates

Паттерн `{variable}` для переиспользуемых промптов. Структура промпта остаётся стабильной — меняется только то, что нужно.

### Синтаксис

Переменные записываются как `{name, default="value"}`. Если значение не указано — используется дефолт. Если дефолта нет — переменная обязательна.

### Шаблон

```
Scene: {location, default="small Lisbon florist storefront at blue hour"}
Subject: {person, default="woman in navy apron"} {action, default="locking the front door"}
Important Details: {lighting}, {lens_feel, default="50mm feel"}, {key_texture}
Use Case: {use_case, default="editorial photography"}
Constraints: {constraints, default="no extra signage, no people in background"}
```

### Как использовать

1. **Заменяй только то, что меняется** — остальное берётся из дефолтов
2. **Структура стабильна** — порядок слотов одинаковый для всех вариаций, модель получает консистентный формат
3. **Batch-генерация** — идеально для серий: продуктовые ракурсы, позы персонажа, локации в одном стиле

### Примеры использования

**Серия продуктовых шотов** (меняется только товар и текстура):
```
Scene: {location, default="marble kitchen counter, morning light"}
Subject: {product} on {surface, default="raw linen cloth"}
Important Details: {lighting, default="soft window light from left"}, {lens_feel, default="85mm feel"}, {key_texture}
Use Case: {use_case, default="e-commerce hero shot"}
Constraints: {constraints, default="clean background, no props except surface"}
```

**Серия персонажных поз** (меняется действие и настроение):
```
Scene: {location, default="industrial loft studio"}
Subject: {person, default="man in black turtleneck"} {action}
Important Details: {lighting, default="single softbox, camera right"}, {lens_feel, default="50mm feel"}, {key_texture, default="fabric texture visible"}
Use Case: {use_case, default="fashion editorial"}
Constraints: {constraints, default="no visible logos, neutral expression"}
```

## Cinematic Verbose Mode

Стандартный verbose — 5-7 строк. **Cinematic verbose** — уровень выше, для случаев когда нужен максимум детализации: hero shots, ключевые визуалы, campaign centerpieces.

### Когда использовать

- Финальный визуал кампании, а не итерация
- Hero shot для лендинга или обложки
- Key visual, который будет масштабироваться на все форматы
- Портфолийная работа, где каждый пиксель имеет значение

### Чеклист микро-деталей

Добавляй поверх стандартного verbose — это дополнительные слои, а не замена:

1. **Surface wear & aging** — "chipped paint on window frame, hairline scratches on metal surface, green patina on copper fittings, oxidation marks on iron hinges"
2. **Micro-textures** — "visible pores on skin, individual hair strands catching backlight, fabric weave pattern on linen shirt, grain of weathered wood"
3. **Atmospheric particles** — "dust motes suspended in light beam, steam wisps rising from coffee cup, pollen floating in golden hour air, fine rain droplets on glass surface"
4. **Specular behavior** — "specular highlights on metal edges of watch, caustic reflections dancing inside glass bottle, wet surface sheen on cobblestones after rain"
5. **Fabric & material drape** — "natural fabric folds at elbow crease, gravity pull on loose linen garment, weight distribution visible in heavy wool coat"
6. **Contact shadows** — "soft contact shadow where cup meets saucer, ambient occlusion in crevices of stone wall, dark line where book spine meets table"
7. **Environmental reflections** — "building reflections in wet pavement, sky gradient in chrome bumper surface, warm neon glow on skin from nearby sign"
8. **Motion cues** — "slight motion blur on trailing hair strand, frozen splash droplet from espresso pour, wind-displaced fabric edge of scarf"

### Before / After

**Standard Verbose:**
```
Create a cinematic portrait for coffee brand campaign.

Setting: Small Italian café, early morning. Espresso machine prominent in background.
Subject: Barista in white shirt, mid-pour, focused expression.
Atmosphere: Steam rising, warm tones, golden morning light through window.
Mood: Craftsmanship, ritual, quiet dedication
Lighting: Warm directional light from left window
Format: 4:5
```

**Cinematic Verbose:**
```
Create a cinematic portrait for coffee brand campaign.

Setting: Small Italian café, early morning. Brass-and-chrome La Marzocca espresso machine in background, oxidation marks on steam wand, hairline scratches on drip tray from years of use. Chipped paint on wooden window frame behind machine.

Subject: Barista in white linen shirt — fabric weave pattern visible, natural folds at rolled-up sleeves, gravity pull on loose collar. Mid-pour with focused expression, visible pores on forehead, individual eyebrow hairs catching backlight.

Atmosphere: Steam wisps rising from espresso cup, dust motes suspended in morning light beam cutting through window. Fine coffee grounds scattered on worn marble counter — soft contact shadow where cup meets saucer. Wet surface sheen on freshly wiped counter edge.

Details: Specular highlights on chrome portafilter handle. Caustic reflections dancing inside glass water carafe on shelf. Warm neon glow of "APERTO" sign reflecting on barista's forearm. Slight motion blur on trailing steam, frozen droplet mid-drip from group head.

Mood: Craftsmanship, ritual, quiet dedication
Lighting: Warm directional light from left window, volumetric through steam
Format: 4:5
```
