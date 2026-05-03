# Portrait & Cinema Patterns

Reusable prompt templates for cinematic portraits, atmospheric character photography, and mood-driven portraiture. Each pattern uses `{variables}` for customization. Default model: GPT Image 2 (5-slot format) unless noted.

---

## Golden Hour Street Backlit Portrait

Use for warm, emotive street portraits with strong backlight flare — editorial, personal branding, album covers.

<!-- Source concept: golden hour backlit street portrait with lens flare and warm atmospheric haze -->

```
Scene: {street_description} at golden hour, sun positioned directly behind subject (5-10 degrees above horizon line), warm amber light flooding the street, slight atmospheric haze diffusing the backlight
Subject: {person_description}, standing at {position_in_street}, body angled three-quarter to camera, face turned toward lens with {expression}
Important Details: strong rim light outlining hair and shoulders in warm gold (#FFAA33), face lit primarily by bounce light from {bounce_surface} on the opposite side — softer and cooler than the backlight, shallow depth of field rendering background into warm bokeh circles, {clothing_detail} catches backlight along edges showing fabric texture, visible lens flare — one or two hexagonal flare artifacts near frame edge (organic, not excessive), long shadow cast toward camera on {ground_surface}, skin rendered naturally with warm undertones — no heavy smoothing, visible pores, {color_grade}
Use Case: editorial portrait, personal brand photography, album art
Constraints: face must be visible and well-exposed despite backlight (not silhouetted), no reflectors or studio equipment visible, lens flare limited to one or two subtle artifacts — not a starburst explosion, no added text, no vignette
```

**Key levers:** `{street_description}` (narrow European alley with stone walls, wide boulevard with linden trees, industrial backstreet with brick), `{person_description}`, `{expression}` (quiet confidence, mid-smile with closed lips, contemplative gaze), `{bounce_surface}` (cream-painted wall, parked white van, sand-colored buildings), `{clothing_detail}` (linen shirt collar, leather jacket shoulder seam, scarf edge), `{ground_surface}` (wet cobblestones, dry asphalt, packed earth), `{color_grade}` (Kodak Portra 400 warmth, slightly lifted blacks with amber cast, clean digital with warm white balance)

**Recommended model:** GPT Image 2 — backlight exposure control and skin rendering

---

## Convenience Store Neon Portrait

Use for urban night portraits with mixed artificial lighting — fluorescent overhead + colored neon signage creating a chromatic push-pull on the subject's face.

<!-- Source concept: convenience store / bodega neon portrait — fluorescent + neon mixed light on face -->

```
Scene: exterior of a {store_type} at night, shot through or near the front window/entrance, overhead fluorescent tubes casting flat {fluorescent_color} light from inside, {neon_sign_description} mounted on the wall/window casting {neon_color} glow on one side of the subject's face
Subject: {person_description}, {pose_description}, positioned at the threshold between interior fluorescent zone and exterior neon zone — split lighting across the face
Important Details: face receives {fluorescent_color} fill from the store interior on one side and {neon_color} accent from signage on the other — the two colors mix on the nose bridge and chin, visible product shelves or cooler glow softly in background bokeh, {clothing_description} absorbs and reflects the two light sources differently, condensation or grime on window glass if shot through it (subtle, not obscuring), wet pavement outside reflects both light sources in streaks, shallow depth of field with subject sharp, background a mosaic of colored bokeh, {camera_feel}
Use Case: urban editorial, music press portrait, fashion story, short film still
Constraints: face clearly visible — neither light source blows out features, neon sign text (if present) is secondary to the portrait not the focal point, no additional light sources beyond what exists in the scene, no heavy color grading beyond what the practical lights create naturally, no motion blur
```

**Key levers:** `{store_type}` (Korean convenience store, bodega, late-night pharmacy, 24-hour laundromat), `{fluorescent_color}` (cool blue-white, greenish-white, warm tungsten), `{neon_sign_description}` (red "OPEN" sign, blue beer brand logo, pink cursive word), `{neon_color}` (red #FF2D2D, blue #3366FF, pink #FF69B4, green #39FF14), `{person_description}`, `{pose_description}` (leaning against door frame, sitting on overturned crate, standing with hands in pockets), `{clothing_description}` (dark hoodie that absorbs light, white t-shirt that bounces both colors, leather that reflects), `{camera_feel}` (Cinestill 800T with halation around neon, clean digital night, Fujifilm color science)

**Recommended model:** GPT Image 2 (`quality: high`) — precise dual-light color rendering on skin

---

## Monochrome Glitch Profile Portrait

Use for edgy, tech-forward portraits — artist profiles, electronic music press, tech brand campaigns. High contrast black-and-white with selective red digital artifacts.

<!-- Source concept: monochrome profile portrait with digital glitch artifacts and red accent color -->

```
Scene: pure black background (#000000), no environment — subject emerges from darkness
Subject: {person_description} in sharp profile (facing {direction}), head and upper shoulders only, high-contrast black-and-white rendering
Important Details: extreme contrast — skin highlights blow to near-white, shadows fall to pure black with minimal midtone graduation, {hair_detail} silhouetted against black, one eye visible in profile with a single catchlight, horizontal glitch displacement lines cutting across the image at {glitch_positions} — each line offsets a thin horizontal slice (4-8px) to the right by 10-20px, the displaced slices rendered in {accent_color} (#FF0000 default) while the rest remains monochrome, fine horizontal scan lines across entire image (subtle, CRT monitor texture), grain: heavy high-ISO film grain throughout, jaw line and nose bridge are the sharpest elements in frame
Use Case: artist press photo, electronic music EP cover, tech brand portrait, social media profile
Constraints: glitch lines must look digital (clean horizontal displacement, not organic), accent color appears ONLY in the displaced glitch slices — no other colored elements, maximum {max_glitch_lines} glitch lines to avoid visual noise, face must remain recognizable despite artifacts, no text, background is solid black — no gradient or texture
```

**Key levers:** `{person_description}`, `{direction}` (left, right), `{hair_detail}` (tight buzz cut showing skull contour, shoulder-length hair with flyaway strands catching backlight, pulled-back bun), `{glitch_positions}` (across the eye, across the mouth, across the forehead — specify 2-3 positions), `{accent_color}` (#FF0000 red, #00FF41 terminal green, #FF00FF magenta), `{max_glitch_lines}` (3-5)

**Recommended model:** GPT Image 2 — high-contrast mono rendering and controlled glitch placement

---

## Japanese Negative Film Rooftop Portrait

Use for moody, atmospheric portraits with overexposed analog film qualities — muted colors, lifted shadows, and a feeling of faded memory. Ideal for editorial, zine, or personal project work.

<!-- Source concept: Japanese negative film aesthetic — overexposed, muted tones, rooftop setting -->

A waist-up portrait of {person_description} on a {rooftop_description}. They stand near the edge railing, {pose_description}, with the {city_skyline} visible behind them but washed out and desaturated by {sky_condition}. Shot on expired Japanese negative film — colors shifted toward {color_shift}, highlights blown soft and chalky, shadows lifted with visible grain in the flat midtones. Skin tones slightly green-yellow as if the film has aged. {clothing_description} reads as muted tones, almost monochromatic against the overexposed sky. Wind moves {wind_detail}. The mood is nostalgic and transient — a memory captured on deteriorating film stock. Eye-level framing, subject slightly off-center toward {frame_position}. Format: {aspect_ratio}.

**Key levers:** `{person_description}`, `{rooftop_description}` (concrete apartment building rooftop, industrial warehouse roof with exhaust vents, school building roof with chain-link fence), `{pose_description}` (leaning on railing looking at camera, turned away looking at skyline, sitting on a ledge with knees drawn up), `{city_skyline}` (Tokyo mid-rise apartments, generic Asian city with power lines), `{sky_condition}` (overcast white sky, hazy afternoon sun), `{color_shift}` (green-cyan cast, yellow-amber cast), `{clothing_description}` (oversized vintage windbreaker, plain white t-shirt, navy work jacket), `{wind_detail}` (hair across face, jacket hem, collar), `{frame_position}` (left third, right third), `{aspect_ratio}` (3:2, 4:5)

**Recommended model:** NB2 — analog film grain emulation and atmospheric mood

---

## Dreamy Underwater Surreal Portrait

Use for beauty campaigns, conceptual art, or album visuals — a portrait where the subject floats in clear water surrounded by translucent aquatic elements.

<!-- Source concept: surreal underwater portrait with translucent fish and dreamy caustic light -->

```
Scene: clear {water_color} water filling the entire frame, caustic light patterns rippling across the subject from above (sunlight through water surface), no visible pool walls or floor — infinite aquatic void
Subject: {person_description}, floating in a relaxed {pose_description}, eyes {eye_state}, hair fanning out in all directions as if weightless, {clothing_description} billowing and suspended in the water
Important Details: {fish_count} translucent {fish_type} swimming in a loose school around the subject — each fish semi-transparent with visible skeletal structure and iridescent scales catching the caustic light, light rays penetrating from above in {light_pattern}, fine air bubbles rising from near the subject's {bubble_source}, fabric of clothing moves independently from the body — folds and hems suspended in mid-drift, skin has a subtle cool {water_tint} cast from the water, overall palette is {palette}, composition framed as a {shot_type}
Use Case: beauty campaign, album cover, conceptual art print, fashion editorial
Constraints: subject's face must be clearly visible and serene (not distressed or holding breath with effort), fish are translucent — not solid opaque tropical fish, no visible water surface edge or pool tiles, no scuba gear or goggles, bubbles are small and delicate not large air pockets, underwater physics must be consistent (everything floats)
```

**Key levers:** `{water_color}` (deep cerulean #0077B6, pale turquoise #AFEEEE, dark teal #004D4D), `{person_description}`, `{pose_description}` (arms slightly outstretched like a slow free-fall, curled fetal position, one arm reaching upward toward the light), `{eye_state}` (softly closed, open and gazing upward at the light, looking directly at camera), `{clothing_description}` (flowing white silk dress, loose linen shirt and trousers, sheer organza wrap), `{fish_count}` (5-8), `{fish_type}` (jellyfish, small reef fish, elongated glass catfish), `{light_pattern}` (parallel god rays from upper right, scattered dappled caustics, single concentrated beam), `{bubble_source}` (lips, fingertips, fabric edges), `{water_tint}` (blue-green, aquamarine), `{palette}` (teal and ivory, deep blue and gold, seafoam and blush), `{shot_type}` (full body vertical, waist-up centered, three-quarter with negative space below)

**Recommended model:** NBP — complex physics (floating hair, fabric, fish transparency, caustic light)

### Nano Banana version:

```
A surreal underwater portrait of {person_description} floating in a relaxed {pose_description} in clear {water_color} water. Eyes {eye_state}, hair fans out weightlessly in all directions. {clothing_description} billows and suspends in the current, folds drifting independently. {fish_count} translucent {fish_type} swim in a loose school around the subject — each semi-transparent with visible skeletal structure and iridescent scales catching caustic light from above. Sunlight penetrates from the surface in {light_pattern}, casting rippling patterns across skin and fabric. Fine air bubbles rise from the subject's {bubble_source}. Skin has a subtle cool {water_tint} cast. No pool walls, no surface edge visible — infinite aquatic void. Serene and dreamlike. Palette: {palette}. Format: 4:5.
```
