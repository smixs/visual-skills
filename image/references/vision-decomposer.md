# Vision Decomposer — Image-to-Prompt Analysis

Use this reference when the user asks to analyze an image and convert it to a generation prompt: **style transfer**, **mood reference**, **"сделай промпт по этой картинке"**, **"перенеси стиль/образ"**, **"проанализируй кадр"**, **"image to prompt"**, **"reverse-engineer this look"**.

You become a **professional Vision Agent**. Your task is deep cinematic, psychological and optical-colorimetric analysis of the image, translating it into a perfect, highly detailed text prompt for generation.

The process has two strict steps. Do not skip Step 1. Do not freestyle Step 2.

---

## STEP 1 — DEEP DECOMPOSITION

Scan the image as **raw data** and extract facts based on:

- **Cinematic composition** — Bruce Block's visual structure
- **Color theory** — Itten
- **Perceptual psychology** — Arnheim
- **Directing references** — Spielberg / Scorsese / Tarantino
- **Cinematography & colorimetry** — Valentin Zheleznyakov

Evaluate the following four parameter blocks.

### 1. Subject — psychology and mise-en-scène

- **Who / What:** precise clothing (era, style, materials), age, skin texture, makeup / toning, micro-expressions.
- **Shot size (after Mascelli):** Extreme Long Shot (ELS), Long Shot, Medium Shot, Two-shot / Three-shot, Close-Up (CU), Choker CU, Extreme CU, Insert shot.
- **Directing & force placement (Blocking after Kenworthy):** isolating the character at the edge of the frame (anxiety), physical barriers, face turned away from camera, shooting from behind (effect of unknown / powerlessness). Height difference (Level Change) for dominance.
- **Kinetics & perceptual forces (Arnheim):** visual weight of the object, center of gravity. Internal tension of form (compression / stretching / twisting). Pose, plasticity, motion vectors. Imitation of swift action (motion blur) or monumental stillness.
- **Color and emotion (Itten):** psychological impact of the local color of the subject.
- **Gaze:** direction, eyeline anchor, interaction with the frame edges, look into the lens.

### 2. Environment — geometry and structure of space

- **Setting & Art Direction:** place, era, background, architecture, specifics of materials and surface textures (gloss, matte, rust).
- **Three-plane depth (Spielberg):** clear separation into Foreground (with leading details), Midground (action plane), Background.
- **Figure & ground (Arnheim):** degree of subject isolation, overlapping of forms, mass relationships. Use of reflections (mirrors, windows) to expand context.
- **Tonal & aerial perspective (Zheleznyakov):** drop in contrast, desaturation, washing out, shift toward cool (blue-cyan) tones in the background.
- **Frame geometry:** structural framework (axes of symmetry / asymmetry), claustrophobic compression, surface divisions. Illusion of depth via Foreground framing.

### 3. Lighting — chiaroscuro, color and contrast

- **Optical & visual contrast (Zheleznyakov):** ratio of lit and shadow areas (OVK). Depth and density of shadows. Exact local color vs. color modified by lighting (valeurs).
- **Lighting scheme:** Key, Fill, Backlight / Rim, Modeling. Rembrandt lighting, Chiaroscuro. Height, hardness (Hard / Soft) and type of source.
- **Broken light & reflexes (Zheleznyakov):** use of shadow masks (gobos), light through blinds / foliage, color reflexes from neighboring objects onto skin / clothing.
- **Tonality & color:** light key (High-key / Low-key). Threshold Silhouette. Itten's 7 contrasts. White balance (Daylight / Tungsten) and temperature contrast (warm light / cool shadows).

### 4. Tech & Cinematography — optics, filters and film texture

- **Camera (angles & viewpoint):** Angle (High angle, Low angle, Eye-level, Dutch tilt). Objective camera, Subjective, POV, Over-the-shoulder (OTS). Movement imitation (Push-in, Tracking shot).
- **Optics & DOF:** Focal length (wide-angle for distortion / coverage, telephoto for spatial compression). Depth of field. Rack focus, bokeh.
- **Optical filters & attachments (Zheleznyakov):** diffusion filters (Pro-Mist, Black Pro-Mist, Fog, Double Fog, Low Contrast) for highlight bloom (halation), skin softening, lowering of micro-contrast. Polarizers (cutting reflections).
- **Effects & texture:** Frame format (70mm, 35mm, IMAX). Exposure (motion blur). Stylization (Bleach Bypass). Film Grain, chromatic aberration.

---

## STEP 2 — PROMPT SYNTHESIS

Assemble the final prompt from Step 1 data.

Rules:
- Write **only keywords separated by commas, in English**.
- Describe **strictly what you see**. Do not invent new objects.
- **No filler.** Never write "The image shows...", "A picture of...", "I can see...".
- **Strict word order** (this formula is non-negotiable):

```
[Shot type, optics and angle], [Subject, mise-en-scène / blocking, visual weight, clothing and action], [Multi-plane environment (Foreground / Midground / Background), overlapping and geometry], [Lighting scheme, optical contrast, gobos and reflexes], [Color palette, temperature contrast and aerial perspective], [Color Grading, diffusion filters, film stock, textural artifacts]
```

---

## OUTPUT PROTOCOL

When the user gives you an image (or asks to reverse-engineer one), produce the answer in **two blocks**:

### Block 1 — Brief Analysis Log

```
Subject & Blocking: ...
Environment & Depth: ...
Lighting & Contrast: ...
Tech & Optics: ...
```

Each line: 1-2 sentences max. Just the extracted parameters.

### Block 2 — Final Prompt

A code block containing only the prompt text in English, assembled by the formula in Step 2:

````
```
<comma-separated keywords following the strict 6-segment formula>
```
````

After the prompt, append the standard image-skill output header (Model / Quality / Size) so the user can drop it straight into the generator.

---

## When to load this file

Load `vision-decomposer.md` whenever:
- The user attaches an image and asks for a prompt to **recreate / transfer / match** its style
- The user asks to **decompose, deconstruct, reverse-engineer** a visual reference
- The user says **"перенеси стиль", "сделай так же", "повтори образ", "проанализируй кадр", "разбери картинку на промпт"**
- Mood-board work: extracting cinematic DNA from a film still, ad frame, painting, photo

Do NOT load this for: pure generation requests where no reference image is given. For those, use the standard model files.
