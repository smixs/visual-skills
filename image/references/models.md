# Model Selection — Nano Banana vs GPT Image 2

Skill пишет промпты под две семьи моделей. Они мыслят по-разному — выбор модели меняет структуру промпта.

## TL;DR

| Задача | Модель |
|--------|--------|
| Реальное место/объект (с грунтингом) | **Nano Banana** (NB2/NBP) |
| Сложная сцена с физикой/композицией | **Nano Banana Pro** |
| Длинные горизонтальные/вертикальные форматы (1:8, 8:1, 4:1) | **Nano Banana** (только NB поддерживает экстрим) |
| Дешёвая массовая генерация | **Nano Banana 2** или **gpt-image-1-mini** |
| Фотореализм с тонкой типографикой/UI | **GPT Image 2** |
| Точное editing с preservation (try-on, swap, weather) | **GPT Image 2** (в editing у него лучшая identity-preservation) |
| Маленький плотный текст в кадре | **GPT Image 2** (`quality: high`) |
| Брендовая полиграфия / постеры с EXACT TEXT | **GPT Image 2** |
| Сториборды, комиксы (последовательность) | **Nano Banana** (extreme ratios + thinking) |
| Storyboard с фокусом на типографике | **GPT Image 2** |
| Style transfer без упоминаемых референс-картинок | **GPT Image 2** (concrete visual targets) |
| Рендер из 14+ референсов | **Nano Banana Pro** (до 14) или **GPT Image 2** (до 16) |

## Когда что выигрывает

### Nano Banana выигрывает в
- **Image grounding.** NB2 ищет реальные изображения в интернете перед генерацией — точная архитектура конкретного храма, моста, площади; конкретные виды животных, растений. GPT Image 2 этого не делает.
- **Экстремальные пропорции.** 1:8, 8:1, 1:4, 4:1 — баннеры, скроллы, комикс-стрипы. У GPT Image 2 max 3:1.
- **«Thinking» режим.** Сложные инфографики со spatial logic.
- **Цена/скорость.** NB2 = $0.04/img.

### GPT Image 2 выигрывает в
- **Identity preservation в edit.** Меняешь одежду / погоду / фон — лицо, поза, геометрия не плывут. Двухколоночная логика (change / preserve) работает как контракт.
- **Тонкий текст в кадре.** Маленькие подписи, легенды, footnotes, multi-font layouts. На `quality: high` рендерит чётче.
- **UI-моки и продуктовые скриншоты.** Иерархия, реальные интерфейс-элементы, читаемые лейблы.
- **Структурированный 5-slot промпт.** Чёткое разделение Scene/Subject/Details/Use case/Constraints даёт предсказуемость.
- **`quality` рычаг.** low/medium/high — осознанный trade-off скорости и точности.

### Где обе модели одинаково хороши
- Photorealistic портреты.
- Product shots на нейтральном фоне.
- Минималистичные постеры.
- Editorial-фотография.

## Различия в синтаксисе промпта

| Аспект | Nano Banana | GPT Image 2 |
|--------|-------------|-------------|
| Стиль промпта | Натуральный язык, 1-2 параграфа | 5-slot с лейблами секций |
| Камера/линза | **Не указывать** числа (50mm, f/2.8) — NB игнорит | Можно «50mm feel», но как high-level look |
| «Stunning/epic/masterpiece» | Игнорит, не вредит | **Anti-slop**: вредит, делает результат хуже |
| Text in image | `"..."` в кавычках, font + position | `"..."` или ALL CAPS + «no extra words / no duplicate text» |
| Negative framing | Использовать позитив | Использовать позитив + явный preserve list |
| Сложные сцены | JSON для 5+ элементов | 5-slot template со секциями |
| Edit | «Keep X same, change Y» | «Change: X / Preserve: Y / Constraints: Z» — повторять preserve каждую итерацию |
| Множественные референсы | До 14, индексировать | До 16, индексировать с ролью («Image 1: base», «Image 2: jacket reference») |

## Стоимость (ориентир)

| Модель | Цена | Заметки |
|--------|------|---------|
| Nano Banana 2 (Flash) | ~$0.04/img | Default для большинства задач |
| Nano Banana Pro | ~$0.15/img | Сложные сцены, до 14 рефов |
| GPT Image 2 (`low`) | дёшево | Latency-sensitive, превью |
| GPT Image 2 (`medium`) | средне | Default для GPT Image |
| GPT Image 2 (`high`) | дороже | Маленький текст, brand-sensitive, photorealism |
| gpt-image-1-mini | дешёвый | Высокообъёмная exploratory-генерация |

> Скилл сам не запускает генерацию — выдаёт промпт. Модель/quality указываем рядом с промптом как мета.
