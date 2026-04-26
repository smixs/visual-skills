# 🎨 Visual Skills для Claude — промпты для image и video

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet?style=flat-square)](https://docs.claude.com/en/docs/agents/agent-skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![image: Nano Banana + GPT Image 2](https://img.shields.io/badge/image-Nano_Banana_%2B_GPT_Image_2-ff69b4?style=flat-square)](#-image--что-делает)
[![video: Seedance + Kling + Veo](https://img.shields.io/badge/video-Seedance_%2B_Kling_%2B_Veo-orange?style=flat-square)](#-video--что-делает)

**🇬🇧 [Read in English](README.md)**

Два профессиональных Claude-скилла для production-генерации визуального AI-контента. Они пишут production-grade промпты под топовые image- и video-модели — выбирают правильную модель под задачу, применяют её специфичный синтаксис и возвращают готовый к копированию промпт.

Это то, чем пользуется креативный директор, копирайтер или команда AI-контента вместо «be cinematic, 4k, masterpiece» наполнителя.

---

## ✨ Поддерживаемые модели

### 🖼️ Image-модели

| Модель | Семейство | Для чего | Заметки |
|---|---|---|---|
| **Nano Banana 2** (Flash) | Google Gemini 3 Flash Image | Дефолтная рабочая лошадка, быстро и дёшево | ~$0.04/картинка |
| **Nano Banana Pro** | Google Gemini 3 Pro Image | Сложные многослойные сцены, до 14 референсов, image grounding (реальные места и виды) | ~$0.15/картинка |
| **GPT Image 2** | OpenAI | Brand-ассеты, плотный текст, UI-моки, edit с жёстким preservation, до 16 референсов | `quality: low / medium / high` |
| GPT Image 1.5 / 1 | OpenAI legacy | Только для миграции | — |
| GPT Image 1-mini | OpenAI | Дешёвые exploratory-батчи | — |

### 🎬 Video-модели

| Модель | Семейство | Для чего | Заметки |
|---|---|---|---|
| **Seedance 1.0 / 1.5 / 2.0 Pro** | ByteDance | Multi-shot в одном клипе, быстрый монтаж драмы, 1080p, до 12 секунд | `--resolution / --duration / --camerafixed`, `@img1` для лока персонажа |
| **Seedance Lite** | ByteDance | Дешёвая batch-генерация, 720p | — |
| **Kling 1.6 / 2.1 / 2.5 Turbo / 2.6 Pro** | Kuaishou | Преемственность персонажа через Element Binding, Motion Brush, Motion Transfer, social-вертикалки | Отдельное поле негативного промпта |
| **Kling 3.0** (pro / standard) | Kuaishou | Нативный multi-shot до 6 шотов в одной генерации, нативные диалоги + lip-sync, контроль тона голоса, 15 секунд непрерывного вывода, лейблы `[Character A: ...]` прямо в промпте | API эксклюзивно на fal.ai |
| **Veo 3 / Veo (flagship)** | Google | Нативные диалоги + lip-sync, синхронные SFX, JSON-промпты, рекламная полировка | До 8 секунд |
| Runway Gen-4, Luma Dream Machine, Pika 2, Sora | разное | Общая логика через universal rules | Без отдельного reference |

---

## 🤝 Совместимость

Это обычные Claude Skills — markdown-файлы плюс запакованный `.skill` архив. Работают в любом агенте или IDE, поддерживающем формат Claude Skill:

| Инструмент | Как подключить |
|---|---|
| **Claude Code** | Скопируй `image/` или `video/` в `~/.claude/skills/` (или `claude install image.skill`) |
| **Claude.ai Projects** | Загрузи папку-источник в knowledge base проекта |
| **Claude Agent SDK** | Подключи папку скилла в определении агента |
| **Cursor / Windsurf** | Скопируй папку-источник в project rules |
| **Cline / Roo Code** | То же — папку в контекст агента |
| **OpenCode / opencode-ai** | Добавь как skill в конфиг агента |
| **Hermes-agent** | Загрузи через skill loader агента |
| Любой LLM-агент со структурированным prompt-форматом | Работает — внутри обычный markdown, без vendor lock-in |

Скиллы работают с Claude Opus / Sonnet / Haiku, и плавно деградируют на GPT / Gemini / open-weights агентах (markdown model-agnostic).

---

## 📦 Что в репо

```
visual-skills/
├── image/              # Папка-источник image-скилла
├── image.skill         # Запакованный скилл — drop-in инсталлер
├── video/              # Папка-источник video-скилла
├── video.skill         # Запакованный скилл — drop-in инсталлер
├── README.md / README.ru.md
└── LICENSE             # MIT
```

---

## 🖼️ `image` — что делает

Пишет промпты для AI-генерации картинок. Выбирает Nano Banana или GPT Image 2 под задачу, применяет специфичный синтаксис модели, возвращает готовый к копированию промпт с заголовком (модель, quality, size).

**Покрываемые задачи:**

- 📰 Editorial-фотография, постеры, рекламные креативы
- 🛍️ Продуктовая съёмка, упаковка, моки
- 🖥️ UI-моки и продуктовые скриншоты
- 📊 Инфографика, диаграммы, слайды
- ✏️ Edit — try-on, смена света/погоды, удаление объектов, реставрация, локализация
- 👤 Преемственность персонажа между кадрами
- 🎞️ Сториборды, комиксы, последовательный нарратив
- 📐 Скетч → фото, wireframes, 2D → 3D, планы этажей

**Разделение по моделям:**

| Сигнал из задачи | Использовать |
|---|---|
| Реальное место / вид животного (image grounding) | Nano Banana |
| Экстремальные пропорции (1:8, 8:1, 4:1) | Nano Banana |
| Edit с жёстким preservation (try-on, swap) | GPT Image 2 |
| Мелкий плотный текст, multi-font, brand-ассеты | GPT Image 2 (`quality: high`) |
| UI-мок, продуктовый скриншот | GPT Image 2 |
| Дефолт, быстро/дёшево | Nano Banana 2 |

**Reference-файлы внутри `image/`:** `models.md`, `nano-banana.md`, `gpt-image.md`, `golden-rules.md`, `prompt-framework.md`, `creative-direction.md`, `text-rendering.md`, `editing.md`, `characters.md`, `slides.md`, `storyboards.md`, `structural.md`, `dimensional.md`.

---

## 🎬 `video` — что делает

Пишет промпты для AI-генерации видео. Работает как гибрид Режиссёр / Сценарист / Монтажёр — применяет кинематографическую драматургию (формула сцены, Murch Rule of Six, блокинг, staging) и специфичный синтаксис каждой модели (Seedance multi-shot, Kling Element Binding, Veo JSON / диалоги).

**Покрываемые задачи:**

- 🎯 Одиночные 5-секундные клипы и склеенные multi-clip истории (15с / 30с / 60с+)
- 🎞️ Режиссёрские treatment'ы и shot list'ы (14-польная карточка кадра)
- 📋 Раскадровки из сценария
- 🔧 Аудит чужих промптов («вот промпт, почини»)
- 📝 Перевод сценариев и сториборда в shot-by-shot промпты
- 🔗 Continuity между клипами (лок персонажа, wardrobe, логика света)
- 🎭 Жанровые паттерны: реклама, музыкальное видео, драма, экшн, fashion, UGC, продуктовая съёмка

**Разделение по моделям:**

| Сигнал из задачи | Использовать |
|---|---|
| Multi-shot в одной генерации, быстрый монтаж драмы, синтаксис «Cut to», без диалогов | Seedance |
| Multi-shot **с диалогами + lip-sync**, до 15 секунд, многоперсонажный voice control | **Kling 3.0** |
| Преемственность персонажа в social-клипах (без диалогов), Motion Brush, дешевле | Kling 2.6 Pro |
| Диалоги, lip-sync, синхронные SFX, полированная рекламная озвучка, JSON-промпты | Veo |

**Reference-файлы внутри `video/`:** `dramaturgy.md`, `universal-rules.md`, `seedance.md`, `kling.md`, `veo.md`, `role-modes.md`, `patterns-and-genres.md`, `camera-lighting-vocabulary.md`, `fixes-and-skeletons.md`.

---

## 🚀 Установка

### Вариант A — поставить запакованный `.skill`

Скачай `image.skill` и/или `video.skill` из репо и загрузи через свой Claude-клиент:

```bash
# Claude Code
claude install image.skill
claude install video.skill
```

### Вариант B — клонировать исходники

```bash
git clone https://github.com/smixs/visual-skills.git
```

Потом скопируй `image/` и/или `video/` в свою skills-директорию:

```bash
# Claude Code
cp -r visual-skills/image  ~/.claude/skills/
cp -r visual-skills/video  ~/.claude/skills/

# Cursor / Windsurf — папка project rules
cp -r visual-skills/image  .cursor/rules/
```

---

## 💡 Примеры использования

**Image — короткие промпты:**
> «Сделай промпт для постера офисной кружки с надписью BEST DAY EVER, фон #f5f5dc, 16:9»
>
> «Отредактируй этот продуктовый shot — поменяй фон на чистый белый, бутылку оставь как есть»

**Image — с явным указанием модели:**
> «Используй GPT Image 2 для UI-мока медитейшн-приложения в стиле Spotify, quality high»
>
> «Используй Nano Banana Pro — кинематографичная фотография Карлова моста в Праге в золотой час, архитектура должна быть точной»

**Video — одиночный промпт:**
> «Напиши промпт для Seedance — голодный мужик ночью находит последнюю сосиску в холодильнике, 5 секунд, мульти-шот»

**Video — полный разбор:**
> «Раскадруй 30-секундный ролик про чувство вины. Главная эмоция — guilt. Опорный объект — телефон с непрочитанным сообщением.»
>
> «Сделай аудит этого промпта: [...]. Что сломано, как починить?»
>
> «Переведи этот сценарий в 6 × 5-секундных промптов для Seedance.»

---

## Как это устроено (коротко)

Каждый `SKILL.md` — тонкий маршрутизатор. В теле сказано: «прежде чем выдать промпт, загрузи эти reference-файлы в этом порядке». Сами правила — специфичный синтаксис каждой модели, драматургия, Закон деталей, запрещённые слова, которые ломают модель — живут только в `references/`. Это вынуждает агента идти в references и спасает от ленивого generic-ответа.

Для video отдельно: каждый кадр обязан владеть тремя конкретными деталями — давление среды (холодный свет холодильника, мокрый асфальт, мерцающая лампа), физическое микро-действие (сжатая челюсть, побелевшие костяшки), и звуковой/визуальный мотив. Слова «cinematic», «epic», «stunning», «masterpiece» запрещены — они не рендерятся.

---

## Credits и источники

- **Nano Banana** — Google Gemini 3 Pro Image / Flash Image, промптинг через гайды fal.ai и Google AI Studio.
- **GPT Image 2** — OpenAI, через OpenAI developers cookbook и GPT Image 2 prompting guide на fal.ai.
- **Seedance** — ByteDance Seed, официальная документация Seedance 2.0.
- **Kling** — Kuaishou, официальная документация Kling.
- **Veo** — Google DeepMind, официальная документация Veo.
- **Видео-драматургия** — Walter Murch (*In the Blink of an Eye*, Rule of Six), Akira Kurosawa (среда как персонаж), David Fincher (мотивированная камера), Steven Spielberg (пространственная ясность), Jonathan Glazer (видеоклип как одна визуальная фраза), Bong Joon Ho (раскадровка после локаций).

## Лицензия

MIT — форкайте, адаптируйте, делайте визуальный контент лучше.

---

**Теги:** `claude` · `claude-skills` · `claude-code` · `claude-agent-sdk` · `prompt-engineering` · `ai-image-generation` · `ai-video-generation` · `nano-banana` · `gpt-image` · `gpt-image-2` · `seedance` · `kling` · `veo` · `creative-director` · `cursor` · `windsurf` · `cline` · `opencode` · `hermes-agent`
