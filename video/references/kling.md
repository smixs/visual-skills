# Kling reference (Kuaishou)

## Contents

1. What Kling is
2. Versions and element limits
3. **Kling 3.0 — multi-shot, native audio, 15s (read first if user is on 3.0)**
4. Prompt formula (1.x – 2.x)
5. Prompt length by model
6. Negative prompts (dedicated field, special rule)
7. Element Library and Element Binding (unique to 1.x – 2.x)
8. Motion Brush (unique)
9. Motion Control (2.6 Pro, unique)
10. Image-to-video rule
11. Failure modes and fixes
12. Skeleton and example

---

## 1. What Kling is

Strong at realistic physics, character animation, and consistency through reference images. Fast generation. Best for social-ready clips and repeat-character scenes.

**Kling 3.0** changed the model's positioning fundamentally — it now competes with Seedance on multi-shot output (up to 6 shots per generation) and with Veo on native dialogue and lip-sync. See section 3.

## 2. Versions and element limits

Kling models vary widely in how many distinct elements they can handle in a single prompt. Overstuffing produces melting faces, broken hands, or static motion.

- **Kling 1.6.** Simplified prompts. Keep it very simple.
- **Kling 2.1 Pro.** 1080p at 30fps. Motion Brush. End frame control.
- **Kling 2.5 Turbo Pro.** Maximum 3-4 distinct elements.
- **Kling 2.6 Pro.** 5-7 elements. Motion Control. Element Binding for character consistency.
- **Kling 3.0.** Multi-shot in one generation (up to 6 shots). Native audio with dialogue and lip-sync. 15s continuous output. Strongest character and scene consistency. Two tiers: v3/pro and v3/standard.

If in doubt about the user's version, ask. The prompting protocol differs between 1.x – 2.x (sections 4-9) and 3.0 (section 3).

## 3. Kling 3.0 — multi-shot, native audio, 15s

Kling 3.0 is a different beast. It understands cinematic intent, not just visual descriptions. Prompts read like scene directions, not object lists.

### What changed vs 2.x

| Capability | 1.x – 2.6 | **3.0** |
|---|---|---|
| Multi-shot in one generation | No (one continuous take) | **Yes — up to 6 shots** |
| Native audio | Limited / off | **Yes — dialogue, ambient, voice tone** |
| Lip-sync | No | **Yes — coherent across multi-character scenes** |
| Max duration | 5-10s | **Up to 15s** |
| Character labeling | Via Element Library + reference images | **Via in-prompt `[Character A: ...]` tags** (still supports references) |
| Cinematic language understanding | Partial | **Full — reads "shot-reverse-shot", "POV", "tracking shot", "macro close-up"** |

### Five-layer prompt structure

```text
Scene  →  Characters  →  Action  →  Camera  →  Audio
```

Write each layer as flowing prose with explicit labels.

### Anchor subjects early

Introduce every character and key object at the **start** of the prompt, before any shot description. Use unique consistent identifiers — the same label survives across all shots:

```text
[Character A: Exhausted Partner — late 40s, gray-streaked beard, navy peacoat, hollow eyes]
[Character B: Female Investor — early 30s, sharp blazer, calm posture]
```

Then refer to them as "Character A" / "Character B" inside shot descriptions. This locks identity better than re-describing the character each shot.

### Multi-shot syntax (think in shots, not clips)

```text
[Character A: ...]
[Character B: ...]

Master intent: tense negotiation in a glass-walled office at dusk.

Shot 1 (0-3s). Wide tracking shot. Character A enters frame from left, crosses to the table.
Shot 2 (3-6s). Profile close-up on Character A. He sets down a brown leather folder.
Shot 3 (6-9s). Shot-reverse-shot. Cut to Character B's face. She does not blink.
Shot 4 (9-12s). Macro insert on her hand tightening around a fountain pen.
Shot 5 (12-15s). Two-shot, low angle, both reflected in the glass wall behind them.

Camera. Slow, deliberate. Sony FX6 feel, 35mm and 85mm.
Lighting. Cold blue dusk through floor-to-ceiling windows. Single amber desk lamp.
Audio. Distant city ambience. No music. Footsteps on hardwood. Pen clicks on paper.
```

Each shot must answer: **framing + subject + motion**. Empty shot descriptions ("static frame, ambient mood") collapse into one continuous take.

### Dialogue protocol (P1-P4)

For any speaking scene, follow these four rules. The fal.ai guide calls them P1, P2, P3, P4.

**P1. Structured naming.** Use unique identifiers per character.
- ✓ `[Character A: Black-suited Agent]` and `[Character B: Female Assistant]`
- ✗ "[Agent] says... Then, he says..."

**P2. Visual anchoring before dialogue.** Bind dialogue to a unique action first.
- ✓ "Character A pulls a folded note from his pocket and reads aloud: 'It's not what you think.'"
- ✗ "Character A says 'It's not what you think.'" (no visual anchor → lip-sync drifts)

**P3. Voice tone in the tag.** Assign emotion / texture inline.
- ✓ `[Character A, raspy deep voice]: "We're out of time."`
- ✓ `[Character B, clear fearful voice]: "Don't open it."`
- ✗ `[Man]: "We're out of time."` (vague — model picks a generic voice)

**P4. Temporal control between lines.** Use linking words to prevent dialogue from merging.
- ✓ "Character A: 'I won't ask again.' **Immediately,** Character B: 'You don't have to.'"
- ✗ Two consecutive `[Character X]: "..."` lines with no transition (model overlaps them)

### Image-to-video on 3.0 — lock first, then move

The input image serves as the anchor for identity, layout, and on-image text. Keep the prompt short and motion-focused. Describe **how the scene evolves from the image**, not what is in the image.

```text
Preserve identity, wardrobe, and the storefront sign exactly.
[Character A: same person from the image]
Shot 1 (0-2s). She turns her head toward camera, exhales.
Shot 2 (2-5s). Slow push-in to a tight close-up. Wind catches her hair.
Audio. Distant traffic, wind through awnings, a soft bell from inside the shop.
```

### Cinematic vocabulary that 3.0 actually understands

Use these terms directly — the model treats them as instructions, not flavor:

- Framing: profile shot, three-quarter, macro insert, two-shot, OTS, POV, low angle, high angle, Dutch
- Edits: shot-reverse-shot, match cut, smash cut, J-cut, L-cut
- Camera moves: tracking, dolly, push-in, pull-out, whip pan, crane, handheld
- Lens feel: 35mm, 50mm, 85mm, 100mm macro, anamorphic 40mm

### Default model choice

If the task hits any of these — **use Kling 3.0 over earlier Kling**:
- Multi-shot dialogue scenes
- 10-15s continuous narrative
- Lip-sync required
- Multi-character with distinct voices
- Image-to-video where text on the image must stay legible

For everything else (single clip, no dialogue, < 10s, character lock via reference images, Motion Brush) — older versions still work and are cheaper.

## 4. Prompt formula (1.x – 2.x)

For 1.6, 2.1 Pro, 2.5 Turbo Pro, 2.6 Pro:

```text
Subject (with specific details)
+ Subject Movement (one clean verb phrase)
+ Scene (3-5 elements max)
+ Camera Language
+ Lighting
+ Atmosphere
```

Write as flowing prose. Kling 1.x – 2.x dislikes fragmented tag-style inputs.

For Kling 3.0, use the multi-shot structure from section 3 instead.

## 5. Prompt length by model

- 1.6. Keep it simple, minimal.
- 2.5 Turbo Pro. 3-4 elements max. 50-80 words.
- 2.6 Pro. 5-7 elements. 50-80 words.
- 3.0. Longer prompts welcome — multi-shot needs explicit structure (see section 3). Plan ~30-60 words per shot.
- Image-to-video (any version). 20-40 words. Shorter, motion-focused.

Long prompts on 1.x – 2.x = melted outputs. Compress ruthlessly. On 3.0, structure beats length.

## 6. Negative prompts (critical rule)

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

## 7. Element Library and Element Binding (1.x – 2.x)

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

For Kling 3.0 — Element Library still works, but the in-prompt `[Character A: ...]` labels (see section 3) are usually enough on their own.

## 8. Motion Brush (unique)

Animate up to 6 regions of a single image independently. Each region gets its own motion path.

Critical rule. The text prompt MUST match the brush motion. If you brush a river flowing and write "stagnant pond" the model tears itself apart. Align prompt verbs with brush directions.

## 9. Motion Control (2.6 Pro, unique)

Copy motion from a reference video. Use when you need specific performance or choreography (dance, martial arts, specific gait). The prompt then focuses on subject description only, the reference handles motion.

## 10. Image-to-video rule

Keep the prompt short (20-40 words). Focus only on motion. Do not re-describe static elements the model already sees.

Include explicit continuity cues. Kling responds well to "preserve X" instructions.

Example.

```text
Preserve silhouette and label text. Slow tracking shot from the side. She turns her head toward camera. Wind catches her hair. 35mm, golden hour rim light.
```

For Kling 3.0 image-to-video — see section 3 ("Image-to-video on 3.0 — lock first, then move").

## 11. Failure modes and fixes

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

### Kling 3.0 collapses multi-shot into one continuous take

Fix. Make shot boundaries explicit: `Shot 1 (0-3s). ... Shot 2 (3-6s). ...`. Each shot description must include a different framing or camera angle. If two adjacent shots share both framing and angle, the model merges them.

### Kling 3.0 dialogue lip-sync drifts

Fix. Apply P2 — bind dialogue to a unique visual action ("Character A pulls a folded note from his pocket and reads aloud:") before the line itself. Then add P4 linking words ("Immediately,") between consecutive lines.

### Kling 3.0 picks the wrong voice

Fix. Apply P3 — put voice tone inside the speaker tag: `[Character A, raspy deep voice]:`. Generic `[Man]:` / `[Woman]:` tags get a generic voice.

## 12. Skeleton

### Text-to-video (1.x – 2.x)

```text
[Subject with identity anchor]. [Subject movement in one clean verb phrase]. Scene. [3-5 environment elements]. Camera. [one movement + lens]. Lighting. [source + quality]. Atmosphere. [mood].

Negative field. blurry, distorted hands, extra fingers, melted face, watermark, subtitles, jitter.
```

### Image-to-video

```text
Preserve [silhouette / label / specific feature]. [Camera movement, one lens]. [One or two motion verbs]. [Atmospheric cue, light change].

Negative field. blurry, distorted hands, melted face, jitter.
```

### Worked example. Fashion, image-to-video (2.6 Pro)

```text
Preserve silhouette and fabric texture. Slow lateral tracking, 85mm. She turns her head toward camera, exhales through her nose, hair catches golden hour wind. Warm rim light. Confident stillness.

Negative field. blurry, distorted hands, extra fingers, melted face, watermark, motion blur, jitter.
```

### Multi-shot with dialogue (Kling 3.0)

```text
[Character A: Investigator — late 30s, navy raincoat, tired blue eyes, three-day stubble]
[Character B: Witness — early 20s, oversized hoodie, hands wrapped around a paper cup, eyes red from crying]

Master intent: a 12-second interrogation in a fluorescent-lit precinct break room at 2am. The investigator holds back, the witness breaks.

Shot 1 (0-3s). Two-shot, eye level, 35mm. Character A sits across from Character B. Static frame.
Shot 2 (3-6s). OTS over Character A's shoulder. Character B's hands tighten on the paper cup.
Shot 3 (6-9s). Profile close-up on Character A. He slides a photo across the table.
[Character A, low even voice]: "You were there."
Shot 4 (9-12s). Reverse — close-up on Character B. She does not look up.
Immediately, [Character B, fragile broken voice]: "I didn't see anything."

Camera. Locked frames, no movement except the slide of the photo. Sony FX6 feel.
Lighting. Cold overhead fluorescent, slight flicker. Pale skin, hard shadows under the eyes.
Audio. Distant police radio chatter, the buzz of the fluorescent tube, a vending machine humming in the corridor. No music.

Negative field. blurry, distorted hands, extra fingers, melted face, watermark, subtitles, jitter, dialogue overlap.
```
