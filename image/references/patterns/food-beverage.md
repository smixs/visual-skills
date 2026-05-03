# Food & Beverage Patterns

Reusable prompt templates for food photography, beverage campaigns, and culinary illustration. Each pattern uses `{variables}` for customization. Default model: GPT Image 2 (5-slot format) unless noted.

---

## Luxury Chocolate Brand Campaign

Use for premium chocolate or confectionery brand visuals — moody, textural, with controlled color and atmosphere. Adaptable across mood variants (dark indulgence, bright artisan, earthy origin-story).

<!-- Source concept: luxury chocolate brand campaign with variant moods and tactile surfaces -->

```
Scene: {surface_material} surface, {lighting_mood} lighting setup — {light_description}, thin atmospheric haze at background edge, color palette restricted to {palette}
Subject: {product_arrangement} — {product_count} pieces of {chocolate_type} arranged in {arrangement_style}
Important Details: visible snap edge on broken piece revealing {interior_texture}, fine cocoa powder dusted across surface (concentrated near product, fading to clean edges), {garnish_elements} placed deliberately as art direction not garnish, one piece mid-break with clean fracture line, surface texture of chocolate shows {surface_quality}, camera angle {camera_angle}, shallow depth of field with sharpest focus on the broken piece
Use Case: luxury chocolate brand campaign, print ad, packaging insert
Constraints: no human hands, no utensils, no wrappers or packaging visible, no text, cocoa dust must look natural not dumped, maximum {product_count} chocolate pieces, no melting

Mood variant — {mood_name}:
{mood_modifier}
```

**Key levers:**
- `{surface_material}` — dark slate, raw walnut wood, black marble, crumpled kraft paper
- `{lighting_mood}` — dramatic chiaroscuro / soft diffused warmth / cold window light
- `{light_description}` — single hard key from upper left / wrap-around softbox / backlit through parchment
- `{palette}` — deep browns #3E2723 + gold #C9A84C + black / warm terracotta #A0522D + cream #FFF8E7 / emerald #2D6A4F + copper #B87333
- `{chocolate_type}` — single-origin dark 72%, white chocolate with matcha veins, ruby chocolate
- `{interior_texture}` — smooth ganache center, crunchy praline layers, salted caramel pocket
- `{garnish_elements}` — single vanilla pod, fleur de sel crystals, edible gold leaf fragments, dried raspberry
- `{arrangement_style}` — diagonal cascade, tight cluster with negative space right, single row
- `{mood_name} / {mood_modifier}` — "Dark Indulgence": push contrast, deepen shadows, add smoke wisp / "Bright Artisan": overcast daylight, lifted blacks, pastel accent / "Origin Story": raw earth tones, burlap texture, raw cacao beans nearby

**Recommended model:** GPT Image 2 (`quality: high`) — fracture detail and cocoa powder precision

---

## High-Fashion Beverage Campaign Board

Use for premium beverage brand campaigns that combine lifestyle and product in a structured board layout — model shot + hero product + product lineup.

<!-- Source concept: fashion-meets-beverage campaign board with model, hero product, and lineup -->

```
Scene: horizontal triptych layout on single canvas — left panel (45% width), center panel (30%), right panel (25%), thin {divider_color} dividers (2px), unified {color_temperature} color temperature
Subject: {beverage_brand} campaign board featuring {model_description} and {product_name}
Important Details:
  Left panel (lifestyle): {model_description} at {location}, holding {product_name} at {hold_position}, {model_action}, shot on {film_aesthetic} — environment tells the brand story
  Center panel (hero): {product_name} bottle/can beauty shot, {product_angle} angle, {product_surface} surface, single key light with {highlight_style}, condensation droplets on glass/can surface, label sharp and legible
  Right panel (lineup): {lineup_count} product variants arranged in a {lineup_arrangement}, same lighting as center panel but pulled back wider, each label variant distinguishable by color ({variant_colors})
  Typography: none in image
Use Case: brand campaign presentation, pitch deck, retail POS
Constraints: model does not look directly at product (natural interaction), product label consistent and legible in all panels, lighting temperature cohesive, no floating elements, condensation looks physical not painted on
```

**Key levers:** `{product_name}`, `{beverage_brand}`, `{model_description}`, `{location}` (sunlit rooftop bar, marble kitchen counter, poolside), `{hold_position}` (mid-sip, resting at hip, gesturing with it), `{model_action}` (laughing mid-conversation, looking off-frame, walking), `{film_aesthetic}` (warm Kodak Portra feel, clean digital, cold editorial), `{product_angle}` (three-quarter front, straight-on, slight low angle), `{product_surface}` (wet dark stone, frosted glass shelf, white marble), `{lineup_count}` (3-5), `{variant_colors}` (amber/ruby/gold, mint/lemon/berry), `{divider_color}` (#FFFFFF, #1A1A1A)

**Recommended model:** GPT Image 2 (`quality: high`) — label legibility and panel consistency

---

## Hyper-Realistic Food Poster Template

Use for hero food posters — restaurants, delivery apps, menu boards — where the food is the entire composition with fillable content slots.

<!-- Source concept: hyper-realistic food poster with controlled composition slots -->

```
Scene: {background_treatment}, {atmosphere_effect}, overall tone {color_tone}
Subject: {dish_name} — {dish_description}, plated on {plate_description}, centered in frame
Important Details:
  Plating: {plating_details}
  Steam/moisture: {steam_detail}
  Garnish: {garnish_detail} placed at {garnish_position}
  Surface: {table_surface}, visible texture extending to frame edges
  Props: {prop_list} — arranged {prop_arrangement}
  Camera: overhead ({overhead_angle}) OR {camera_angle}, {lens_feel}
  Lighting: {food_lighting} — highlights on {highlight_targets}
Use Case: restaurant poster, delivery app hero, menu board, food magazine cover
Constraints: food must look freshly prepared (not cold or sat-out), no human hands or utensils in active use (props only), colors must be appetizing — no blue cast, no desaturated tones on the food itself, {plate_description} must not compete with the dish
```

**Key levers:**
- `{dish_name}` / `{dish_description}` — the hero food item described in appetizing physical detail
- `{plate_description}` — matte white ceramic, dark stoneware, rustic wooden board, banana leaf
- `{plating_details}` — sauce swoosh from 2 o'clock, microgreens at 10 o'clock, sesame seed scatter
- `{steam_detail}` — visible steam wisps rising from center, condensation on glass nearby, no steam
- `{garnish_detail}` — single basil sprig, chili flake scatter, citrus zest curls
- `{table_surface}` — aged oak, dark concrete, white marble with gray veins
- `{prop_list}` — linen napkin, vintage fork, small bowl of sauce, scattered herbs
- `{food_lighting}` — warm directional from upper-left with fill bounce, harsh noon daylight, moody side light
- `{background_treatment}` — dark vignette, clean bright, rustic blur
- `{camera_angle}` — 45-degree three-quarter, straight-on eye-level, overhead flat-lay

**Recommended model:** GPT Image 2 (`quality: high`) — steam, condensation, and ingredient texture fidelity

---

## Naturalist Food Specimen Cross-Section

Use for educational food content, ingredient features, or artisanal brand storytelling — the food item rendered as a scientific illustration in the style of 19th-century naturalist prints.

<!-- Source concept: Audubon-style naturalist botanical/food specimen illustration with cross-section -->

A detailed naturalist illustration of {food_item} rendered in the style of 19th-century scientific specimen plates. The composition shows the item in three states arranged vertically on an aged {paper_color} parchment background: whole specimen at top with botanical accuracy, lateral cross-section at center revealing internal structure ({internal_details}), and an exploded detail of {detail_element} at bottom with fine ink annotation lines pointing to key features. Drawn with precise {medium_description} — visible hatching for shadow, stippling for texture, thin ink outlines. Color is naturalistic but slightly muted as if from a hand-tinted lithograph. A thin decorative border frames the composition. Small italic Latin-style label "{latin_label}" at the bottom in serif font, {ink_color} ink. Format: 3:4.

**Key levers:** `{food_item}` (pomegranate, sourdough loaf, wagyu ribeye, cacao pod), `{internal_details}` (seed chambers with ruby arils, crumb structure with irregular air pockets, marbling fat distribution), `{detail_element}` (individual seed anatomy, crust layering, fat crystal structure), `{paper_color}` (warm cream #FDF5E6, cool ivory #FFFFF0), `{medium_description}` (watercolor wash with ink line, graphite with colored pencil, pure ink with minimal color), `{latin_label}` (a playful Latinized name), `{ink_color}` (sepia #704214, India black #1A1A1A)

**Recommended model:** NB2 — naturalist illustration style, grounding on botanical plate aesthetics

---

## City Food Map Illustration

Use for restaurant guides, food festival materials, travel content, or local cuisine features — a bird's-eye illustrated map showing food specialties across a city.

<!-- Source concept: hand-drawn illustrated food map of a city with dish icons and landmarks -->

A hand-drawn illustrated bird's-eye map of {city_name} showing its food culture. The map covers the {area_description} with simplified but recognizable {landmark_list} drawn in a loose ink-and-watercolor style. Scattered across the map are {dish_count} illustrated food items representing local specialties — each dish ({dish_list}) drawn at exaggerated scale hovering near its neighborhood, rendered in warm appetizing watercolor with visible brushstrokes. Streets are thin ink lines with {street_style}. Water features rendered in soft {water_color} wash. The overall palette is {palette_description}. A decorative hand-lettered title "{MAP_TITLE}" sits in a banner at the top. Small hand-written labels mark each dish and neighborhood. Style references vintage travel poster illustration meets editorial food drawing. Format: {aspect_ratio}.

**Key levers:** `{city_name}`, `{area_description}` (central 5 km, old town quarter, waterfront district), `{landmark_list}` (main cathedral, central market, river bridges), `{dish_count}` (6-10), `{dish_list}` (plov near the bazaar, samsa near the old town, shashlik near the park), `{street_style}` (slightly wobbly freehand, clean but simplified), `{water_color}` (cerulean #0077B6, teal #2A9D8F), `{palette_description}` (warm terracotta and cream with food items in full saturated color, cool blues and greens with warm food accents), `{MAP_TITLE}` ("A Taster's Guide to {city_name}"), `{aspect_ratio}` (3:4, 1:1)

**Recommended model:** NB2 — image grounding for real city landmarks + illustration style

### Nano Banana version:

```
A hand-drawn illustrated bird's-eye food map of {city_name}, covering the {area_description}. Simplified but recognizable {landmark_list} are drawn in loose ink-and-watercolor style. {dish_count} local dishes ({dish_list}) float at exaggerated scale near their neighborhoods, each painted in warm appetizing watercolor with visible brushstrokes. Streets are thin freehand ink lines. Water features in soft {water_color} wash. A hand-lettered banner at top reads "{MAP_TITLE}". Small hand-written labels mark dishes and neighborhoods. Style mixes vintage travel poster illustration with editorial food drawing. Palette: {palette_description}. Format: {aspect_ratio}.
```
