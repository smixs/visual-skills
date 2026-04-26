# Fixes, checklist, and cross-model skeletons

## Contents

1. Continuity checklist (before final output)
2. Common failures and fixes
3. Cross-model prompt skeletons
4. Default negative constraints
5. Prompt compression order
6. Output format templates

---

## 1. Continuity checklist

Before sending a prompt to the user, verify.

- Same character across shots (face, body, hair).
- Same clothes across shots, exactly named.
- Consistent location logic.
- Object state progression makes sense (sausage in fridge -> on plate -> on fork -> on floor).
- No unwanted extra characters.
- No unwanted text or subtitles.
- No unwanted logos.
- Consistent age / body / face.
- No impossible hand-object action.
- No vague camera instructions ("cinematic camera").
- No vague lighting instructions ("beautiful light").
- No random stacking of director references.
- No contradictions.
- Palette is defined with concrete colors.
- Final image is explicitly stated.

If any item is missing, fix before sending.

---

## 2. Common failures and fixes

### One continuous take instead of montage

Fix.

```text
This must be a multi-shot sequence with visible hard cuts. Do not generate a single continuous take. Each beat uses a different angle and framing.
```

For Seedance specifically, add explicit `Cut to.` or `Camera cut to.` markers in the prompt body.

### Character face changes between shots

Fix.

```text
Preserve the exact character in every shot. Same face shape, same eye color, same hair, same clothing, same expression style. [repeat the full identity block]
```

For Kling. Use Element Binding with 3-4 reference images (front, side, three-quarter).

### Object disappears mid-scene

Fix.

```text
Track the object continuously. The same object remains visible or clearly implied in every beat.
```

Describe the object's state progression in one sentence. "The sausage moves. fridge -> pot -> fork -> floor."

### Weak drama. Scene feels flat.

Fix.

```text
Play the scene with full emotional seriousness. Treat the ordinary object as if it carries life-or-death meaning. No comedy pacing. No detached observation.
```

### Messy random cuts in fast montage

Fix.

```text
Use fast montage with clear readable action per cut. Every cut shows a distinct detail. face, hand, object, reaction, impact. Each cut must have a visible function.
```

### Dialogue too fast (Veo)

Fix. Cut the line. 8 seconds max of spoken text. Test by reading aloud at normal pace.

### Melting hands / extra fingers

For Kling. Add to negative field.

```text
distorted hands, extra fingers, melted face, deformed
```

For Seedance and Veo. Use positive phrasing.

```text
anatomically correct hands, clean finger separation, realistic proportions
```

### Lighting drifts between clips

Fix. Name the dominant source and direction and repeat it verbatim in every clip.

```text
Lighting constant. Cold fridge light as key from frame-right. Warm window spill as rim from frame-left. Same contrast ratio in every shot.
```

### Model ignores camera instruction

Fix. Move camera to the front of the prompt.

Bad. "A man opens a fridge. The camera is a slow push-in."
Good. "Slow 50mm push-in. A man opens the fridge."

### Weird AI-looking faces

Fix. Avoid style words like "hyperrealistic 8k masterpiece." These push the model into AI-art territory. Use production language instead.

```text
Shot on 50mm, natural skin texture, motivated lighting, documentary feel.
```

---

## 3. Cross-model prompt skeletons

### Seedance

```text
Subject. [identity block].
Motion. [one clear present-tense action].
Camera. Shot 1. [framing, lens, movement]. Cut to. Shot 2. [framing, lens, movement]. Cut to. Shot 3. [framing, lens, movement].
Environment. [location, time, props].
Lighting. [source, direction, quality, color].
Style. [realism level, genre reference].
Audio. [ambient, SFX]. (1.5+ only)
Continuity. [what must remain constant].

--resolution 1080p --duration 5 --camerafixed false
```

### Kling text-to-video

```text
[Subject with identity anchor]. [Subject movement]. Scene. [3-5 environment elements]. Camera. [one movement + lens]. Lighting. [source + quality]. Atmosphere. [mood].

Negative field. blurry, distorted hands, extra fingers, melted face, watermark, subtitles, jitter.
```

### Kling image-to-video

```text
Preserve [silhouette / feature / label]. [Camera movement, one lens]. [One or two motion verbs]. [Atmospheric cue, light change].

Negative field. blurry, distorted hands, melted face, jitter.
```

### Veo prose

```text
[Subject performing action] in [environment]. [Camera framing + lens + movement]. [Lighting direction + color]. [Style + mood + palette].

Audio: [ambient, SFX, music texture].
Says: [character] says, "[dialogue, max 8s of speech]."
SFX: [punctual sound events].

Duration: [4 / 6 / 8] seconds.
```

### Veo JSON

See `references/veo.md` section 6 for full schema.

---

## 4. Default negative constraints

Where negatives are supported (Kling field, Veo body text, Seedance 2.0 fragile).

```text
No subtitles. No on-screen text. No extra characters. No changing clothes. No changing face. No logos. No cartoon physics unless requested. No warm yellow tones unless requested. No random camera drift. No single-take when multi-shot is requested. No distorted hands. No extra fingers.
```

For Kling field. Rewrite as positive entities. "distorted hands, extra fingers, subtitles, logos, cartoon physics, random camera drift."

For Seedance 1.0. Invert all negatives to positive phrasings in the prompt body.

---

## 5. Prompt compression order

When a model performs better with shorter prompts (Kling 2.5 Turbo, Kling 1.6, any image-to-video), cut in this order.

1. Keep character continuity.
2. Keep story action.
3. Keep shot timecodes (where relevant).
4. Keep lighting.
5. Keep camera.
6. Keep editing grammar.
7. Keep sound.
8. Remove philosophy and meta-commentary.
9. Remove extra adjectives.
10. Remove director references.

The goal. Preserve the skeleton. Lose the perfume.

---

## 6. Output format templates

### Format A. Single prompt

One ready-to-copy prompt for one generation. Use the appropriate model skeleton.

### Format B. Multi-clip prompts

Sequence of self-contained prompts. Each one repeats the full continuity block. Label them `Clip 1 / 5`, `Clip 2 / 5`, etc.

Between clips, add a one-line note explaining how they cut together. "Clip 1 ends on his hand reaching into the fridge. Clip 2 opens on his hand already inside the fridge, same light."

### Format C. Storyboard (раскадровка)

Table with columns.

| Time | Shot | Function | Action | Camera | Light | Sound | Emotion |
|---|---|---|---|---|---|---|---|
| 0-1s | WS | Establish | Man walks to fridge | 35mm, slow push-in | Cold fluorescent overhead | Fridge hum | Exhaustion |
| 1-2s | MCU | Reveal | He opens fridge door | 50mm, static | Cold fridge light as key | Door seal pop | Anticipation |

Adjust row count to clip length.

### Format D. Prompt audit

Given a user prompt. Return six sections.

1. What works.
2. What breaks generation.
3. Missing direction (camera, light, continuity).
4. Continuity risks.
5. Model-specific mismatches (wrong syntax for the chosen model).
6. Stronger version. Rewritten prompt, ready to copy.

### Format E. Director treatment

For concept stage before any prompt is written.

- Core idea (one sentence)
- Emotional arc (three states)
- Visual motif (one recurring element)
- Rhythm (pace logic)
- Camera language (dominant grammar)
- Lighting (dominant source)
- Sound (texture)
- Ending image (final frame)

### Format F. Veo JSON

Structured scene-by-scene JSON. Use for complex continuity. See `references/veo.md` section 6.
