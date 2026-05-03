# Character Design Patterns

Reusable prompt templates for character turnarounds, expression sheets, outfit variants, and collectible/card formats. Each pattern uses `{variables}` for customization. Default model: GPT Image 2 (5-slot format) unless noted.

---

## Character Turnaround Sheet (3-View)

Use for game or animation pre-production — front, side, and back views of a character on a single white canvas with color callouts and height reference lines.

<!-- Source concept: character model sheet / turnaround sheet for 3D modelers and animators -->

```
Scene: clean white background, flat even lighting with no cast shadows, thin horizontal height reference lines in #CCCCCC spanning the full width at head, shoulder, waist, knee, and foot level
Subject: {character_name} — {character_description} — shown in three views arranged left to right: front view (facing camera), three-quarter side view (turned 75 degrees right), back view (facing away)
Important Details: all three views share identical proportions and vertical alignment along the height lines, feet on the same baseline, arms relaxed at sides for clear silhouette reading, color callout annotations — small circles of each key color ({color_1} {hex_1}, {color_2} {hex_2}, {color_3} {hex_3}) connected by thin #999999 leader lines to the corresponding material on the front view, fine line weight for height markers, clothing folds and seam lines consistent across all three angles
Use Case: game character pre-production, animation model sheet, 3D reference handoff
Constraints: no background elements, no props in hands, no dramatic poses — neutral standing pose only, all three views must depict the exact same character with identical outfit and proportions, no drop shadows, no gradient backgrounds
```

**Key levers:** `{character_name}`, `{character_description}` (age, build, hairstyle, outfit — be specific), `{color_1}`/`{hex_1}` through `{color_3}`/`{hex_3}` (key palette colors for callouts, e.g. jacket navy #1B2A4A, skin warm beige #D4A574, hair auburn #8B3A2F)

**Recommended model:** GPT Image 2 (`quality: high`) — height reference lines and color callout text require precise rendering

---

## Expression Sheet

Use to produce a grid of 6–9 facial expressions for the same character — consistent head angle and art style, with emotion labels under each face.

<!-- Source concept: character expression/emotion reference sheet for animation or visual novel production -->

```
Scene: white background, 3x3 grid (or 3x2 for 6 expressions) with thin #DDDDDD divider lines, each cell contains one head-and-shoulders portrait
Subject: {character_name} — {character_description} — same head angle (three-quarter left), same hairstyle, same lighting across all cells
Important Details:
  Cell 1: neutral — relaxed brow, closed mouth, calm eyes. Label: "NEUTRAL"
  Cell 2: happy — genuine smile reaching the eyes, raised cheeks. Label: "HAPPY"
  Cell 3: angry — furrowed brow, clenched jaw, narrowed eyes. Label: "ANGRY"
  Cell 4: sad — downturned mouth, glistening eyes, slightly lowered head. Label: "SAD"
  Cell 5: surprised — wide eyes, raised eyebrows, open mouth. Label: "SURPRISED"
  Cell 6: disgusted — wrinkled nose, upper lip raised, squinted eyes. Label: "DISGUSTED"
  {extra_expressions}
  Labels in small {label_font} beneath each cell, #555555 text
  Consistent {art_style} rendering across all cells — skin tone, line weight, shading approach identical
Use Case: animation expression reference, visual novel sprite guide, game character documentation
Constraints: same character identity in every cell — no variation in hair, accessories, skin tone, or clothing between expressions, head angle stays fixed, no hand gestures, labels must be legible
```

**Key levers:** `{character_name}`, `{character_description}` (face shape, skin tone, hair, distinguishing marks), `{art_style}` (clean cel-shaded anime, painterly semi-realism, flat vector illustration), `{label_font}` (condensed sans-serif, monospace, rounded sans), `{extra_expressions}` (add cells 7-9: e.g. "Cell 7: smirk — one corner of mouth raised, knowing look. Label: 'SMIRK'")

**Recommended model:** GPT Image 2 (`quality: high`) — text labels and consistent facial identity across 9 cells need precise control

---

## Outfit Variant Grid

Use to show one character in multiple outfits or costumes — for fashion exploration, game skin concepts, or wardrobe design.

<!-- Source concept: character costume/skin variant sheet for fashion or game design -->

```
Scene: light neutral background ({bg_color}), {grid_layout} grid, thin white gaps between cells, soft even front lighting in every cell
Subject: {character_name} — {character_description} — same pose ({pose_description}) in every cell, only the outfit changes
Important Details:
  Cell 1: {outfit_1_name} — {outfit_1_description}
  Cell 2: {outfit_2_name} — {outfit_2_description}
  Cell 3: {outfit_3_name} — {outfit_3_description}
  Cell 4: {outfit_4_name} — {outfit_4_description}
  Cell 5: {outfit_5_name} — {outfit_5_description}
  Cell 6: {outfit_6_name} — {outfit_6_description}
  Outfit name in small bold sans-serif centered below each cell, #333333 text
  Character body proportions, face, hairstyle, and skin tone identical across all cells — only clothing and accessories differ
Use Case: game skin lineup, fashion mood board, costume design exploration
Constraints: same character identity and pose in every cell, no background scenery — character only, outfit labels must be readable, no overlapping garments between cells, {grid_layout} layout must be uniform
```

**Key levers:** `{character_name}`, `{character_description}` (build, face, hair — anchor identity), `{bg_color}` (#F0F0F0 light gray, #FFF8F0 warm cream, #E8EDF2 cool blue-gray), `{grid_layout}` (2x3 or 3x3), `{pose_description}` (hands on hips, relaxed standing, one hand raised), `{outfit_N_name}` / `{outfit_N_description}` (e.g. "Street Casual" — oversized denim jacket, white tee, black cargo pants, chunky sneakers)

**Recommended model:** GPT Image 2 (`quality: medium`) — character consistency is the priority; `high` only if outfit labels need fine legibility

---

## Chibi / Mini-Me Collectible

Use to transform a realistic character into a cute 3D collectible figurine — oversized head, compact body, multiple poses performing different activities.

<!-- Source concept: chibi/super-deformed vinyl collectible figurine with consistent identity across poses -->

```
Scene: soft gradient background ({bg_gradient}), studio product lighting with rim light from behind and soft fill from front, subtle ground shadow beneath each figurine
Subject: chibi-style 3D collectible figurine of {character_name} — {character_description_simplified} — large head (roughly 1:2 head-to-body ratio), rounded limbs, smooth matte vinyl surface, {num_poses} poses arranged in a row
Important Details:
  Pose 1: {pose_1_description}
  Pose 2: {pose_2_description}
  Pose 3: {pose_3_description}
  {extra_poses}
  Face retains recognizable features from the original character — {face_markers} — simplified into the chibi style with large round eyes and small nose/mouth
  Outfit matches the original: {outfit_simplified} — colors preserved ({color_palette}), details reduced to clean shapes
  Each figurine sits on a small circular base ({base_color} matte finish)
  Vinyl toy aesthetic — visible seam line at sides, slight glossy highlight on forehead and cheeks
Use Case: merchandise concept, social media avatar set, fan collectible design
Constraints: consistent face and outfit across all poses, chibi proportions must stay uniform (no realistic proportions creeping in), no text on bases, smooth render — not cel-shaded, matte vinyl material throughout
```

**Key levers:** `{character_name}`, `{character_description_simplified}` (key outfit and hair only), `{face_markers}` (e.g. round glasses, scar on left cheek, green eyes), `{color_palette}` (hex values for 2-3 dominant colors), `{bg_gradient}` (#F5F0EB to #FFFFFF warm, #E0E8F0 to #FFFFFF cool), `{num_poses}` (3-5), `{pose_N_description}` (e.g. sitting cross-legged reading a book, waving with both hands, holding a coffee cup), `{base_color}` (white, black, matching character's main color)

**Recommended model:** GPT Image 2 (`quality: medium`) — smooth 3D vinyl surfaces render well at medium; `high` for marketing-ready close-ups

### Nano Banana version:

```
A row of {num_poses} chibi-style 3D vinyl collectible figurines of {character_name}, each in a different pose. Large head (1:2 head-to-body ratio), rounded limbs, smooth matte vinyl surface with visible seam lines and subtle glossy highlights on the forehead. Face retains {face_markers} simplified into chibi proportions with large round eyes. Outfit: {outfit_simplified} in {color_palette}. Poses left to right: {pose_1_description}, {pose_2_description}, {pose_3_description}. Each figurine on a small circular {base_color} matte base. Soft gradient background ({bg_gradient}), studio product lighting with rim light from behind and soft fill from front, subtle ground shadow. Format: 16:9.
```

---

## Anime-Style Character Card

Use for a full character reference card with portrait, full body, key items, and color palette — organized on a white background in a professional concept art layout.

<!-- Source concept: anime/game character reference sheet with stats, items, and palette swatches -->

```
Scene: white background, organized reference card layout divided into clear sections with thin #CCCCCC separator lines
Subject: {character_name} — {character_description} — anime-style rendering with clean line art and flat cel shading
Important Details:
  Left section (40% width): full-body standing pose, front-facing, arms slightly away from body to show full outfit, feet visible, confident neutral expression
  Upper-right section: portrait bust — head and shoulders, three-quarter angle, detailed face rendering showing {face_details}
  Mid-right section: {num_items} key items arranged in a row — {item_1}, {item_2}, {item_3} — each drawn at consistent scale with thin outline, labeled in small text below
  Lower-right section: color palette — {num_swatches} rectangular swatches in a horizontal strip showing the character's key colors ({swatch_colors}), hex code below each swatch
  Bottom strip: brief stat block or bio text in clean sans-serif — "Name: {character_name} | Class: {class} | Height: {height} | Affiliation: {affiliation}"
  Consistent line weight and shading style across all sections
Use Case: game character documentation, light novel illustration guide, animation production reference
Constraints: unified anime art style across all sections — portrait and full body must be the same character with identical design, items must match what the character wears/carries in the full body view, no decorative borders or ornamental frames, text must be legible at screen resolution
```

**Key levers:** `{character_name}`, `{character_description}` (detailed: hair color/style, eye color, outfit layers, accessories), `{face_details}` (distinctive facial features — e.g. heterochromia, facial tattoo, sharp jawline), `{item_1}`/`{item_2}`/`{item_3}` (signature weapon, accessory, artifact), `{swatch_colors}` (e.g. midnight blue #191970, cherry red #C41E3A, silver #C0C0C0, warm skin #E8B89D), `{num_swatches}` (4-6), `{class}` / `{height}` / `{affiliation}` (stat block fields)

**Recommended model:** GPT Image 2 (`quality: high`) — text-heavy layout with hex codes, labels, and stat block requires precise rendering

### Nano Banana version:

```
An anime-style character reference card for {character_name} on a white background. Left side: full-body standing pose, front-facing, clean cel-shaded anime rendering — {character_description}. Upper right: portrait bust at three-quarter angle showing {face_details}. Mid-right: key items laid out in a row — {item_1}, {item_2}, {item_3} — each drawn consistently and labeled. Lower right: horizontal color palette strip with {num_swatches} rectangular swatches ({swatch_colors}). Clean layout with thin gray separator lines between sections. Professional concept art quality, consistent line weight throughout. Format: 3:4.
```
