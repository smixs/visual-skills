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
