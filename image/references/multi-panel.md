# Multi-Panel Compositions

Single-image layouts containing multiple frames, panels, or grid cells. Unlike [storyboards.md](storyboards.md) (sequential images generated one-at-a-time), these patterns produce **one image** with all panels baked in.

Core principle: explicitly number and describe every panel. Models need panel-by-panel instructions — vague requests like "show multiple angles" produce inconsistent grids.

---

## 1. 9-Cell Grid Storyboard

> For a product-focused narrative variant, see [patterns/ecommerce.md](patterns/ecommerce.md#9-panel-tvc-storyboard-grid).

**When to use:** TVC or commercial shot breakdown — one image = 9 panels with scene titles and timestamps.

### Template (5-slot format)

```
Scene: Dark storyboard layout — 3x3 grid of cinematic frames for a {duration}-second {product_name} commercial. Each cell has a thin dark border. Below each cell: scene number, title, and timestamp in small white sans-serif text on dark background.

Subject: {product_name} commercial storyboard showing the complete narrative arc across 9 panels.

Important Details:
Panel 1 (0:00–{t1}): {scene_1_description}
Panel 2 ({t1}–{t2}): {scene_2_description}
Panel 3 ({t2}–{t3}): {scene_3_description}
Panel 4 ({t3}–{t4}): {scene_4_description}
Panel 5 ({t4}–{t5}): {scene_5_description}
Panel 6 ({t5}–{t6}): {scene_6_description}
Panel 7 ({t6}–{t7}): {scene_7_description}
Panel 8 ({t7}–{t8}): {scene_8_description}
Panel 9 ({t8}–{duration}): {scene_9_description}

Each panel labeled below: "Scene {N}: {title}" and "{start}–{end}"

Use Case: Pre-production storyboard for video production team
Constraints: All 9 panels must be clearly separated, no merged cells, every panel must contain distinct content, timestamps must be legible, {language} titles
```

**Variables:**
- `{product_name}` — brand/product
- `{duration}` — total spot length (e.g., "30", "60")
- `{t1}` through `{t8}` — timestamp boundaries
- `{scene_1_description}` through `{scene_9_description}` — shot description per panel
- `{language}` — "Chinese" / "English" / "bilingual"

**Recommended size:** 1536x1024 (landscape)
**Model:** GPT Image 2 `quality: high` (text-heavy — timestamps and titles need legibility)
**Common pitfalls:**
- Omitting panel numbers causes the model to merge or skip panels
- Vague scene descriptions produce near-identical panels — each must have a distinct action, angle, or subject
- Timestamps in very small text need `quality: high` to remain readable

---

## 2. 2x2 Editorial Portrait Grid

**When to use:** Same person shown from 4 angles/crops in one image for an editorial or casting look.

### Template (5-slot format)

```
Scene: 2x2 grid of four editorial portraits, minimal gap between panels. {background_description}. {lighting_style}.

Subject: {subject_description} — same person in all four panels, consistent identity and wardrobe.

Important Details:
Top-left: front-facing portrait, direct eye contact, shoulders up
Top-right: extreme macro close-up of face — eyes, skin texture, freckles visible
Bottom-left: lower angle looking up, chin slightly raised, confident expression
Bottom-right: side profile, clean silhouette against background

Consistent lighting across all four panels. Skin texture realistic, no airbrushing.

Use Case: editorial photography, model portfolio, casting composite
Constraints: same person in every panel, no wardrobe changes between panels, no extra people, no text overlays
```

**Variables:**
- `{subject_description}` — age, appearance, wardrobe (e.g., "woman in her 30s, dark curly hair, white linen shirt")
- `{background_description}` — (e.g., "soft gray studio backdrop")
- `{lighting_style}` — (e.g., "single key light from upper left, subtle fill from right")

**Recommended size:** 1024x1024 (square) or 1024x1536 (vertical for portrait emphasis)
**Model:** GPT Image 2 `quality: medium` or Nano Banana Pro (both handle photorealistic portraits well)
**Common pitfalls:**
- Not specifying "same person" in every panel — model may generate four different people
- Omitting which quadrant gets which angle — model arranges arbitrarily
- Requesting too-different crops (full body + extreme close-up) creates scale inconsistency within the grid

---

## 3. 3-Panel Campaign Collage

**When to use:** Hero shot + close-up + action for a campaign visual — horizontal or vertical triptych.

### Template (5-slot format)

```
Scene: Three-panel {orientation} collage for {brand_name} campaign. Panels separated by thin white lines.

Subject: {model_description} showcasing {product_description}.

Important Details:
Panel 1 (left/top): Hero wide shot — full figure of model with product, environmental context, lifestyle setting
Panel 2 (center/middle): Close-up product detail — {product_detail_description}, tactile textures, sharp focus
Panel 3 (right/bottom): Action shot — model using/wearing/interacting with product, candid energy, slight motion blur on extremities

Consistent warm golden-hour lighting across all panels. Same model identity throughout.
{typography_instruction}

Use Case: social media campaign visual, brand lookbook
Constraints: same person across all panels, consistent color grading, no stock-photo stiffness, {product_name} must be visible in every panel
```

**Variables:**
- `{orientation}` — "horizontal" (side by side) or "vertical" (stacked)
- `{brand_name}`, `{product_name}`, `{product_description}` — brand context
- `{model_description}` — who appears
- `{product_detail_description}` — what the close-up shows
- `{typography_instruction}` — e.g., `Text: "{HEADLINE}" in bold condensed white, overlaid on Panel 1 lower third` or omit for no text

**Recommended size:** 1536x1024 (horizontal triptych) or 1024x1536 (vertical triptych)
**Model:** GPT Image 2 `quality: medium` — if text overlay needed, use `quality: high`
**Common pitfalls:**
- Not specifying panel order — "hero, close-up, action" without left/center/right assignment
- Lighting inconsistency when mixing indoor close-up with outdoor hero shot — specify unified lighting
- Forgetting to mention subject consistency causes three different models

---

## 4. 4x3 Borderless Grid

**When to use:** 12 panels telling a story or showing moods — no gaps between panels, seamless mosaic feel.

### Template (5-slot format)

```
Scene: 4x3 borderless grid (4 columns, 3 rows) where each of the 12 panels is an independent image but panels share no borders, gaps, or dividers — edges touch seamlessly. Overall theme: {theme}.

Subject: {subject_description} — maintain strong subject consistency across all 12 panels.

Important Details:
Row 1: {panel_1}, {panel_2}, {panel_3}, {panel_4}
Row 2: {panel_5}, {panel_6}, {panel_7}, {panel_8}
Row 3: {panel_9}, {panel_10}, {panel_11}, {panel_12}

Style: {style_description}
Mood progression: {mood_arc}
Each panel is an independent composition but the overall grid reads as a unified artwork.

Use Case: mood board, editorial spread, social media carousel preview, album artwork
Constraints: borderless — no white lines, no black borders, no gaps between panels. Same subject identity across all panels. No text in panels.
```

**Variables:**
- `{subject_description}` — who/what appears across panels
- `{theme}` — overarching concept (e.g., "solitude in a city", "four seasons of a garden")
- `{panel_1}` through `{panel_12}` — brief shot description per cell
- `{style_description}` — visual style (e.g., "35mm film grain, desaturated palette")
- `{mood_arc}` — how energy changes across the grid (e.g., "calm morning to chaotic night")

**Recommended size:** 1536x1024 (landscape) — gives each cell enough resolution
**Model:** Nano Banana Pro (handles complex multi-element compositions with thinking mode; no text needed)
**Common pitfalls:**
- Saying "borderless" is not enough — explicitly state "no white lines, no black borders, no gaps"
- 12 panels in one image pushes detail limits — keep per-panel descriptions short and visually distinct
- Without explicit subject consistency instructions, each panel may feature a different person/object

---

## 5. 6-Frame Cinematic Sequence

**When to use:** Fashion editorial or film-style sequence — multiple camera angles of the same scene in one image.

### Template (5-slot format)

```
Scene: 6-frame cinematic sequence arranged in a 3x2 grid. Dark film-strip aesthetic with thin black borders. {location_description}.

Subject: {subject_description}, wearing {wardrobe_description}. Same person, same outfit, same location across all 6 frames.

Important Details:
Frame 1 (top-left): Top-down bird's eye view — subject seen from directly above, full body visible against ground/floor
Frame 2 (top-center): Low angle looking up — subject towering over camera, dramatic perspective, sky/ceiling visible
Frame 3 (top-right): Wide isolation shot — subject small in frame, vast environment dominates, sense of scale
Frame 4 (bottom-left): Close-up with slight tilt — face and upper body, Dutch angle, intimate intensity
Frame 5 (bottom-center): Motion frame — subject mid-action ({motion_action}), natural motion blur on limbs
Frame 6 (bottom-right): Grounded final — medium shot, subject at rest, direct gaze, resolving the sequence

Photographer reference: {photographer_style}
Lighting: consistent {lighting_description} across all frames

Use Case: fashion editorial, film lookbook, director's shot list visualization
Constraints: same person and wardrobe in every frame, no costume changes, consistent color grading, no text overlays
```

**Variables:**
- `{subject_description}` — model details
- `{wardrobe_description}` — clothing
- `{location_description}` — setting
- `{motion_action}` — what the motion frame captures (e.g., "walking forward", "turning sharply", "jumping")
- `{photographer_style}` — (e.g., "Peter Lindbergh desaturated realism", "Helmut Newton dramatic contrast")
- `{lighting_description}` — (e.g., "overcast natural light, soft shadows")

**Recommended size:** 1536x1024 (landscape, 3x2 grid)
**Model:** GPT Image 2 `quality: medium` or Nano Banana Pro
**Common pitfalls:**
- Not naming each frame explicitly — "various angles" is too vague, the model needs per-frame instructions
- Top-down and low-angle in the same grid confuse the model if you don't anchor each frame to a grid position
- Motion blur instruction must be specific ("blur on hands and feet") or the model applies blur everywhere

---

## 6. Before/After Split

**When to use:** Product transformation, makeover, time comparison, renovation — two states side by side.

### Template (5-slot format)

```
Scene: Single image split into left and right halves with a {divider_style} dividing line down the center. Before/after comparison.

Subject: {subject_description}

Important Details:
Left half (BEFORE): {before_description} — {before_condition}
Right half (AFTER): {after_description} — {after_condition}

The transition at the center line should feel {transition_style}. Same camera angle, same framing, same background perspective in both halves — only the subject's state changes.

Use Case: {use_case}
Constraints: identical composition and camera angle on both sides, same lighting direction, no text unless specified, the dividing line must be clearly visible
```

**Variables:**
- `{subject_description}` — what is being compared
- `{before_description}` / `{before_condition}` — left side state (e.g., "faded, cracked wall with peeling paint")
- `{after_description}` / `{after_condition}` — right side state (e.g., "freshly painted wall, smooth finish, vibrant color")
- `{divider_style}` — "thin white line" / "subtle gradient blend" / "sharp vertical cut"
- `{transition_style}` — "clean and abrupt" / "natural, as if wiping away"
- `{use_case}` — "product marketing", "renovation portfolio", "skincare results"

**Recommended size:** 1536x1024 (landscape — gives each half a portrait-like proportion)
**Model:** GPT Image 2 `quality: medium` — for text labels ("BEFORE" / "AFTER"), use `quality: high`
**Common pitfalls:**
- Not specifying "same camera angle both sides" — model may show two completely different viewpoints
- Without a visible divider, the two halves can merge into one ambiguous scene
- Left/right assignment matters — always state which side is before and which is after

---

## 7. 12-Panel Storyboard Poster

**When to use:** Full narrative in one image — 3x4 grid (3 columns, 4 rows) for animation or video pre-production.

### Template (5-slot format)

```
Scene: 12-panel storyboard poster, 3 columns x 4 rows. Dark background with each panel in a clean rectangular frame. "{title}" in bold white text at the top of the image. Below each panel: scene number and one-line description in small white text.

Subject: {character_description} — maintain consistent character design, proportions, and colors across all 12 panels.

Important Details:
Panel 1: {scene_1} — "{caption_1}"
Panel 2: {scene_2} — "{caption_2}"
Panel 3: {scene_3} — "{caption_3}"
Panel 4: {scene_4} — "{caption_4}"
Panel 5: {scene_5} — "{caption_5}"
Panel 6: {scene_6} — "{caption_6}"
Panel 7: {scene_7} — "{caption_7}"
Panel 8: {scene_8} — "{caption_8}"
Panel 9: {scene_9} — "{caption_9}"
Panel 10: {scene_10} — "{caption_10}"
Panel 11: {scene_11} — "{caption_11}"
Panel 12: {scene_12} — "{caption_12}"

Panels read left-to-right, top-to-bottom (like a comic page). Character appearance, clothing, and color palette must stay identical across all 12 panels — only pose, expression, angle, and environment change.

Style: {art_style}

Use Case: animation pre-production, pitch deck visualization, narrative overview poster
Constraints: all 12 panels must be distinct scenes (no duplicates), character consistency is critical, scene numbers must be legible, {language} captions
Quality: high
```

**Variables:**
- `{title}` — project/episode title displayed at top
- `{character_description}` — detailed character design (colors, outfit, distinguishing features)
- `{scene_1}` through `{scene_12}` — visual description of each panel
- `{caption_1}` through `{caption_12}` — text label under each panel
- `{art_style}` — (e.g., "Pixar-style 3D", "anime cel shading", "watercolor illustration", "graphic novel ink")
- `{language}` — caption language

**Recommended size:** 1024x1536 (portrait — 3 columns x 4 rows needs vertical space)
**Model:** GPT Image 2 `quality: high` (text-heavy — scene numbers and captions must be readable)
**Common pitfalls:**
- Character drift is the biggest risk at 12 panels — repeat character design details in the prompt, not just "same character"
- Without explicit scene numbering in the prompt, panels may appear in random order
- 12 panels with captions is extremely text-dense — keep captions under 5 words each for legibility
- Art style must be stated once and applied uniformly; mixing styles across panels produces visual chaos

---

## General Multi-Panel Tips

**Panel count vs. detail trade-off:** More panels = less detail per panel. 4 panels allow rich per-panel descriptions; 12 panels need brief, visually distinct descriptions (3-8 words each).

**Subject consistency:** Always include an explicit instruction: "same person / same character / same product across all panels." Repeat key identity markers (hair color, clothing, distinguishing features) rather than saying "same as before."

**Grid specification:** Always state the grid dimensions (e.g., "3x2 grid, 3 columns 2 rows"). Saying "6 panels" without layout instruction lets the model choose an unpredictable arrangement.

**Borders and gaps:** Be explicit — "thin white border between panels" or "borderless, no gaps." Default behavior varies by model and is unreliable.

**Reading order:** State it: "left-to-right, top-to-bottom" or "numbered 1-9 starting top-left." Without this, narrative flow may be jumbled.

**Model selection summary:**
- Text/labels in panels --> GPT Image 2 `quality: high`
- No text, complex composition --> Nano Banana Pro
- Budget/exploration --> Nano Banana 2 or GPT Image 2 `quality: low`
