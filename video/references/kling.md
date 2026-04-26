# Kling reference (Kuaishou)

## Contents

1. What Kling is
2. Versions and element limits
3. Prompt formula
4. Prompt length by model
5. Negative prompts (dedicated field, special rule)
6. Element Library and Element Binding (unique)
7. Motion Brush (unique)
8. Motion Control (2.6 Pro, unique)
9. Image-to-video rule
10. Failure modes and fixes
11. Skeleton and example

---

## 1. What Kling is

Strong at realistic physics, character animation, and consistency through reference images. Fast generation. Best for social-ready clips and repeat-character scenes. Limited audio. No JSON prompts.

## 2. Versions and element limits

Kling models vary widely in how many distinct elements they can handle in a single prompt. Overstuffing produces melting faces, broken hands, or static motion.

- Kling 1.6. Simplified prompts. Keep it very simple.
- Kling 2.1 Pro. 1080p at 30fps. Motion Brush. End frame control.
- Kling 2.5 Turbo Pro. Maximum 3-4 distinct elements.
- Kling 2.6 Pro. 5-7 elements. Motion Control.
- Kling 3.0. Strongest character and scene consistency.

If in doubt about the user's version, assume 2.6 Pro and cap at 5-7 elements.

## 3. Prompt formula

```text
Subject (with specific details)
+ Subject Movement (one clean verb phrase)
+ Scene (3-5 elements max)
+ Camera Language
+ Lighting
+ Atmosphere
```

Kling 3.0 five-layer structure.

```text
Scene -> Characters -> Action -> Camera -> Audio
```

Write as flowing prose. Kling dislikes fragmented tag-style inputs.

## 4. Prompt length by model

- Text-to-video. 50-80 words.
- Image-to-video. 20-40 words. Shorter, motion-focused.
- 2.5 Turbo Pro. 3-4 elements max.
- 2.6 Pro. 5-7 elements.
- 1.6. Keep it simple, minimal.

Long prompts = melted outputs. Compress ruthlessly.

## 5. Negative prompts (critical rule)

Kling has a dedicated negative prompts field. The field auto-interprets input as exclusion. Do not write "no X". Write the thing itself.

Bad. "no robots"
Good. "robots"

Bad. "no blurry faces, no distorted hands"
Good. "blurry faces, distorted hands, melted features"

Common effective negatives.

```text
low resolution, blurry, distorted hands, extra fingers, melted face, watermark, subtitles, logo, text overlay, jitter, shaking camera, deformed
```

Keep the list short. Long negative stacks reduce motion and detail.

## 6. Element Library and Element Binding (unique)

For character consistency across generations, Kling has an Element Library. Upload 3-4 reference images of the character from different angles.

Required angles.

- Front
- Side (profile)
- Three-quarter

Then in Image-to-Video settings, enable "Bind Elements" to lock features. This gives the AI a visual anchor that survives camera pans and light changes.

Source image rules.

- 1080p or higher.
- Even lighting. Avoid hard shadows. The AI can mistake them for permanent facial features.
- No text or watermarks.
- Clean uncluttered background.
- Centered subject.
- Well-contrasted.

## 7. Motion Brush (unique)

Animate up to 6 regions of a single image independently. Each region gets its own motion path.

Critical rule. The text prompt MUST match the brush motion. If you brush a river flowing and write "stagnant pond" the model tears itself apart. Align prompt verbs with brush directions.

## 8. Motion Control (2.6 Pro, unique)

Copy motion from a reference video. Use when you need specific performance or choreography (dance, martial arts, specific gait). The prompt then focuses on subject description only, the reference handles motion.

## 9. Image-to-video rule

Keep the prompt short (20-40 words). Focus only on motion. Do not re-describe static elements the model already sees.

Include explicit continuity cues. Kling responds well to "preserve X" instructions.

Example.

```text
Preserve silhouette and label text. Slow tracking shot from the side. She turns her head toward camera. Wind catches her hair. 35mm, golden hour rim light.
```

## 10. Failure modes and fixes

### Random camera drift in static scenes

Fix. Say "locked static frame" or "camera fixed, no movement."

### Prompt exceeds model capacity, output melts

Fix. Cut to model-appropriate element count. 3-4 for Turbo, 5-7 for 2.6 Pro.

### Character face changes between generations

Fix. Upload 3-4 reference images to Element Library. Use Bind Elements in the settings.

### Negative prompts ignored

Fix. Rewrite "no X" as "X" in the negative field.

### Motion Brush artifact

Fix. Check that the text prompt verbs match the brush direction. Rewrite the text if it contradicts the motion.

### Element overload melts hands

Fix. Simplify. Combine elements where possible. Cut secondary descriptions.

## 11. Skeleton

### Text-to-video

```text
[Subject with identity anchor]. [Subject movement in one clean verb phrase]. Scene. [3-5 environment elements]. Camera. [one movement + lens]. Lighting. [source + quality]. Atmosphere. [mood].

Negative field. blurry, distorted hands, extra fingers, melted face, watermark, subtitles, jitter.
```

### Image-to-video

```text
Preserve [silhouette / label / specific feature]. [Camera movement, one lens]. [One or two motion verbs]. [Atmospheric cue, light change].

Negative field. blurry, distorted hands, melted face, jitter.
```

### Worked example. Fashion, image-to-video

```text
Preserve silhouette and fabric texture. Slow lateral tracking, 85mm. She turns her head toward camera, exhales through her nose, hair catches golden hour wind. Warm rim light. Confident stillness.

Negative field. blurry, distorted hands, extra fingers, melted face, watermark, motion blur, jitter.
```
