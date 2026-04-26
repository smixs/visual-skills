# 🎨 Visual Skills for Claude

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet?style=flat-square)](https://docs.anthropic.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Skills: 2](https://img.shields.io/badge/Skills-2-orange?style=flat-square)](#whats-inside)

**🇷🇺 [Читать на русском](README.ru.md)**

Two production-grade Claude skills for prompt engineering against AI image and video generators. They don't generate media themselves — they write prompts so good the model can't fail. Each skill enforces the discipline that separates strong work from "cinematic masterpiece" filler: model-specific syntax, dramaturgy, concrete details over vague praise.

Built around one architectural rule: **SKILL.md is a router, not a process description.** The body of each skill is intentionally thin so the agent cannot fake a result by reading it alone — it must load the reference files in a mandatory order before producing output.

---

## Why This Exists

Most "image prompt" and "video prompt" libraries fail in the same way: they hand the model a paragraph of generic advice ("be specific, use cinematic lighting, add details") and expect a strong result. What actually happens — the model reads the advice, decides it has enough, and produces lazy, generic prompts that ignore the physics of each target generator.

These skills fix the failure mode at the architecture level:

- **Model-specific physics** — Nano Banana wants natural-language paragraphs and ignores `50mm/f-stop` numbers; GPT Image 2 wants a labeled 5-slot template and breaks on "stunning/epic/masterpiece" praise; Seedance multi-shot needs a `@img1` character lock and an explicit anti-mush guard. Each model has its own reference file.
- **Mandatory reading order** — `SKILL.md` does not contain the rules. It contains the order in which the rules must be loaded. This forces the agent into the references where the actual craft lives.
- **Dramaturgy + Details Law** — for video, the prompt is built from desire + obstacle + geometry + gaze + rhythm, with every shot owning environmental pressure + physical micro-action + sound or visual motif. Beautiful frame without dramaturgy is wallpaper.

---

## What's Inside

```
visual-skills/
├── image/                              # Source folder — Image prompting skill
│   ├── SKILL.md                        # Thin router with mandatory reading order
│   └── references/
│       ├── models.md                   # Pick: Nano Banana vs GPT Image 2
│       ├── nano-banana.md              # NB2 / NBP specifics
│       ├── gpt-image.md                # GPT Image 2 specifics (5-slot template, anti-slop)
│       ├── golden-rules.md             # Universal rules (verb start, positive framing, hex)
│       ├── prompt-framework.md         # Element checklist, detail modes
│       ├── creative-direction.md       # Lighting, camera, color, materiality
│       ├── text-rendering.md           # Text in image, infographics, diagrams
│       ├── editing.md                  # Object removal, lighting swap, colorization
│       ├── characters.md               # Character continuity across images
│       ├── slides.md                   # Presentation slides
│       ├── storyboards.md              # Sequential narrative
│       ├── structural.md               # Sketch → final, wireframes
│       └── dimensional.md              # 2D → 3D, floor plans, isometric
├── image.skill                         # Packaged skill (drop-in installer)
├── video/                              # Source folder — Video prompting skill
│   ├── SKILL.md                        # Thin router with mandatory reading order
│   └── references/
│       ├── dramaturgy.md               # Scene formula, Murch Rule of Six, Details Law
│       ├── universal-rules.md          # U1-U12 — applies to every video model
│       ├── seedance.md                 # Seedance 2.0 (production 11-block skeleton, @img1)
│       ├── kling.md                    # Kling (Element Binding, Motion Brush)
│       ├── veo.md                      # Veo (dialogue, lip-sync, JSON prompts)
│       ├── role-modes.md               # Director / Screenwriter / Editor
│       ├── patterns-and-genres.md      # Commercial, music video, drama, action
│       ├── camera-lighting-vocabulary.md
│       └── fixes-and-skeletons.md      # Continuity, multi-clip, common failures
└── video.skill                         # Packaged skill (drop-in installer)
```

---

## The Two Skills

### 🖼️ `image` — Image Prompting

Writes prompts for **Nano Banana** (Gemini 3 Pro / 3 Flash by ByteDance via Google) and **GPT Image 2** (OpenAI). The skill picks the right model for the task, applies its specific syntax, and returns a copy-paste-ready prompt with model + quality + size headers.

**What it covers:**
- Editorial photography, product shots, posters, ad creatives
- UI mockups and product screenshots
- Infographics, diagrams, slides
- Edits — try-on, lighting/weather swap, object removal, restoration, localization
- Character continuity across multiple images
- Storyboards, comics, sequential narrative

**Model split (the choice changes the syntax fundamentally):**

| Decision cue | Use |
|---|---|
| Real geographic place / animal species (image grounding) | Nano Banana |
| Extreme aspect ratio (1:8, 8:1, 4:1) | Nano Banana |
| Edit with hard preservation (try-on, swap, weather change) | GPT Image 2 |
| Small dense text, multi-font layouts, brand assets | GPT Image 2 (`quality: high`) |
| UI mockup / product screenshot | GPT Image 2 |
| Default, fast, cheap | Nano Banana 2 |

### 🎬 `video` — Video Prompting

Writes prompts for **Seedance** (ByteDance, multi-shot in one clip), **Kling** (Kuaishou, Element Binding for character lock), and **Veo** (Google, native dialogue and lip-sync). The skill operates as a hybrid Director / Screenwriter / Editor — and it refuses to produce a prompt without first running the dramaturgy check and the three-detail audit.

**What it covers:**
- Single-prompt clips and multi-clip stitched stories
- Director treatments
- Storyboards and shot lists (14-field shot card)
- Prompt audits ("here's my prompt, fix it")
- Translating scripts into shot-by-shot prompts
- Continuity across clips
- Genre patterns: commercial, music video, drama, action, fashion, UGC, product film

**Model split:**

| Decision cue | Use |
|---|---|
| Multi-shot in one generation, fast montage drama, "Cut to" syntax | Seedance |
| Character consistency across many social clips, Motion Brush | Kling |
| Dialogue, lip-sync, synchronized SFX, commercial polish with voiceover | Veo |

**The non-negotiable:** every shot owns three details — environmental pressure, physical micro-action, and a sound or visual motif. Words like "stunning", "epic", "cinematic", "masterpiece" don't render — they mark the writer being lazy. The skill audits every shot against this rule before sending the prompt.

---

## Installation

### Option A — Drop the `.skill` archive

```bash
# image skill
claude install image.skill

# video skill
claude install video.skill
```

Or download `image.skill` / `video.skill` from this repo and load them through your Claude client.

### Option B — Clone the source folders

```bash
git clone https://github.com/smixs/visual-skills.git
```

Then copy `image/` and/or `video/` into your skills directory (`~/.claude/skills/` for Claude Code, or your project's skill folder).

The skills work with any agent that supports Claude Skill format — Claude Code, Claude Projects, Cursor, Windsurf. Source is plain markdown — no platform lock-in.

---

## Usage Examples

### Image — quick prompts

> "Сделай промпт для постера офисной кружки с надписью BEST DAY EVER, фон #f5f5dc, 16:9"

> "Edit this product shot — change the background to plain white, keep the bottle exactly as is"

> "Need a blog cover. Topic: AI agents replacing analysts. Style — minimalist editorial."

### Image — model-aware

> "Use GPT Image 2 to mock up a Spotify-like UI for a meditation app, quality high"

> "Use Nano Banana Pro — generate a cinematic photograph of the Charles Bridge in Prague at golden hour, must be architecturally accurate"

### Video — single prompt

> "Напиши промпт для Seedance — голодный мужик ночью находит последнюю сосиску в холодильнике, 5 секунд, мульти-шот"

### Video — full breakdown

> "Раскадруй 30-секундный ролик про чувство вины. Главная эмоция — guilt. Опорный объект — телефон с непрочитанным сообщением."

> "Audit this prompt: [...]. What's broken, how to fix?"

> "Translate this script into 6 × 5-second Seedance prompts."

---

## Architectural Notes

### SKILL.md is a router, not a process description

Both `SKILL.md` files are intentionally short (~90-100 lines). They contain:

1. Frontmatter with triggers
2. A 2-4 line identity paragraph
3. **Mandatory reading order** — numbered steps with wikilinks to reference files, one short line per file
4. Output format
5. Final response style (prefer / avoid)

That's it. No rules, no examples, no decision trees longer than a 3-row table. The actual craft lives only in `references/`.

**Why:** when SKILL.md contains the process, the agent reads the body, decides "I know what to do", and skips the references. The result is lazy, generic prompts. Forcing the agent into specific files via a "DO NOT WRITE A PROMPT WITHOUT THIS" loading sequence fixes this empirically.

### Progressive disclosure with hard ordering

Anthropic's Skills documentation calls this *progressive disclosure*: metadata (always loaded) → SKILL.md body (loaded on trigger) → references (loaded on demand). These skills push that pattern further by **mandating an order** — the model file must be loaded before universal rules, dramaturgy must be loaded before any model file, the three-detail check runs after both. The agent isn't free to skip steps.

### One core law per skill

- **Image:** *the model file is non-negotiable.* Nano Banana and GPT Image 2 reward different syntax. Skipping the model file is the single biggest cause of weak prompts.
- **Video:** *details intensify emotion, laziness kills the prompt.* The dramaturgy can be perfect, but one thin shot drags the whole sequence into mush. Every shot is audited against the three-detail rule before sending.

---

## Credits

- **Image guidelines** — Nano Banana via Google's official cookbook and ByteDance's Seedance guides on fal.ai; GPT Image 2 via OpenAI's developers cookbook and fal.ai's GPT Image 2 prompting guide.
- **Video dramaturgy** — Walter Murch (*In the Blink of an Eye*, Rule of Six), Akira Kurosawa (environment as character), David Fincher (motivated camera), Steven Spielberg (spatial clarity), Jonathan Glazer (one-sentence music video), Bong Joon Ho (post-location storyboarding).
- **Model references** — ByteDance Seedance 2.0 docs, Kuaishou Kling docs, Google Veo docs.

## License

MIT — fork it, adapt it, ship better prompts.
