# Seedance reference (ByteDance)

## Contents

1. What Seedance is
2. Versions and specs
3. CLI parameters
4. The Details Law (read first)
5. 6-step prompt formula (quick)
6. Production-grade skeleton (11 blocks) — for dramatic / multi-shot work
7. The 5-second shot timeline (rhythm template)
8. Multi-shot syntax (unique capability)
9. Anti-mush guard block (when Seedance smears the cuts)
10. `@img1` character reference syntax
11. Camera movements (9 presets)
12. Negative prompts handling
13. Image-to-video rule
14. Audio (1.5+)
15. Failure modes and fixes
16. Worked example. 15-second tragicomedy as 3 × 5s clips
17. Seedance 2.5 — the 30-second single-pass clip

---

## 1. What Seedance is

A ByteDance video model with the UNIQUE ability to generate several distinct shots in ONE generation. The only major model that can pack a mini-montage inside a single 5-10s clip. Good cinematic motion, strong at ads and short narrative.

## 2. Versions and specs

- Seedance 1.0 Pro. 1080p, 5-10s (API up to 12s). Strong multi-shot.
- Seedance 1.0 Lite. 720p, faster, cheaper.
- Seedance 1.5 Pro. Native audio and lip-sync added.
- Seedance 2.0. Improved motion, better audio, 9 camera movement presets, limited negative prompt support, up to 12 reference inputs via `@` tags. Since June 2026: native 4K, 10-bit color. 2.0 Mini: ~2× faster, ~30% cheaper, for drafts and batches.
- **Seedance 2.5** (API since July 2026). Native 30-second single-pass clip (no stitching), up to 50 multimodal reference inputs (images + video + audio + style guides), 3D white-box camera blockout, localized re-draw of part of the frame without touching motion/camera/light, 11 prompt languages. See section 17.

Resolutions. 480p, 720p, 1080p; 2.0/2.5 add native 4K.
Aspect ratios. 16:9, 4:3, 1:1, 3:4, 9:16, 21:9, 9:21.
Frame rate. 24-30 fps.

**Model pick within the family:** people-centric drama with faces → 1.5 Pro (2.0/2.5 aggressively filter human faces and celebrity-adjacent content after the 2026 deepfake crackdown; for face-heavy work Kling or Veo are safer). Scenes, architecture, product, montage → 2.0. One continuous 15-30s arc or heavy reference kits → 2.5. Cheap drafts → 2.0 Mini, then re-render keepers high.

## 3. CLI parameters

Append at the end of the prompt.

```text
--resolution 1080p --duration 5 --camerafixed false --seed 42
```

- `--resolution`. 480p | 720p | 1080p
- `--duration`. 2 to 12 (Pro)
- `--camerafixed`. true locks the camera. false allows movement.
- `--seed`. for reproducibility

## 4. The Details Law (read this first)

> **Details intensify emotion. Laziness kills the prompt.**

Seedance does not render abstractions. It renders **physical specifics**. Every adjective must be a sensory fact. Every emotion must be a body. Every shot must own at least three concrete details:

1. **One environmental pressure.** Cold blue refrigerator light. Steam off boiling water. Wet asphalt. Flickering fluorescent. Dripping tap. Curtain breathing in the AC.
2. **One physical micro-action.** Jaw locks. Finger taps the counter. Knuckles whiten on the fork. Lips press into a line. He swallows hard.
3. **One sound anchor or visual motif.** Stomach growl at 2.3s. Reflection in the dark phone screen. Rain hitting the same windowpane.

If a shot has none of these — it is filler. Delete it or rewrite it.

Banned, lazy phrasing that produces mush:
- "cinematic, professional, high quality, masterpiece"
- "beautiful lighting"
- "epic scene"
- "amazing visuals"
- "he is sad / he is angry" (with no physical translation)

This rule is hard. Multi-shot prompts on Seedance fail not because of the model, but because the writer was lazy on a single shot. One thin shot drags the whole sequence down.

## 5. Six-step prompt formula (quick scenes)

For single-shot 5s clips with one clear action.

```text
Subject. [Who or what]
Motion. [Present-tense verb, one clear action]
Camera. [Movement + framing + lens]
Environment. [Where, props, atmosphere]
Lighting. [Direction + quality + color]
Style. [Realism level, genre reference]
```

Write in full sentences, not tags. Seedance prefers clear grammatical prose. For dramatic / multi-shot / character-locked work, **use the production-grade skeleton in section 6 instead.**

## 6. Production-grade skeleton (11 blocks)

Use this for any dramatic piece, multi-shot ad, music-video segment, or character-locked clip. Each block answers a specific failure mode. Skipping a block reintroduces that failure.

```text
[1] Character lock.
    Use @img1 as the main character reference and preserve the exact same person
    across the whole clip: <face shape, eye color, hair, facial hair, build, distinctive
    features>. Dress him in <exact wardrobe>. No nudity. No glasses (unless reference).
    No extra characters.

[2] Length + genre + editing intent.
    Generate a <duration>-second multi-shot <genre> sequence with <fast / slow / staircase>
    dynamic editing.

[3] Story (one paragraph).
    <Concrete physical events of this clip in present tense. What changes from start to
    end. Name the break point.>

[4] Visual style.
    <Palette, contrast, grain, color temperature, what to avoid (e.g. "no warm yellow
    tones"). Texture cues — realistic skin, food detail, fabric, surfaces.>

[5] Camera style.
    <Camera body / look (e.g. Sony FX3 handheld). Lenses with purpose:
    35mm / 50mm for medium, 85mm for emotional close-ups, 100mm macro for inserts,
    24mm for wide silhouettes. Handheld micro-shake or static. Strict cuts between
    shots. No continuous take.>

[6] Editing style.
    <Hard cuts vs match cuts. Rhythmic escalation. Where the pause lands. Where the
    impact hits. The rhythmic staircase: long → shorter → shorter → pause → impact.>

[7] Audio.
    <Diegetic sounds in order: ambient, micro-actions, impact, silence moment, final
    cue. Examples: stomach growl, refrigerator hum, fork clink, wet thud, abrupt
    silence, distant city ambience. No dialogue / No subtitles / No on-screen text.>

[8] Shot-by-shot timeline.
    Shot 1, 0.0–X.X sec: <framing, lens, camera move, action, environment detail,
                           emotion translated into body>.
    Shot 2, X.X–Y.Y sec: <...>.
    ...
    (See section 7 for the 5-second rhythm template.)

[9] Lighting (recap and specifics).
    <Main source, fill, rim. Direction. Color temperature. What it carries
    psychologically — judgment, isolation, hope, grief.>

[10] Composition.
    <Where the subject sits in frame across shots. Negative space. Reflections.
    Silhouettes. Foreground obstruction. The final image must be named.>

[11] Output specs.
    <Exact duration. Aspect ratio. Realism level. CLI: --resolution 1080p
    --duration 5 --camerafixed false>
```

Why 11 blocks and not 6? Each block prevents one specific Seedance failure: identity drift, one-take collapse, mood smear, lens chaos, audio mismatch, drift on rhythm. Cheap insurance.

## 7. The 5-second shot timeline (rhythm template)

For a 5-second multi-shot clip, the model performs best with **5 shot beats** following a dramatic micro-arc. Use this timing as the default scaffold:

```text
0.0–0.8 sec  | Establish     | extreme close-up or insert that anchors emotion / situation
0.8–1.6 sec  | Action        | medium shot, hero moves or reacts
1.6–2.5 sec  | Turn          | new framing reveals the shift (POV, OTS, rack focus)
2.5–3.6 sec  | Reaction      | tight close-up, slow push-in, emotion lands on the body
3.6–5.0 sec  | Climax / hero | hero shot, low angle, slow-mo if earned, final image
```

For 10s clips, double the structure or insert one pause before the climax (the pause beats speed). For 15s+ stories, split into 3 × 5s clips and stitch in the editor — Seedance is more reliable in shorter generations than one long take.

## 8. Multi-shot syntax (unique)

Seedance reads explicit cut markers inside a single prompt and generates distinct shots connected by visible cuts. This is its strongest card. Use it when you need montage in a single generation.

Supported cut markers.

```text
Shot 1. [description]
Cut to. [description]
Camera cut to. [description]
Camera switching. [description]
Lens switch to. [description]
```

Inline timeline syntax.

```text
[Shot A description] -> Cut to -> [Shot B description] -> Camera cut to -> [Shot C description]
```

Example.

```text
Shot 1. Medium close-up on a tired man in a kitchen. He opens the refrigerator.
Cut to. Macro insert. His hand reaches toward a single sausage on an empty shelf.
Cut to. Over-the-shoulder shot. The fridge light paints his face cold blue.
```

Use 2-3 shots per 5-second clip for tight cinematic montage, 4-5 shot beats only when each beat is short and physically distinct (see section 7). Hard cap: 5 shots per generation — beyond that the model drops or compresses shots. Size the duration to the shot count (4 shots need 10-15s, not 5s). Every shot must share an anchor with its neighbors — same character, same location, or same lighting recipe — or the model produces disconnected clips instead of a sequence.

## 9. Anti-mush guard block

Seedance sometimes ignores cuts and produces one continuous take, smears multiple shots into a single moving frame, or drifts character identity across the timeline. Drop this block at the **very top of the prompt** (before block [1]) when it happens or to prevent it pre-emptively on heavy multi-shot work:

```text
Important direction:
This must be a clearly edited multi-shot sequence with visible cuts between shots.
Do not generate a single continuous take. Each shot must have a different camera angle
and different framing. Use rapid montage pacing with rhythmic escalation. Keep the same
character appearance throughout. Preserve the same clothing, face, body type, facial
hair, and hairstyle in every shot. The tone is <serious cinematic drama / tragicomedy /
documentary realism / etc.>.
```

This is the highest-leverage paragraph in any Seedance prompt. Add it any time the model produced mush on a previous attempt.

## 10. `@img1` character reference syntax

Seedance 2.0 accepts image references inline using `@img1`, `@img2`, etc. Use this to lock the protagonist's likeness across all shots in a multi-shot clip and across multiple stitched clips.

```text
Use @img1 as the main character reference and preserve the exact same man across the
whole clip: <full identity block: face, eyes, hair, facial hair, build, distinctive
features, wardrobe>. No nudity. No glasses (unless in reference). No extra characters.
```

Rules.

- The full identity block must follow the `@img1` mention. The model needs the textual description as a backup signal — the image alone drifts.
- Repeat the identity block in **every** clip of a stitched sequence. Treat each generation as briefing a new intern.
- For multiple references (character + setting, character + outfit), label each: `@img1` is the protagonist, `@img2` is the location reference, `@img3` is the outfit reference. Then state the role inline.
- 2.0 also takes `@Video1` (motion/style reference, 480-720p) and `@Audio1` (voiceover / music) tags — state each reference's role in prose, e.g. "@Audio1 plays as the voiceover". Limits: 12 files total on 2.0 (up to 9 images, 3 videos, 3 audio); up to 50 on 2.5.

## 11. Camera movements (9 presets)

- Dolly Out. Reveals context, pulling away.
- Dolly In. Pushes into subject, builds tension.
- Pan Left / Pan Right. Horizontal reveal, landscape, row.
- Tilt Up / Tilt Down. Vertical reveal.
- Tracking. Follows a moving subject.
- Crane / Aerial. Epic scale, establishing.
- Handheld. Documentary, intimate, UGC.
- Zoom In / Zoom Out. Tension or detail.
- Hitchcock Zoom. "dolly out while zooming in" for vertigo effect.
- Static (via `--camerafixed true`). Locked frame.

Combine sparingly. Multiple camera moves in 5s rarely resolve cleanly.

## 12. Negative prompts

Seedance 1.0 Pro does NOT support negative prompts. No `--no blur` syntax works.

Seedance 2.0 adds limited negative prompt support but it's fragile and often ignored.

Workaround. Always invert to positive phrasing. Instead of "no yellow tones" write "cold blue-gray palette with desaturated skin tones." Instead of "no distorted hands" write "anatomically correct hands with clear finger separation."

## 13. Image-to-video rule

When using a reference image, DO NOT describe elements already visible in the image. The model sees it. Describe only motion and camera work. Re-describing static elements creates identity drift.

Bad. "A man in red shirt stands in kitchen. He walks to the fridge."
Good. "He slowly walks toward the fridge, opens it with hesitation, freezes when he sees the empty shelves. Tracking shot from behind, 35mm."

## 14. Audio (1.5+)

Seedance 1.5 Pro, 2.0 and 2.5 generate native audio and support lip-sync. Include audio cues in the body of the prompt — treat the prompt as a sound brief.

```text
Audio. fridge hum, distant rain on window, one stomach growl at 2.3 sec, final silence.
```

Rules:

- Dialogue goes in **double quotes** — the model voices it, generates the voice and syncs lips to the cut. State the delivery: "Play her line dry and a little proud, his quiet and worn out."
- Keep lines short. Long monologues drift out of sync — split into several lines and hold sync with cuts. Still less robust than Veo for speech-first work.
- Write **"no music"** explicitly when you want none — otherwise the model lays an ad-style score under everything.
- Subtitles: describe the voiceover, then ask for "text along the bottom edge, timed to the voice".

## 15. Failure modes and fixes

### One continuous take when multi-shot was requested

Fix. Add explicit "Cut to" markers. Say "multi-shot sequence with visible hard cuts. Do not generate a single continuous take."

### Character drift across shots

Fix. Repeat the full identity block at each shot boundary inside the prompt.

### Motion ignored below 5 seconds

Fix. Minimum duration 5s for any scene that has multiple actions or camera moves.

### Negative phrasing ignored

Fix. Use positive substitutes. Seedance 1.0 has no negative parser.

### Multi-shot fails on 4+ shots in 5s

Fix. Cap at 2-3 shots per 5-second clip for tight cinematic, or 4-5 short beats following the section 7 timeline. If more shots are needed, split into multiple generations.

### Mood smear / "everything looks the same"

Fix. Each shot needs a distinct emotional function (Establish / Power / Pressure / Detail / Reaction / Shift / Impact / Aftermath — see dramaturgy.md §10, Layer 2). If two adjacent shots have the same function, the model averages them into the same frame. Vary function and framing in every cut.

### Lazy abstract phrasing produces lifeless clips

Fix. Apply the Details Law (section 4). Audit your draft: every shot must have one environmental pressure, one micro-action, one sound or visual motif anchor. Replace adjectives like "dramatic", "intense", "beautiful" with concrete physical facts.

### Human faces rejected or degraded (2.0 / 2.5)

After the 2026 deepfake crackdown, 2.0+ aggressively filters human faces, helmets, sunglasses, and anything resembling protected IP or celebrity likeness. Fix. Route face-heavy drama to Seedance 1.5 Pro, Kling, or Veo; keep 2.0/2.5 for scenes, architecture, product and montage work. Use only owned or synthetic character references.

## 16. Worked example. 15-second tragicomedy as 3 × 5s clips

A 15s narrative is **never** one prompt. It is three self-contained 5-second prompts, each with the full character lock, the full visual style, the full audio block, and a different dramatic function. Stitch in the editor.

### Story spine
- Beat 1 (Clip A, 0-5s). Hunger. Hero opens an almost empty fridge. Discovers one lonely sausage. Despair flips to hope.
- Beat 2 (Clip B, 5-10s). Cooking. Pot, water, fire, sausage, bubbling, anticipation, hero shot lifting the sausage with a fork.
- Beat 3 (Clip C, 10-15s). Catastrophe. Sausage slips, falls, wet thud. Window. Bedroom. Hungry sleep. Cut to black.

### Clip A. Hunger (production-grade skeleton applied)

```text
Important direction:
This must be a clearly edited multi-shot sequence with visible cuts between shots.
Do not generate a single continuous take. Each shot must have a different camera angle
and different framing. Use rapid montage pacing.

Use @img1 as the main character reference and preserve the exact same man across the
whole clip: bald head, gray-green eyes, round expressive face, moustache, long black
braided goatee, short dark side hair tufts, slightly overweight build, tragicomic face.
Dress him in a dark oversized T-shirt and dark sweatpants. No nudity. No glasses.
No extra characters.

Generate a 5-second multi-shot tragicomic cinematic sequence with fast dynamic editing.

Story:
The man is hungry at night. He suddenly goes to the refrigerator, opens it, feels
disappointment because it is almost empty, then notices one lonely sausage and becomes
instantly hopeful.

Visual style:
Cold night kitchen. Blue-green refrigerator light. Desaturated colors. No warm yellow
tones. Slightly harsh LED reflections. Realistic cinematic look. High contrast but
natural skin texture. Subtle film grain. Realistic food detail.

Camera style:
Sony FX3 handheld look. 35mm and 50mm lenses for medium and close shots. 100mm macro
for inserts. Handheld micro-shake. Visible cuts between shots.

Editing style:
Fast montage with hard cuts. Each shot a different angle and framing. Tense rhythm,
escalating to the moment of discovery.

Audio:
Deep stomach growl, soft room tone, refrigerator hum, quiet footsteps, fridge door
sound. No dialogue. No subtitles. No on-screen text.

Shot 1, 0.0–0.8 sec. Extreme close-up of the man's eyes in darkness. He is awake,
hungry, tense. Static close shot, faint blue ambient light.
Shot 2, 0.8–1.6 sec. Medium handheld side shot. He sits up and walks fast to the
kitchen. Slight shake, push-in.
Shot 3, 1.6–2.6 sec. POV from inside the refrigerator. The door opens toward camera.
Cold blue-green light hits his face. Shelves almost empty. His face drops.
Shot 4, 2.6–3.5 sec. Rapid inserts: empty shelf, empty container, lonely sauce stain,
his sad eyes, his hand moving items aside.
Shot 5, 3.5–5.0 sec. Macro insert of one single sausage in the corner. Rack focus
from empty shelf to sausage. Smash cut to a slightly low-angle close-up of his face.
His eyes widen, despair flips to joy, tiny victorious smile.

Lighting:
Dark apartment, very low ambient fill. Main source is cold refrigerator light,
blue-green, top-front. Strong contrast. No warm kitchen light.

Composition:
Tight close-ups and inserts. Negative space inside the empty fridge. Final face shot
heroic and absurd.

--resolution 1080p --duration 5 --camerafixed false
```

Clips B and C follow the same structure with their own story paragraph, shot list, and final image. The character lock and visual style blocks are repeated **verbatim** in each clip — Seedance has no memory between generations.

### Older single-clip skeleton (kept for quick scenes)

For a single non-dramatic shot or a quick test, the original 6-step skeleton still works:

```text
Subject. [identity block with face, hair, clothing, distinguishing features].
Motion. [one clear present-tense action for the scene].
Camera. Shot 1. [framing, lens, movement]. Cut to. Shot 2. [framing, lens, movement]. Cut to. Shot 3. [framing, lens, movement].
Environment. [location, time of day, props, weather].
Lighting. [dominant source, direction, quality, color].
Style. [realism level, genre reference, palette].
Audio. [ambient, SFX, silence moments]. (1.5+ only)
Continuity. [what must remain constant across shots].

--resolution 1080p --duration 5 --camerafixed false
```

For dramatic, multi-shot, character-locked, or stitched-clip work — always use the 11-block production-grade skeleton from section 6.

## 17. Seedance 2.5 — the 30-second single-pass clip

2.5 changes the workflow: a 15-30s narrative that used to be 3-6 stitched clips can now be **one generation with one continuous arc**. The dramaturgy does not change — the beat map from `dramaturgy.md` §10 simply moves inside a single prompt.

### Prompt = compact shot-list with beat timings

Structure each beat as Subject → Action → Camera → Style, laid out on a timeline. Default 6-8 seconds per beat, 3-4 seconds for the resolution:

```text
00-06s  Hook.       <subject + action + camera + one environmental pressure>
06-14s  Pressure.   <...>
14-24s  Crack.      <...>
24-30s  Resolution. <final image, held>
```

- Name both the shot size (**CU / MCU / WS**) and the move (**push-in, dolly left, orbit, handheld drift**) on every beat. "Cinematic" tells the model nothing.
- Ask for transitions explicitly (match cut, whip pan) — do not hope. Foreshadowing works: an insert in the opening beat, returned in the last 3 seconds.
- Physics: describe the **consequence** of an action, not just the action — the model renders real physics.

### Character consistency across 30 seconds

- Attach 2-3 portrait stills per hero and tag them (`@Image1`, `@Image2`).
- Repeat wardrobe, props and time of day in every beat — this is what suppresses drift.
- Write the eyeline logic (what the hero looks at) so the model keeps spatial continuity.
- Independent long-form tests are still scarce: verify face and light consistency across all 30s yourself before promising it to a client.

### 3D white-box blockout (previz inside the model)

Reference-to-video accepts green-screen plates or rough 3D geometry to lock camera path, staging and blocking before spending render money. Use for complex blocking the same way you would previz a real shoot.

### Localized re-draw

2.5 can re-render part of the frame (product, background, one subject) without changing motion, camera or lighting — one master cut becomes SKU / locale / seasonal variants. Prompt the patch only; do not re-describe the untouched scene.

### Workflow discipline

Draft low, finish high: block at low resolution, re-render the keeper at 4K. The experimental long-video mode beyond 30s (up to ~180s) is unstable — treat 30s as the reliable ceiling.

---

*Author: Serge Shima ([t.me/aimastersme](https://t.me/aimastersme) · [sergeshima.com](https://sergeshima.com) · [aimasters.me](https://aimasters.me)) · License: CC BY 4.0 — attribution required · Source: [smixs/visual-skills](https://github.com/smixs/visual-skills)*
