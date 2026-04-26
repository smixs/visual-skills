# Image Editing

Универсальные паттерны. Логика edit'а различается по моделям:

- **Nano Banana:** conversational, без масок. «Keep X same, change Y». Хорошо понимает физику и материалы.
- **GPT Image 2:** двухколоночная логика **Change / Preserve / Constraints**. Preserve list повторять каждую итерацию, иначе drift. Опционально `mask_image_url` для точечных edit'ов. Лучшая identity preservation. См. [gpt-image.md](gpt-image.md#editing--двухколоночная-логика).

Общее правило: **один edit за итерацию**, не пытайся менять всё разом.

## Object Removal
```
Remove [OBJECT] from this image.
Fill with [LOGICAL REPLACEMENT] matching surroundings.
Keep [PRESERVED ELEMENTS] exactly the same.
```

Examples:
- "Remove tourists, fill with cobblestones"
- "Remove car, extend street naturally"

## Object Addition
```
Add [OBJECT] to this image.
Position: [LOCATION]
Style: matching existing lighting
Scale: [RELATIVE SIZE]
```

## Lighting Control
```
Change lighting to [NEW LIGHTING].
Keep subject and composition same.
```

Vocabulary:
- Golden hour / sunset / warm backlight
- Overcast / soft / diffused
- Night / dramatic / single source
- Rim lighting / silhouette

## Seasonal/Weather
```
Turn scene into [SEASON/WEATHER].
Keep architecture exactly same.
Adjust: [snow/leaves/reflections/sky]
```

## Colorization

**Photo:**
```
Colorize this B&W photograph.
Era-appropriate colors for [DECADE].
Skin tones: natural, realistic
```

**Manga:**
```
Colorize this manga panel.
Style: [vibrant anime / muted realistic]
Effects: [glowing/neon] for energy elements
Maintain: line art integrity
```

## Restoration
```
Restore this damaged photograph.
Fix: [tears/scratches/fading/stains]
Enhance: sharpness, contrast
Preserve: original character and grain
```

## Localization
```
Translate all [SOURCE] text to [TARGET].
Keep everything else same.
Maintain: font style, sizing, position
```

Cultural adaptation:
```
Localize this [ORIGINAL] ad to [TARGET MARKET].
Background: [NEW LOCATION]
Translate: text to [LANGUAGE]
Keep: brand elements, core composition
```

## Physics-Aware

NBP understands materials:
```
Fill this glass with [LIQUID].
Add: refraction, meniscus, condensation
Match: existing lighting
```

```
Add [MATERIAL] texture to [SURFACE].
Properties: [matte/glossy], [rough/smooth]
```

## Conversational Refinement

After initial edit:
- "Make it warmer"
- "Increase contrast"
- "Soften the edges"
- "Add more detail to shadows"
