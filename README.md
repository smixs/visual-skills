# 🎨 Visual Skills for Claude — Image & Video Prompting

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet?style=flat-square)](https://docs.claude.com/en/docs/agents/agent-skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![image: Nano Banana + GPT Image 2](https://img.shields.io/badge/image-Nano_Banana_%2B_GPT_Image_2-ff69b4?style=flat-square)](#-image--what-it-does)
[![video: Seedance + Kling + Veo](https://img.shields.io/badge/video-Seedance_%2B_Kling_%2B_Veo-orange?style=flat-square)](#-video--what-it-does)

**🇷🇺 [Читать на русском](README.ru.md)**

Two professional Claude Skills for AI visual content production. They write production-grade prompts for the leading image and video models — picking the right model for the task, applying its specific syntax, and returning a copy-paste-ready prompt.

This is what a creative director, copywriter, or AI-content team uses instead of "be cinematic, 4k, masterpiece" filler.

---

## ✨ Supported Models

### 🖼️ Image generation models

| Model | Family | Best for | Notes |
|---|---|---|---|
| **Nano Banana 2** (Flash) | Google Gemini 3 Flash Image | Default workhorse, fast & cheap | ~$0.04/image |
| **Nano Banana Pro** | Google Gemini 3 Pro Image | Complex multi-layered scenes, up to 14 reference images, image grounding (real places/species) | ~$0.15/image |
| **GPT Image 2** | OpenAI | Brand assets, dense text, UI mockups, edits with hard preservation, up to 16 references | `quality: low / medium / high` |
| GPT Image 1.5 / 1 | OpenAI legacy | Migration path only | — |
| GPT Image 1-mini | OpenAI | Cheap exploratory batches | — |

### 🎬 Video generation models

| Model | Family | Best for | Notes |
|---|---|---|---|
| **Seedance 1.0 / 1.5 / 2.0 Pro** | ByteDance | Multi-shot in one clip (unique), fast montage drama, 1080p, up to 12s | `--resolution / --duration / --camerafixed` |
| **Seedance Lite** | ByteDance | Cheaper batch generation, 720p | — |
| **Kling 1.5 / 2.0 / 2.6** | Kuaishou | Character consistency (Element Binding), Motion Brush, Motion Transfer, social verticals | Dedicated negative prompt field |
| **Veo 3 / Veo (flagship)** | Google | Native dialogue + lip-sync, synchronized SFX, JSON prompts, commercial polish | Up to 8s |
| Runway Gen-4, Luma Dream Machine, Pika 2, Sora | misc | Generic guidance via universal rules | No dedicated reference yet |

---

## 🤝 Compatible With

These are plain Claude Skills — markdown files plus a packaged `.skill` archive. They work in any agent or IDE that supports the Claude Skill format:

| Tool | How |
|---|---|
| **Claude Code** | Drop `image/` or `video/` into `~/.claude/skills/` (or run `claude install image.skill`) |
| **Claude.ai Projects** | Upload the source folder to your project's knowledge base |
| **Claude Agent SDK** | Reference the skill folder in your agent definition |
| **Cursor / Windsurf** | Copy the source folder into your project rules |
| **Cline / Roo Code** | Same — drop the folder into the agent's context |
| **OpenCode / opencode-ai** | Add as a skill in the agent config |
| **Hermes-agent** | Load via the agent's skill loader |
| Any LLM agent with structured prompt support | Works — content is plain markdown, no platform lock-in |

The skills work with Claude Opus, Sonnet, Haiku, and degrade gracefully on GPT / Gemini / open-weights agents (the markdown is model-agnostic).

---

## 📦 What's in the Repo

```
visual-skills/
├── image/              # Source folder for the image-prompting skill
├── image.skill         # Packaged skill — drop-in installer
├── video/              # Source folder for the video-prompting skill
├── video.skill         # Packaged skill — drop-in installer
├── README.md / README.ru.md
└── LICENSE             # MIT
```

---

## 🖼️ `image` — What It Does

Writes prompts for AI image generation. Picks Nano Banana or GPT Image 2 based on the task, applies the model's specific syntax, returns a copy-paste-ready prompt with a header (model, quality, size).

**Tasks covered:**

- 📰 Editorial photography, posters, ad creatives
- 🛍️ Product shots, packaging, mockups
- 🖥️ UI mockups and product screenshots
- 📊 Infographics, diagrams, slides
- ✏️ Edits — try-on, lighting/weather swap, object removal, restoration, localization
- 👤 Character continuity across multiple images
- 🎞️ Storyboards, comics, sequential narrative
- 📐 Sketch-to-photo, wireframes, 2D-to-3D, floor plans

**Model split:**

| Decision cue | Use |
|---|---|
| Real place / species (image grounding) | Nano Banana |
| Extreme aspect ratios (1:8, 8:1, 4:1) | Nano Banana |
| Edit with hard preservation (try-on, swap) | GPT Image 2 |
| Small dense text, multi-font, brand assets | GPT Image 2 (`quality: high`) |
| UI mockup, product screenshot | GPT Image 2 |
| Default fast/cheap | Nano Banana 2 |

**Reference files inside `image/`:** `models.md`, `nano-banana.md`, `gpt-image.md`, `golden-rules.md`, `prompt-framework.md`, `creative-direction.md`, `text-rendering.md`, `editing.md`, `characters.md`, `slides.md`, `storyboards.md`, `structural.md`, `dimensional.md`.

---

## 🎬 `video` — What It Does

Writes prompts for AI video generation. Operates as a hybrid Director / Screenwriter / Editor — applies cinematic dramaturgy (scene formula, Murch Rule of Six, blocking, staging) and the model-specific syntax (Seedance multi-shot, Kling Element Binding, Veo JSON / dialogue).

**Tasks covered:**

- 🎯 Single 5-second clips and stitched multi-clip stories (15s / 30s / 60s+)
- 🎞️ Director treatments and shot lists (14-field shot card)
- 📋 Storyboards from script
- 🔧 Prompt audits ("here's my prompt, fix it")
- 📝 Translating scripts and storylines into shot-by-shot prompts
- 🔗 Continuity across clips (character lock, wardrobe, lighting logic)
- 🎭 Genre patterns: commercial, music video, drama, action, fashion, UGC, product film

**Model split:**

| Decision cue | Use |
|---|---|
| Multi-shot in one clip, fast montage drama, "Cut to" syntax | Seedance |
| Character consistency across many social clips, Motion Brush | Kling |
| Dialogue, lip-sync, synchronized SFX, voiceover commercial | Veo |

**Reference files inside `video/`:** `dramaturgy.md`, `universal-rules.md`, `seedance.md`, `kling.md`, `veo.md`, `role-modes.md`, `patterns-and-genres.md`, `camera-lighting-vocabulary.md`, `fixes-and-skeletons.md`.

---

## 🚀 Installation

### Option A — Install the packaged `.skill`

Download `image.skill` and/or `video.skill` from this repo and load through your Claude client:

```bash
# Claude Code
claude install image.skill
claude install video.skill
```

### Option B — Clone the source

```bash
git clone https://github.com/smixs/visual-skills.git
```

Then copy the `image/` and/or `video/` folders into your skills directory:

```bash
# Claude Code
cp -r visual-skills/image  ~/.claude/skills/
cp -r visual-skills/video  ~/.claude/skills/

# Cursor / Windsurf — copy into your project's rules folder
cp -r visual-skills/image  .cursor/rules/
```

---

## 💡 Usage Examples

**Image — quick prompts:**
> "Сделай промпт для постера офисной кружки с надписью BEST DAY EVER, фон #f5f5dc, 16:9"
>
> "Edit this product shot — change the background to plain white, keep the bottle exactly as is"

**Image — model-aware:**
> "Use GPT Image 2 to mock up a Spotify-like UI for a meditation app, quality high"
>
> "Use Nano Banana Pro — cinematic photograph of the Charles Bridge in Prague at golden hour, must be architecturally accurate"

**Video — single prompt:**
> "Напиши промпт для Seedance — голодный мужик ночью находит последнюю сосиску в холодильнике, 5 секунд, мульти-шот"

**Video — full breakdown:**
> "Раскадруй 30-секундный ролик про чувство вины. Главная эмоция — guilt. Опорный объект — телефон с непрочитанным сообщением."
>
> "Audit this prompt: [...]. What's broken, how to fix?"
>
> "Translate this script into 6 × 5-second Seedance prompts."

---

## How It Works (short)

Each `SKILL.md` is a thin router. The body says "before producing any prompt, load these reference files in this exact order". The actual rules — model-specific syntax, dramaturgy, the Details Law, banned phrases that hurt the model — live only in `references/`. This forces the agent into the references and prevents lazy generic output.

For video specifically, every shot must own three concrete details: environmental pressure (cold refrigerator light, wet asphalt, flickering fluorescent), physical micro-action (jaw locks, knuckles whiten), and a sound or visual motif. Words like "cinematic", "epic", "stunning", "masterpiece" are banned — they don't render.

---

## Credits & Sources

- **Nano Banana** — Google Gemini 3 Pro Image / Flash Image, prompting via fal.ai and Google AI Studio guides.
- **GPT Image 2** — OpenAI, via OpenAI's developers cookbook and fal.ai's GPT Image 2 prompting guide.
- **Seedance** — ByteDance Seed, official Seedance 2.0 docs.
- **Kling** — Kuaishou, official Kling docs.
- **Veo** — Google DeepMind, official Veo docs.
- **Video dramaturgy** — Walter Murch (*In the Blink of an Eye*, Rule of Six), Akira Kurosawa (environment as character), David Fincher (motivated camera), Steven Spielberg (spatial clarity), Jonathan Glazer (one-sentence music video), Bong Joon Ho (storyboarding after locations).

## License

MIT — fork it, adapt it, ship better visual content.

---

**Tags:** `claude` · `claude-skills` · `claude-code` · `claude-agent-sdk` · `prompt-engineering` · `ai-image-generation` · `ai-video-generation` · `nano-banana` · `gpt-image` · `gpt-image-2` · `seedance` · `kling` · `veo` · `creative-director` · `cursor` · `windsurf` · `cline` · `opencode` · `hermes-agent`
