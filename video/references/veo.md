# Veo reference (Google)

## Contents

1. What Veo is
2. Versions and specs
3. Prompt structure and length
4. Dialogue syntax (critical, unique)
5. SFX syntax
6. JSON prompts (powerful, unique)
7. Image-to-video (Veo 3.1)
8. Reference ingredients (3.1)
9. Failure modes and fixes
10. Skeleton and example

---

## 1. What Veo is

Google's cinematic video model with NATIVE synchronized audio. The only major generator that creates dialogue, SFX, and music in sync with the video and does lip-sync natively. Best for commercial polish, narrative with dialogue, and cinematic audio.

## 2. Versions and specs

- Veo 3. Text-to-video, native audio, 4 / 6 / 8 second clips.
- Veo 3.1. Adds image-to-video with First Frame, improved audio, reference ingredients, stronger motion coherence.

Duration. 4, 6, or 8 seconds.
Dialogue budget. Max 8 seconds of spoken audio per clip.

## 3. Prompt structure and length

Order matters. Lead with subject and camera. Quality modifiers go at the end.

```text
[Subject / Action]
+ [Environment / Setting]
+ [Camera / Shot Type / Lens]
+ [Lighting / Atmosphere]
+ [Style / Quality]
+ [Audio]
+ [Duration]
```

Sweet spot. 50-200 words.

- Shorter prompts = more creative latitude, less control.
- Longer prompts = tighter control, higher risk of contradictions.

## 4. Dialogue syntax (critical)

Veo is the only model that renders synced lip movement and voice. The syntax matters.

### Required format

Double quotes + lead-in verb (says, whispers, shouts, mutters, asks).

```text
A woman says, "Welcome to the future."
He whispers, "Don't move."
She shouts, "Get out!"
```

Colon after the lead-in verb works too and is often more reliable.

```text
A woman says: "Welcome to the future."
```

### Voice character modifiers

Place modifiers before the lead-in verb.

```text
He says in a weary voice, "We are fine. We are fine."
She whispers nervously, "I don't want to be here."
He shouts excitedly, "We did it!"
```

### Timing rule

Maximum 8 seconds of spoken audio. Cram too many words into a 5s clip and the delivery speeds up unnaturally. Cut the line until it fits.

## 5. SFX syntax

Three supported formats. Mix as needed.

```text
SFX: thunder cracks in the distance
Audio: rain on tin roof, distant traffic, one slow breath
(a loud thunderclap)
(key turning in a lock)
(wet footsteps on concrete)
```

Use labels `Audio:`, `Says:`, `SFX:` to separate sound direction from visual direction. The model needs an explicit signal that audio should be generated.

## 6. JSON prompts (powerful, unique)

Veo parses structured JSON. This prevents "concept bleed" where describing mood accidentally changes object colors. Use JSON for complex scenes with strict continuity needs.

### Full schema

```json
{
  "version": "veo-3.1",
  "output": {
    "duration_sec": 8,
    "fps": 24,
    "resolution": "1080p",
    "aspect_ratio": "16:9"
  },
  "global_style": {
    "look": "cinematic naturalism",
    "color": "cold blue-gray palette, desaturated skin",
    "mood": "quiet domestic tragedy",
    "reference": "Fincher-style motivated camera"
  },
  "continuity": {
    "characters": [
      {
        "id": "man",
        "description": "40s, tired eyes, stubble, dark blue t-shirt, grey sweatpants, barefoot"
      }
    ],
    "props": ["empty refrigerator", "single sausage", "chipped white plate"],
    "lighting_constant": "cold fridge light as key"
  },
  "scenes": [
    {
      "id": "01",
      "start": "0.0",
      "end": "3.0",
      "shot": {
        "type": "medium close-up",
        "framing": "eye-level, slightly offset",
        "camera": "slow push-in, 50mm"
      },
      "action": "He opens the fridge. His face catches the cold light. His eyes stop on the empty shelf.",
      "environment": "small kitchen, 3am, rain outside window",
      "lighting": "cold fridge light as key, warm window spill as rim",
      "audio": "fridge hum, distant rain, one stomach growl"
    },
    {
      "id": "02",
      "start": "3.0",
      "end": "8.0",
      "shot": {
        "type": "extreme close-up",
        "framing": "macro insert on hand",
        "camera": "static, 100mm macro"
      },
      "action": "His hand hovers over a single sausage. He picks it up slowly, exhales.",
      "environment": "inside the fridge",
      "lighting": "cold fridge light, high contrast",
      "audio": "quiet breath, soft plastic crinkle"
    }
  ]
}
```

### When to use JSON

- Multiple scenes in one generation.
- Strict character continuity across shots.
- Complex props that must stay the same color and size.
- When a prose prompt kept changing subject colors when you added mood words.

Not every Veo prompt needs JSON. For simple clips, prose is faster and often better.

## 7. Image-to-video (Veo 3.1)

Uses the static image as First Frame. Prompt guides motion and sound.

Rules.

- Do not re-describe static elements.
- Describe only motion, camera, light change, and audio.
- Add "maintain the subject from the first frame" to protect identity.

Example.

```text
Maintain the subject from the first frame. Slow push-in, 50mm. She exhales, her eyes shift to the left, one strand of hair falls across her forehead. Warm rim light grows stronger.

Audio: soft breath, distant traffic, one door closing in the next room.
Duration: 6 seconds.
```

## 8. Reference ingredients (3.1)

Upload multiple reference images (character, location, prop) and tag them in the prompt.

```text
The character from reference_1 walks into the location from reference_2 holding the object from reference_3.
```

Use when you need a specific character in a specific place with a specific object.

## 9. Failure modes and fixes

### Dialogue speeds up unnaturally

Fix. Cut the line to fit 8 seconds of natural speech. Test by reading aloud.

### Audio missing from output

Fix. Add explicit `Audio:`, `SFX:`, or `Says:` labels. Do not assume the model will infer audio from visual description.

### Camera direction ignored

Fix. Lead the prompt with camera. "Wide aerial shot" at the start beats "cinematic camera work" in the middle.

### Character color changes when mood words are added

Fix. Switch to JSON prompt. Lock the character description in the continuity block. Keep mood in global_style where it cannot bleed into object colors.

### Lip-sync off

Fix. Check the lead-in verb. "She says, ..." outperforms just quoted speech alone. Colon form often more reliable than comma.

### Prompt too long, model cherry-picks

Fix. Compress to the 50-100 word range. Or switch to JSON which handles length better because of structural separation.

## 10. Skeleton

### Prose version

```text
[Subject performing action] in [environment]. [Camera framing + lens + movement]. [Lighting direction + color temperature]. [Style + mood + palette].

Audio: [ambient sounds, SFX, music texture].
Says: [character] says, "[dialogue, max 8 seconds of speech]."
SFX: [punctual sound events].

Duration: [4 / 6 / 8] seconds.
```

### JSON version

See section 6. Copy the schema and fill in.

### Worked example. Commercial hero shot

```text
A woman in a cream silk blouse stands in front of a morning window, lifting a ceramic coffee cup to her lips. Medium close-up, 85mm, slow push-in. Warm window key from frame-left, soft bounce fill from frame-right. Cinematic naturalism, creamy palette, shallow depth of field.

Audio: distant city ambience, ceramic clink, one slow breath.
Says: She whispers to herself, "One more minute."
SFX: (spoon tapping ceramic at 2 seconds).

Duration: 6 seconds.
```
