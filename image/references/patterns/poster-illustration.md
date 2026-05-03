# Poster & Illustration Patterns

Reusable prompt templates for posters, art prints, campaign collages, and graphic illustrations. Each pattern uses `{variables}` for customization. Default model: GPT Image 2 (5-slot format) unless noted.

---

## City Across Two Centuries (Time-Split Composition)

Use for urban development campaigns, anniversary materials, cultural exhibitions, or editorial features — a single city view divided down the middle, one half historical and one half modern.

<!-- Source concept: time-split composition — same city view, two eras side by side -->

```
Scene: wide establishing shot of {city_landmark_view}, frame divided vertically down the center — left half shows the scene in {historical_era}, right half shows {modern_era}
Subject: the same geographic viewpoint across two time periods, architecture and infrastructure transforming at the dividing line
Important Details:
  Left half ({historical_era}): {historical_details} — muted {historical_palette} palette, {historical_atmosphere}, period-accurate architecture, {historical_figures} going about daily life, {historical_transport}
  Right half ({modern_era}): {modern_details} — {modern_palette} palette, {modern_atmosphere}, contemporary architecture where old buildings once stood (some landmarks preserved), {modern_figures}, {modern_transport}
  Dividing line: not a hard cut — elements morph and blend across a narrow 5% transition zone (a horse-drawn cart becomes a car, a gas lamp becomes LED, cobblestones become asphalt, a tree grows taller)
  Sky transitions too: {historical_sky} on left to {modern_sky} on right
  Camera angle: elevated three-quarter view (roughly 30 degrees above street level) to show depth of both eras
Use Case: city anniversary campaign, urban development feature, cultural exhibition poster, editorial illustration
Constraints: both halves must depict the SAME geographic location (matching terrain, river, hill positions), transition zone should feel organic not pasted, scale and perspective consistent across both halves, no text unless specified, no anachronistic elements (modern items in historical half or vice versa outside the transition)
```

**Key levers:** `{city_landmark_view}` (view down the main avenue toward the central square, riverfront panorama, view from the hill overlooking the old town), `{historical_era}` / `{modern_era}` (1920s / 2020s, medieval / present day, 1960s / 2060s), `{historical_details}` (cobblestone streets, horse-drawn carts, hand-painted shop signs), `{modern_details}` (glass facades, rooftop gardens, digital signage), `{historical_palette}` (sepia and desaturated earth tones, hand-colored photograph quality), `{modern_palette}` (clean contemporary color, cooler blue-grays with warm accent), `{historical_atmosphere}` (coal haze, soft morning fog), `{modern_atmosphere}` (clear sky, light pollution glow at horizon), `{historical_sky}` (warm overcast), `{modern_sky}` (clear gradient blue)

**Recommended model:** NBP — spatial reasoning for architectural morphing and perspective consistency

### Nano Banana version:

```
A wide elevated view of {city_landmark_view}, divided vertically down the center into two eras. The left half depicts the scene in {historical_era}: {historical_details}, rendered in a muted {historical_palette} palette with {historical_atmosphere}. The right half shows {modern_era}: {modern_details} in a {modern_palette} palette under {modern_atmosphere}. At the center dividing line, elements morph organically across a narrow transition zone — a horse-drawn cart becomes a car, gas lamps become LED lights, cobblestones blend into asphalt, trees grow taller. The sky transitions from {historical_sky} on the left to {modern_sky} on the right. Both halves share the same geographic terrain and perspective. Camera angle roughly 30 degrees above street level. Format: 16:9.
```

---

## Fitness Boxing Campaign Collage

Use for sport and fitness brand campaigns — a dynamic 3-panel collage combining action, detail, and atmosphere around a boxing/combat sport theme.

<!-- Source concept: 3-panel fitness/boxing campaign collage with action and detail shots -->

```
Scene: three-panel horizontal collage on {canvas_color} canvas — left panel (35%), center panel (40%), right panel (25%), {divider_style} dividers, unified {overall_tone} color tone
Subject: {athlete_description} in a boxing/training context — same person across all panels
Important Details:
  Left panel (environment): wide shot of {gym_environment}, atmospheric — {atmosphere_detail}, equipment visible but out of focus, {athlete_description} as a silhouette or distant figure warming up, mood: anticipation
  Center panel (action): medium shot, {athlete_description} mid-{action_type}, captured at peak effort — {action_detail}, sweat visible on skin and {gear_description}, sharp focus on face showing {expression}, directional hard light from {light_direction} creating dramatic shadow on the opposite side of the face, slight motion trail on the {moving_element}
  Right panel (detail): extreme close-up of {detail_subject} — {detail_description}, texture dominates the frame, {detail_lighting}
  Grain: uniform {grain_level} across all panels
  Color: {color_treatment}
Use Case: fitness brand campaign, gym poster, sportswear ad, magazine editorial spread
Constraints: same athlete across all panels (consistent identity, gear, wraps), no text or logos, no sponsor branding, center panel is the visual anchor — should feel like the decisive moment, grain must be uniform not just added to one panel
```

**Key levers:** `{athlete_description}`, `{gym_environment}` (industrial boxing gym with heavy bags, outdoor concrete training yard, dimly lit basement ring), `{atmosphere_detail}` (chalk dust in backlight, steam from breath in cold air, golden light through high windows), `{action_type}` (throwing a cross, landing a hook on a heavy bag, rope-skipping), `{action_detail}` (fist connecting with bag creating visible impact ripple, rope frozen in arc above head), `{gear_description}` (red hand wraps, worn leather gloves, no gloves — taped knuckles), `{expression}` (focused intensity, controlled exhale, battle cry), `{detail_subject}` (taped knuckles against red canvas, worn boxing boot laces, sweat dripping from chin onto canvas), `{detail_description}` (each tape fiber visible, leather cracking at flex points, individual droplets mid-fall), `{color_treatment}` (desaturated with warm midtones, high-contrast monochrome with sepia, teal-and-orange split tone), `{canvas_color}` (matte black #0D0D0D, dark charcoal #1A1A1A), `{divider_style}` (thin white 2px, no dividers — edge bleed)

**Recommended model:** GPT Image 2 — identity consistency across panels and sweat/texture detail

---

## Lavender Smartphone Hero Ad

Use for tech product launch visuals — clean, color-dominant hero shots where a smartphone (or similar device) floats against a monochromatic gradient with soft 3D accent elements.

<!-- Source concept: smartphone product launch hero in monochromatic lavender with floating accent shapes -->

```
Scene: smooth gradient background from {color_light} to {color_dark}, no hard edges, studio void environment
Subject: {device_name} floating at slight {tilt_angle}-degree angle, screen facing camera showing {screen_content}, centered vertically but offset {horizontal_position} horizontally
Important Details: device renders with physically accurate {device_finish} — visible edge chamfer catching a thin highlight line, screen content crisp and legible at this scale, {accent_element_count} soft 3D shapes floating nearby (matte {accent_shape_color} {accent_shapes} — frosted glass or soft plastic appearance, each {accent_size}), shapes are out of focus at varying depths creating a layered composition, soft omnidirectional lighting with a subtle key from upper-left, gentle device shadow projected onto the gradient ({shadow_softness}), overall color palette stays within the {color_family} family — no complementary or clashing tones
  Bottom text area: "{HEADLINE}" in {headline_weight} {headline_font_style}, {headline_color}, centered below device
  Subtext: "{SUBHEADLINE}" in thin weight, {subtext_color}, below headline
Use Case: product launch hero, website header, retail POS, digital ad
Constraints: screen content must be sharp and readable, floating shapes must not obscure the device screen, no reflections of a studio environment on screen, gradient is smooth — no banding, device proportions must match a real smartphone (no stretched or squished body), text exactly as quoted
Quality: high
```

**Key levers:** `{device_name}`, `{color_light}` / `{color_dark}` (lavender #E6D5F5 to #7B4FA0, mint #D0F0E0 to #1B7A5A, coral #FFDDD2 to #C44536), `{device_finish}` (matte aluminum, polished titanium, frosted glass back), `{screen_content}` (a clean home screen with app icons, a camera app showing a landscape, a gradient wallpaper), `{accent_shapes}` (spheres, rounded pills, soft cubes, torus rings), `{accent_shape_color}` — same family as background but slightly lighter or more saturated, `{accent_size}` (golf-ball to grapefruit), `{HEADLINE}` / `{SUBHEADLINE}`, `{headline_color}` (white #FFFFFF, dark tint of the color family), `{color_family}` (lavender-purple, sage-green, warm terracotta), `{tilt_angle}` (5-15), `{horizontal_position}` (left third, center, right third)

**Recommended model:** GPT Image 2 (`quality: high`) — text rendering, screen content legibility, device accuracy

---

## Emerald Street Fashion Poster

Use for fashion drops, event announcements, or editorial magazine covers where bold typography and a street fashion figure share equal visual weight on a saturated color field.

<!-- Source concept: bold emerald fashion poster with oversized type and street style figure -->

```
Scene: solid {background_color} background (flat, no gradient), graphic poster composition split between typography (upper 55%) and figure (lower 60%, overlapping into the type zone)
Subject: {model_description} in {outfit_description}, full-body shot from low angle (worm's eye, approximately 15 degrees below eye level), standing with {pose_description}
Important Details: "{MAIN_TITLE}" in extra-bold extended {title_font_style}, {title_color}, filling the upper half — each letter approximately 20% of frame height, model's head and shoulders break in front of the bottom row of letters (depth layering), "{SUBTITLE}" in lightweight condensed type, {subtitle_color}, running along the bottom edge or lower-right corner, model lit by overcast flat light — even exposure, minimal shadow, fabric textures fully readable ({fabric_details}), shoes visible and grounded (not floating), {graphic_accents} if any
Use Case: fashion brand poster, event flyer, editorial magazine cover, retail window display
Constraints: title text fully legible — model overlap must not obscure more than one letter by more than 40%, no additional decorative elements unless specified in {graphic_accents}, background is flat solid color — no texture or pattern, "{MAIN_TITLE}" and "{SUBTITLE}" spelled exactly as given, model does not hold props unless specified
Quality: high
```

**Key levers:** `{background_color}` (emerald #006B3F, cobalt #0047AB, saffron #F4C430, hot pink #FF1493), `{model_description}`, `{outfit_description}` (oversized leather trench + chunky sneakers, cropped bomber + wide-leg trousers + platform boots), `{pose_description}` (wide stance with arms crossed, one hand adjusting collar, walking stride caught mid-step), `{MAIN_TITLE}` / `{SUBTITLE}`, `{title_font_style}` (geometric sans-serif, grotesque, stencil cut), `{title_color}` (#FFFFFF, #000000, cream #FFF5E1), `{subtitle_color}` (same as title but at 60% opacity), `{fabric_details}` (visible grain in leather, corduroy ridges, denim selvedge edge), `{graphic_accents}` (none, thin white border 20px from edge, small logo mark at bottom-left)

**Recommended model:** GPT Image 2 (`quality: high`) — typography rendering and figure-type layering

---

## Peacock Botanical Vintage Art Print

Use for decorative prints, packaging illustration, wallpaper design, or editorial art — a symmetrical composition combining a peacock with botanical elements in a vintage printmaking style.

<!-- Source concept: peacock botanical vintage symmetrical art print — ornamental and decorative -->

A symmetrical ornamental art print centered on a {peacock_variant} peacock in full tail display, viewed from {view_angle}. The tail feathers fan into a perfect semicircle filling the upper two-thirds of the frame, each eye-spot rendered with precise detail — iridescent {eye_colors} with fine barb texture. The peacock stands on a {base_element} at the composition's center axis. Flanking the bird symmetrically: {botanical_left} on the left mirrored by {botanical_right} on the right — leaves, stems, and blossoms curve inward framing the peacock. {additional_fauna} perch or fly near the upper corners. The entire composition sits on a {background_texture} background in {background_color}. Rendering style: {print_style} — visible {technique_marks}, rich but slightly flattened color as if from layered printing passes. Border: {border_style}. Color palette: {palette}. Format: 3:4.

**Key levers:** `{peacock_variant}` (Indian blue, white albino, green Java), `{view_angle}` (front-facing straight on, three-quarter turning left), `{eye_colors}` (deep blue #003366 and emerald #006B3F and gold #C9A84C, monochrome — all in shades of navy and silver), `{base_element}` (ornate stone pedestal, flowering branch, decorative tile floor), `{botanical_left}` / `{botanical_right}` (magnolia branches, trailing wisteria, passion flower vines, banksia stems), `{additional_fauna}` (two small butterflies, a dragonfly pair, none), `{background_texture}` / `{background_color}` (aged linen #F5F0E1, dark navy #0A1628, cream parchment #FDF5E6), `{print_style}` (hand-colored etching, woodblock print, chromolithograph), `{technique_marks}` (cross-hatching in shadows, visible plate tone, registration marks at corners), `{border_style}` (thin double-line art nouveau border, ornamental corner flourishes, simple single-line rectangle), `{palette}` (natural jewel tones — emerald, sapphire, gold on cream / limited three-color palette — teal, copper, black on ivory / muted earth tones — sage, terracotta, umber)

**Recommended model:** NB2 — image grounding for accurate peacock anatomy and botanical species

### Nano Banana version:

```
A symmetrical ornamental art print centered on a {peacock_variant} peacock in full tail display, viewed {view_angle}. Tail feathers fan into a perfect semicircle filling the upper two-thirds, each eye-spot rendered with iridescent {eye_colors} and fine barb texture. The peacock stands on a {base_element}. Flanking it symmetrically: {botanical_left} on the left mirrored by {botanical_right} on the right, stems and blossoms curving inward to frame the bird. {additional_fauna} near the upper corners. Background: {background_texture} in {background_color}. Style: {print_style} with visible {technique_marks} and slightly flattened color as from layered printing passes. Border: {border_style}. Palette: {palette}. Format: 3:4.
```
