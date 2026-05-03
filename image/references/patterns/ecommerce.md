# E-Commerce Product Photography Patterns

Reusable prompt templates for product ads, packaging, and commercial visuals. Each pattern uses `{variables}` for customization. Default model: GPT Image 2 (5-slot format) unless noted.

---

## Miniature Diorama Product Ad

Use when you need a playful, attention-grabbing product visual where tiny workers interact with an oversized product — ideal for social media ads and launch campaigns.

<!-- Source concept: miniature/tilt-shift product advertising with construction-worker scale play -->

```
Scene: clean {surface_color} tabletop studio, soft overhead diffused light, shallow depth of field with tilt-shift blur at edges
Subject: oversized {product_name} centered in frame, surrounded by miniature construction workers (1/87 scale figurines) — some climbing the packaging with tiny ladders, others operating a miniature crane to lift the cap/lid, a crew painting the label
Important Details: {product_material} surface catches key light from upper left, visible condensation/texture on product, figurines cast tiny hard shadows, warm {accent_color} hard hats on workers, fine detail on miniature tools, slightly desaturated background, eye-level camera angle
Use Case: social media product ad, Instagram carousel hero
Constraints: no text, no logos other than product label, no floating elements, product must remain recognizable and unaltered, no more than 8 figurines
```

**Key levers:** `{product_name}`, `{product_material}` (frosted glass, matte aluminum, glossy plastic), `{surface_color}` (white marble, raw concrete, light birch wood), `{accent_color}` (safety orange #FF6600, yellow #FFD600)

**Recommended model:** GPT Image 2 (`quality: high`) — precise figurine detail and product label legibility

---

## Luxury Cosmetics Studio Shot

Use for premium beauty or fragrance product photography — dark, moody, tactile surfaces with atmospheric effects.

<!-- Source concept: luxury perfume/cosmetics dark-marble studio photography with condensation and smoke -->

```
Scene: dark studio, {background_surface} surface with subtle reflections, thin layer of low-hanging smoke drifting left to right, {time_mood} ambient
Subject: {product_name} bottle/tube centered, three-quarter angle, {product_finish} catching a single key light from upper right
Important Details: fine water droplets on product surface (condensation, not spray), {accent_material} accent elements flanking the product (raw stone, dried botanicals, metal shavings), volumetric haze behind product, reflection on surface below is soft and dark, color palette restricted to {palette}, contact shadow sharp near base fading to soft
Use Case: luxury brand campaign hero, print ad, website banner
Constraints: no text overlays, no human hands, background stays dark (#0a0a0a to #1a1a1a gradient), no color spill outside the defined palette, no lens flare
```

**Key levers:** `{background_surface}` (nero marquina marble, wet obsidian slab, brushed gunmetal), `{product_finish}` (frosted glass, lacquered black, brushed gold), `{accent_material}` (raw quartz crystals, dried lavender stems, black river stones), `{palette}` (golds #C9A84C and blacks, rose #B76E79 and creams, emerald #2D6A4F and silvers), `{time_mood}` (cold blue, warm amber)

**Recommended model:** GPT Image 2 (`quality: high`) — surface materials and condensation detail

---

## 9-Panel TVC Storyboard Grid

> For a dark-themed variant with timestamps, see [multi-panel.md](../multi-panel.md#1-9-cell-grid-storyboard).

Use to present a product commercial shot breakdown in a single image — pitch decks, creative presentations, client approvals.

<!-- Source concept: 9-panel television commercial storyboard grid with numbered frames -->

```
Scene: white canvas background, clean 3x3 grid with thin #CCCCCC divider lines (2px), each cell represents one shot in a {duration}-second commercial
Subject: {product_name} commercial storyboard — each panel is a distinct camera setup
Important Details:
  Panel 1 (wide): establishing shot of {setting}, warm natural light, product not yet visible
  Panel 2 (medium): {protagonist} notices/discovers the product on {surface}
  Panel 3 (close-up): hand reaching for {product_name}, shallow depth of field
  Panel 4 (ECU): product detail — texture of {product_material}, label readable
  Panel 5 (medium): {protagonist} using/opening the product, genuine expression
  Panel 6 (reaction): close-up face, {emotion} expression, soft key light
  Panel 7 (wide): product in context of {lifestyle_scene}
  Panel 8 (beauty shot): product hero on {beauty_surface}, studio lighting
  Panel 9 (pack shot): product centered on white with "{tagline}" below in thin sans-serif, #333333
Use Case: creative pitch deck, storyboard for TVC production
Constraints: consistent character identity across all panels, no panel numbering text, uniform lighting temperature within the narrative (panels 1-7), distinct studio lighting for panels 8-9
```

**Key levers:** `{product_name}`, `{protagonist}` (woman in her 30s, young couple, family), `{setting}` (bright kitchen, outdoor terrace, urban cafe), `{emotion}` (satisfied, surprised, relaxed), `{beauty_surface}` (white marble, gradient gray), `{tagline}`, `{duration}` (15, 30)

**Recommended model:** GPT Image 2 (`quality: high`) — grid precision and text in panel 9

---

## Floating Ingredient Freeze-Frame

Use for food, beverage, or supplement products where suspended ingredients communicate freshness, flavor, or composition.

<!-- Source concept: frozen-motion ingredient explosion around product, high-speed photography aesthetic -->

```
Scene: {background_gradient} gradient backdrop, high-speed flash freeze-frame moment, clean studio environment
Subject: {product_name} container in center, tilted {tilt_angle} degrees, with {liquid_type} mid-pour arcing from the opening
Important Details: individual {ingredient_list} frozen in mid-air around the product — each element sharply focused with visible texture ({texture_details}), micro water droplets suspended alongside ingredients, single hard flash from behind (rim light on ingredients), secondary soft fill from front, liquid splash forms a clean arc with visible viscosity, product label faces camera and remains fully legible, ingredients distributed in a loose orbital pattern
Use Case: beverage packaging, food product poster, social media ad
Constraints: no ingredients overlapping the product label, no motion blur (everything frozen sharp), background must remain clean — no stray splashes hitting edges, no more than {max_ingredients} floating elements, no artificial glow effects
```

**Key levers:** `{product_name}`, `{background_gradient}` (#F5F0EB to #FFFFFF for light, #1A0A2E to #0D0D0D for dark), `{liquid_type}` (amber juice, white milk, green smoothie), `{ingredient_list}` (sliced strawberries + mint leaves + ice cubes, cocoa nibs + hazelnuts + vanilla pod), `{texture_details}` (visible seeds on strawberry cross-section, frost crystals on ice), `{tilt_angle}` (15, 25), `{max_ingredients}` (6-8)

**Recommended model:** GPT Image 2 (`quality: high`) — frozen detail precision and label legibility

---

## Inflatable Surrealism Product Poster

Use for disruptive, scroll-stopping social ads where the product packaging appears squeezed, inflated, or physically distorted as if made of soft rubber or vinyl.

<!-- Source concept: inflatable surrealism — product packaging rendered as squeezed/puffy/distorted soft objects -->

```
Scene: solid {background_color} background, soft even studio lighting with no hard shadows, slightly elevated camera angle (15 degrees above eye level)
Subject: {product_name} packaging reimagined as a puffy inflatable vinyl object — the shape is recognizable but squeezed at the middle as if gripped by an invisible hand, seams visible where vinyl panels meet, surface slightly reflective like a pool float
Important Details: {product_color_scheme} preserved on the inflated surface but stretched and slightly warped around curves, visible air valve at the bottom edge (small brass circle), subtle wrinkles where the vinyl compresses, the brand name/logo distorted by the inflation but still readable, two or three {companion_objects} nearby also inflated (matching aesthetic), environment reflection on glossy vinyl surface, cast shadow soft and diffused below
Use Case: disruptive social media ad, brand campaign poster, billboard
Constraints: product must remain identifiable despite distortion, no liquid, no particles, no humans, no text outside what exists on the packaging, vinyl texture must read as physical (not digital 3D render), background is flat color only
```

**Key levers:** `{product_name}`, `{background_color}` (bubblegum pink #FFB6C1, electric blue #007BFF, acid yellow #E8FF00), `{product_color_scheme}`, `{companion_objects}` (matching accessories, ingredient items, brand mascot elements)

**Recommended model:** NBP — complex spatial reasoning for believable physical distortion

### Nano Banana version:

```
A product poster showing {product_name} packaging transformed into a puffy inflatable vinyl object, squeezed at the middle as if gripped by an invisible hand. The surface is slightly glossy like a pool float, with visible seams where vinyl panels meet and a small brass air valve at the base. The original {product_color_scheme} is preserved but stretched and warped around the inflated curves. Brand text is distorted by the shape but still legible. Two small {companion_objects} sit nearby, also inflated in the same vinyl style. Solid {background_color} background, soft even studio light, slightly elevated camera angle. Soft diffused shadow below. Format: 4:5.
```
