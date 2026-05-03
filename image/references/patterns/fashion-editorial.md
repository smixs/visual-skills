# Fashion Editorial Patterns

Reusable prompt templates for fashion campaigns, lookbooks, and editorial shoots. Each pattern uses `{variables}` for customization. Default model: GPT Image 2 (5-slot format) unless noted.

---

## 3-Panel Campaign Collage

Use for fashion brand campaign hero images — one wide shot combining hero pose, close-up detail, and action/movement in a triptych layout.

<!-- Source concept: fashion campaign triptych collage — hero + detail + movement panels -->

```
Scene: three vertical panels side by side on a single canvas (left 40% width, right split into two stacked panels 60% height each), thin white divider lines (3px), cohesive {lighting_setup} across all panels
Subject: {model_description} wearing {outfit_description} — same person, same outfit, three perspectives
Important Details:
  Left panel (hero): full-body three-quarter pose, {model_description} standing against {background_1}, weight shifted to one hip, direct gaze at camera, medium-format film grain, {color_grade}
  Top-right panel (detail): extreme close-up of {detail_focus} — visible weave/stitching/texture of {fabric_type}, shallow depth of field, warm directional light raking across surface
  Bottom-right panel (action): mid-stride walking shot from low angle, {background_2}, coat/fabric in motion with natural drape physics, slight motion energy in hair
  Overall: cohesive warm/cool temperature of {color_temperature}, consistent skin tone rendering across panels, editorial magazine quality
Use Case: fashion brand campaign, lookbook cover, social media carousel hero
Constraints: same person with identical features in all three panels, no text, no logos, no visible studio equipment, panels must feel like one shoot not three separate photos, no heavy retouching glow
```

**Key levers:** `{model_description}` (East Asian woman mid-20s, athletic man early 30s), `{outfit_description}`, `{detail_focus}` (collar construction, cuff button, belt buckle, shoe sole), `{fabric_type}` (raw selvedge denim, double-faced cashmere, washed silk), `{background_1}` (concrete wall, sand dune, industrial corridor), `{background_2}` (open street, field, rooftop), `{color_grade}` (lifted blacks with amber cast, desaturated teal), `{color_temperature}` (warm 4000K feel, cool overcast daylight)

**Recommended model:** GPT Image 2 (`quality: high`) — identity consistency across panels and fabric texture detail

---

## 2x2 Editorial Portrait Grid

Use for model tests, casting cards, or editorial portfolio pages — four angles of the same person in a clean grid.

<!-- Source concept: 2x2 fashion portrait grid — same model, four setups -->

```
Scene: 2x2 grid on white canvas, thin {divider_color} divider lines (2px), all four cells use the same {background_type} with slight variation in angle
Subject: {model_description}, same {outfit_description} in all four frames
Important Details:
  Top-left: straight-on headshot, neutral expression, eyes to camera, even butterfly lighting
  Top-right: three-quarter profile, chin slightly lifted, single key light from camera-left creating defined cheekbone shadow
  Bottom-left: full profile silhouette, rim light from behind outlining jaw and nose, {background_type} slightly darker
  Bottom-right: candid moment — mid-laugh or adjusting {accessory}, natural movement, softer light
  All frames: {film_stock} color science, consistent {skin_tone_handling}, no heavy skin smoothing — visible pores and natural texture, shallow depth of field in all four
Use Case: fashion editorial spread, model comp card, casting portfolio
Constraints: identical person in all four frames (bone structure, skin, hair must match exactly), no makeup changes between frames, no text, no watermarks, backgrounds must feel cohesive not random
```

**Key levers:** `{model_description}`, `{outfit_description}` (black turtleneck, white linen shirt unbuttoned at collar), `{background_type}` (seamless medium gray, textured plaster wall, out-of-focus greenery), `{divider_color}` (#FFFFFF, #E0E0E0), `{film_stock}` (Kodak Portra 400, Fujifilm Pro 400H), `{skin_tone_handling}` (warm undertones preserved, cool-neutral rendering), `{accessory}` (earring, collar, watch)

**Recommended model:** GPT Image 2 (`quality: high`) — identity consistency critical across four frames

---

## Streetwear Poster with Oversized Typography

Use for streetwear drops, limited edition launches, or urban fashion brand campaigns where bold type dominates the composition.

<!-- Source concept: streetwear poster with model integrated into oversized typographic layout -->

```
Scene: solid {background_color} background, graphic poster composition, typography dominates 60% of visual space
Subject: {model_description} in {streetwear_outfit}, standing or crouching in a {pose_description}, positioned {model_position} — partially overlapping the text layers
Important Details: headline "{HEADLINE_TEXT}" in extra-bold condensed {font_style}, {text_color}, occupying upper two-thirds of frame — model breaks in front of some letters and behind others (depth interplay), secondary text "{SUBHEAD_TEXT}" in thin weight {subhead_color} near bottom edge, {lighting_type} on model creating {shadow_quality} shadows, grain overlay across entire image ({grain_intensity}), composition follows rule of thirds with model at {grid_position} intersection
Use Case: streetwear brand drop poster, social media announcement, lookbook cover
Constraints: text must be fully legible even where model overlaps, no extra text or watermarks, no decorative elements besides type and model, model does not obscure more than 30% of any single letter, "{HEADLINE_TEXT}" spelled exactly as provided
Quality: high
```

**Key levers:** `{HEADLINE_TEXT}` (brand name, drop name), `{SUBHEAD_TEXT}` (date, "LIMITED DROP", collection name), `{background_color}` (off-white #F5F1EB, concrete gray #8C8C8C, matte black #0D0D0D), `{text_color}` (#000000, #FF3333, #FFFFFF), `{font_style}` (sans-serif like Druk Wide, slab-serif, stencil), `{streetwear_outfit}`, `{model_position}` (center-left, right third), `{lighting_type}` (harsh direct flash, soft window light), `{grain_intensity}` (subtle film grain, heavy 35mm grain)

**Recommended model:** GPT Image 2 (`quality: high`) — text rendering and model-type depth interplay

---

## Retro Roller Skating Sportswear Campaign

Use for playful, nostalgic sportswear or athleisure campaigns with 70s-80s visual language.

<!-- Source concept: retro roller skating / sportswear campaign with analog film aesthetic -->

A sun-drenched wide shot of {model_description} roller skating along a {location_description}. They wear {outfit_description} — the fabric catches light as they move, one leg extended mid-glide, arms relaxed and swinging naturally. The ground is smooth asphalt with painted lane markings in faded {lane_color}. Background shows {background_elements} slightly out of focus through heat haze. Shot on {film_stock} with pronounced grain and slightly lifted shadows. Color palette centers on {palette_description}. Golden hour backlight creates a warm halo around the subject and long shadow stretching toward camera. Genuine movement energy — hair and loose fabric respond to speed. Format: {aspect_ratio}.

**Key levers:** `{model_description}`, `{outfit_description}` (high-waisted terry shorts in coral, cropped zip-up in cream, tube socks with racing stripes), `{location_description}` (Venice Beach boardwalk, empty suburban tennis court, coastal promenade), `{film_stock}` (Kodak Gold 200, Fuji Superia 400), `{palette_description}` (terracotta #CC5533, cream #FFF5E1, sky blue #87CEEB, mustard #D4A017), `{lane_color}` (faded yellow, sun-bleached white), `{background_elements}` (palm trees and pastel buildings, chain-link fence and bleachers), `{aspect_ratio}` (3:2, 16:9)

**Recommended model:** NB2 — natural movement, analog film grain, atmospheric grounding

---

## Futuristic Sportswear Editorial with 3D Blob Shapes

Use for forward-looking athletic or techwear editorials where abstract 3D forms create a surreal spatial environment around the model.

<!-- Source concept: futuristic sportswear editorial with organic 3D blob/sphere shapes -->

```
Scene: {studio_environment} studio space, matte {floor_color} floor extending to infinity, ambient fill light with no visible source, three to five large organic 3D blob shapes ({blob_color}, glossy smooth surface with environment reflections) floating at varying heights around the subject
Subject: {model_description} in {techwear_outfit}, posed in an athletic stance — {pose_detail}
Important Details: blobs range from basketball-sized to armchair-sized, each with smooth amoebic curves and a single specular highlight, they cast soft colored shadows onto the floor and the model's clothing, model lit by cool directional light from camera-right creating defined muscle/fabric contour, {fabric_detail} visible in the garment construction, one blob partially behind the model and one in front (spatial depth), color palette limited to {palette}, overall mood is clinical and aspirational
Use Case: sportswear lookbook, techwear campaign, editorial magazine spread
Constraints: blobs must look physically present (not composited), no text, no logos, no additional props, model remains the clear focal point despite the surrounding forms, blobs do not touch or intersect with the model's body, no motion blur
```

**Key levers:** `{studio_environment}` (white void, concrete gray, deep navy), `{floor_color}` (light gray #D0D0D0, charcoal #333333), `{blob_color}` (chrome silver, translucent jade #00A86B, matte coral #FF6B6B), `{techwear_outfit}` (bonded seam track pants + compression top, oversized windbreaker + utility shorts), `{pose_detail}` (low lunge position, standing with one arm extended checking a wrist device, mid-jump), `{fabric_detail}` (visible bonded seams, reflective piping, mesh ventilation panels), `{palette}` (monochrome + single accent, earth tones + neon green #39FF14)

**Recommended model:** NBP — complex spatial reasoning for blob placement and reflections

### Nano Banana version:

```
A futuristic sportswear editorial photograph in a {studio_environment} studio space with a matte {floor_color} floor extending to infinity. {model_description} stands in an athletic {pose_detail}, wearing {techwear_outfit} with {fabric_detail}. Three to five large organic 3D blob shapes in {blob_color} with glossy smooth surfaces float at varying heights around the subject — the largest is armchair-sized, the smallest basketball-sized. Each blob has amoebic curves and casts soft colored shadows onto the floor and the model's clothes. Cool directional light from camera-right defines contour and fabric texture. One blob sits partially behind the model, one in front, creating depth. The model is the clear focal point. No text, no logos. Format: 4:5.
```
