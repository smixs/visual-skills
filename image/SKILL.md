---
name: image
description: >
  Image prompting skill — пишет готовые промпты для двух семей моделей: Nano Banana
  (NBP / NB2, Gemini 3 Pro / Flash) и GPT Image 2 (OpenAI). Skill сам не запускает
  генерацию, только формирует промпт и помечает рекомендуемую модель / quality / size.
  Use when пользователь говорит "нарисуй", "сгенерируй картинку", "сделай изображение",
  "напиши промпт для image gen", запрашивает blog covers, slides, инфографику, постер,
  product shot, UI mockup, storyboard, comic, character sheet, edit/colorize, virtual
  try-on, style transfer. Triggers: "image prompt", "промпт для картинки", nb, nano banana,
  NBP, NB2, gpt-image, gpt image 2, gpt-image-2, "AI image".
  Do NOT use for: video (use video skill), 3D models, audio, non-image tasks.
---

# Image Prompting — Nano Banana & GPT Image 2

This skill writes image prompts. It does not generate images. The output is: model name + quality / size / aspect ratio + the prompt itself.

The body of this SKILL.md is intentionally thin so you cannot fake a result by reading it alone. The actual rules — what the models reward, what they punish, how to phrase a 5-slot template, when to add `quality: high`, when to use image grounding — live only in the reference files.

---

# Mandatory reading order — DO NOT WRITE A PROMPT WITHOUT THIS

Past attempts to write prompts directly from this skill body produced lazy, generic results. Each model has its own physics; common rules collapse into mush when applied without model-specific syntax. Read in this order before producing any prompt:

### Step 1 — always read first → [models.md](references/models.md)

Decide: Nano Banana (NB2 or NBP) or GPT Image 2. The choice changes the prompt syntax fundamentally — natural-language paragraphs vs. labeled 5-slot template, quality settings, which features exist (image grounding only on NB, EXACT TEXT discipline only on GPT Image, etc.).

If the user named a model — confirm and proceed. If not — pick using the table in `models.md`, then state your choice in the output header.

### Step 2 — read **one** model file (the one you picked)

- **Nano Banana** → [nano-banana.md](references/nano-banana.md)
  Image grounding for real locations. Extreme aspect ratios (1:8, 8:1, 4:1). Thinking mode. JSON for 5+ elements. Up to 14 reference images. Why you must NOT write `50mm / f-stop / ISO` numbers.

- **GPT Image 2** → [gpt-image.md](references/gpt-image.md)
  5-slot template (Scene / Subject / Important Details / Use Case / Constraints). Anti-slop banned-words list. `quality: low / medium / high` as a deliberate fidelity lever. Size constraints (multiples of 16, max 3:1, up to 2560×1440). Two-column edit logic (Change / Preserve / Constraints). Up to 16 reference images with explicit roles.

The model file is non-negotiable. Skipping it is the single biggest cause of weak prompts.

### Step 3 — always read after the model file → [golden-rules.md](references/golden-rules.md)

Universal rules that apply to both models: start with a verb, positive framing, hex colors, quote text, edit don't re-roll, one change per iteration, reference images.

### Step 4 — task-shaped reading (load only what matches the request)

Pick zero or more, depending on what the user asked for:

- Text in image, infographic, diagram, multilingual rendering → [text-rendering.md](references/text-rendering.md)
- Edit existing image (object removal, lighting swap, colorization, restoration, localization) → [editing.md](references/editing.md)
- Character continuity across multiple images / panels → [characters.md](references/characters.md)
- Presentation slides → [slides.md](references/slides.md)
- Sequential narrative (storyboard, comic, panel sequence) → [storyboards.md](references/storyboards.md)
- Sketch → final, wireframes, structural input → [structural.md](references/structural.md)
- 2D → 3D, floor plans, isometric → [dimensional.md](references/dimensional.md)

### Step 5 — read for production language → [creative-direction.md](references/creative-direction.md)

Studio-quality vocabulary for lighting design, camera and hardware, color grading and film stock, materiality and texture. Read when you need precise terms beyond what `golden-rules.md` covers.

### Step 6 — read if structuring a complex prompt → [prompt-framework.md](references/prompt-framework.md)

Universal element checklist (subject, context, action, environment, camera, lighting, mood, materials, palette, format), detail modes (concise / standard / verbose), output structure with parameters and exclusions.

---

# Output format

When you return the prompt, structure it like this:

```
Model: <nano-banana-2 | nano-banana-pro | gpt-image-2>
Quality: <low | medium | high>          (only for gpt-image-2)
Size / Ratio: <e.g. 1536×1024 or 16:9>

Prompt:
<the prompt text, ready to copy>

Notes:
- <anything you inferred or assumed because the user did not specify>
```

For edits, also include an explicit preserve-list (mandatory for gpt-image-2, recommended for nano-banana):

```
Change: <one concrete thing>
Preserve: <face, pose, lighting, framing, geometry, ...>
Constraints: <no extra objects, no drift, ...>
```

---

# Final response style

Prefer: ready-to-copy prompts, hex colors, concrete materials, named compositions, model-specific syntax (5-slot for GPT Image, natural prose for Nano Banana).

Avoid: tag soup ("cool, modern, 4k"), vague praise ("stunning, epic, masterpiece" — actively hurts GPT Image 2), negative framing ("no people, no cars" — invert to positive), external comparisons ("like Apple ad" — describe the visual properties instead), numerical lens parameters in Nano Banana prompts (it ignores them).
