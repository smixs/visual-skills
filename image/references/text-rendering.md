# Text Rendering & Infographics

Универсальные стили, layout-типы, примеры. Применимо к обеим моделям, но детали рендера расходятся:

- **Nano Banana:** SOTA по 100+ языкам, multi-language в одном кадре, можно называть конкретные шрифты («Century Gothic 12px», «Brush Script»). См. [nano-banana.md](nano-banana.md).
- **GPT Image 2:** EXACT TEXT в `"..."` или ALL CAPS, добавляй «no extra words / no duplicate text», для мелкого текста — `quality: high`. См. [gpt-image.md](gpt-image.md).

## Prompt Structure

```
Create an educational infographic about [TOPIC].
Target Audience: [GRADE/LEVEL]
Content: [SPECIFIC FACTS/SEQUENCE]
Title: "[TITLE TEXT]"
Visual Style: [STYLE]
Layout: [LAYOUT TYPE]
Format: [ASPECT RATIO]
```

## Visual Styles

**Educational/Friendly:**
- Paper Cutout: construction paper collage look
- Claymation/Plasticine: 3D tactile, Wallace & Gromit style
- Kawaii/Cute Vector: rounded edges, pastel colors
- Storybook Watercolor: soft painted textures
- Chalkboard Art: white chalk on green/black
- Pixel Art (8-Bit): retro gaming nostalgia

**Technical/Professional:**
- Isometric 3D: video game map style, processes
- Blueprint/Schematic: white lines on blue
- Da Vinci Notebook: renaissance sketch, scientific
- UI/UX Wireframe: app blueprint style
- Dashboard: analytics screen with numbers

**Stylized:**
- Cyberpunk/Neon: dark + bright neon accents
- Graphic Novel/Comic Book: bold outlines, flat colors
- Vintage Science Poster: muted, aged paper, fine lines
- Pop Art (Warhol): high contrast, bold, dots
- Corporate Memphis/Flat Art: tech company style

**Specialized:**
- Subway/Transit Map: journey, connections
- IKEA Manual: wordless step-by-step
- Knolling (Flat Lay): objects at 90° angles, overhead
- Origami/Paper Folding: geometric, clean

## Layout Types

**Linear:**
- Horizontal Timeline: history, biography
- Step-by-Step Flow: recipes, experiments, processes
- Winding Roadmap: journey through topic

**Comparison:**
- Split Screen (Versus): instant contrast
- Comparison Matrix: multiple items, same criteria
- Before and After: cause and effect
- Venn Diagram: compare and contrast

**Hierarchical:**
- Pyramid: foundation to peak (Maslow, food pyramid)
- Funnel: filtering process (bill→law, sales)
- Iceberg: visible vs invisible (10% above, 90% below)

**Radial/Connected:**
- Hub and Spoke: core topic + attributes
- Tree/Branching Map: genealogy, taxonomy
- Concentric Circles: layers (Earth, proximity)

**Grid-Based:**
- Bento Grid: tidy boxes, modular
- Periodic Table Grid: items by type/family
- Comic Strip: narrative in scenes
- Jigsaw: pieces forming whole

**Spatial:**
- Isometric Map: 3D game world style
- Cross-Section (Cutaway): inside something solid
- Anatomical Call-out: labeling parts of whole
- Exploded View: parts hovering, showing assembly

## Examples

**Science - Water Cycle:**
```
Create educational infographic for Elementary Science.
Topic: The Water Cycle.
Content: Evaporation, Condensation, Precipitation, Collection.
Visual Style: Bright, colorful, 3D claymation style.
Layout: Circular flow diagram with arrows clockwise.
```

**History - Timeline:**
```
Create educational infographic for High School History.
Topic: Timeline of Ancient Egypt.
Content: Old Kingdom (Pyramids), Middle Kingdom (Arts), New Kingdom (Tutankhamun).
Visual Style: Papyrus texture, hieroglyphic icons, gold/sand palette.
Layout: S-curve roadmap flowing top to bottom.
```

**Literature - Iceberg:**
```
Create educational infographic for Sociology class.
Topic: Surface Culture vs Deep Culture.
Content: Above water (Food, Flags, Festivals). Below water (Body Language, Beliefs, Etiquette).
Visual Style: Paper Cutout Style, textured construction paper.
Layout: Iceberg diagram, tip = 10%, submerged = 90%.
```

**Comparison - Matrix:**
```
Create educational infographic for Elementary Science.
Topic: Inner vs Outer Planets.
Content: Compare across Surface Type, Size, Rings.
Visual Style: Kawaii/Cute Vector, pastel colors.
Layout: Comparison Matrix grid.
```

## Text-First Hack

For complex text in images, generate text FIRST, then ask for the image:
1. Ask the model to write/refine the text content
2. Then ask for an image with that exact text

This produces sharper, more accurate typography than cramming everything in one prompt.

## Font Control

Describe typography style or name the font directly:
- "Bold, white, sans-serif font"
- "Century Gothic 12px font"
- "Flowing, elegant Brush Script"
- "Heavy, blocky Impact font"
- "Thin, minimalist Century Gothic"

## Multilingual / Localization

Supports 10+ languages. Two approaches:

**Direct:** Write prompt in target language, text renders in that language.

**Translate:** Write prompt in one language, specify target:
```
Create this product ad. Render all text in Korean.
```

**Multi-language in one image:**
```
Line 1: "GLOW" in Brush Script
Line 2: "10% OFF" in Impact font
Line 3: "Your First Order" in Century Gothic
Then translate all text into Korean and Arabic.
```

## Tips

**Provide your own content:**
- Paste article text, video transcript, your notes
- More accurate than relying only on search

**Sketch-to-Image:**
- Draw messy layout sketch on paper
- Upload with prompt: "Use layout from attached image"

**Iterative editing:**
- "Leave everything else exactly the same, but change [X]"
- Annotate downloaded image, upload back as reference
