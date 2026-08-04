# Seedance 2.5 — production reference (ByteDance, official guides of 2026-07-31)

Read `seedance.md` first for the family basics (Details Law, multi-shot syntax, 11-block skeleton). This file covers what 2.5 adds: the official prompt formulas, the 50-slot reference system, video editing, extension, ultra-long mode, and the blockout pipeline. Sources: the official Dreamina/Jimeng User Guide and Prompt Guide (both published 2026-07-31), verified against practitioner tests from the first launch week.

## Contents

1. What 2.5 changes
2. Specs and hard limits
3. Official prompt formula
4. Syntax markers for audio, dialogue and text
5. Reference discipline (the 50-slot system)
6. The 30-second structure: stages and end states
7. The anti-collapse skeleton (3 modules)
8. Realistic human formula (anti-AI-face)
9. Camera language
10. Transitions
11. Physics through consequences and triggers
12. Video editing (partial re-render)
13. Video extension
14. Ultra Long mode (30-180s)
15. Blockout and green screen
16. Storyboard grids and keyframes
17. Failure modes and fixes
18. Economics and model choice
19. Worked examples (official, verbatim)

---

## 1. What 2.5 changes

- **30-second native single-pass clip.** One generation, one continuous arc, no stitching. Extension pushes it to 60s; a separate Ultra Long mode goes to 180s (see sections 13-14).
- **50 multimodal references** (30 images + 10 videos + 10 audio) with per-asset role binding. The model understands which asset is responsible for character, scene, prop, camera move, or rhythm — if you tell it.
- **Realistic humans are a headline feature**, not a liability: real skin pores, restrained micro-acting, multilingual lip-sync in 11 languages. The 2.0-era face caution does not apply.
- **Negative commands became reliable.** "Pure video, no subtitles, no background music" now actually suppresses random subtitles and unwanted score — the classic 1.x/2.0 failure is fixed.
- **Second-level timestamp control.** `[0-4s] ...` beat windows are honored as timing, not just ordering.
- **Editing an existing video** (partial re-render, background swap, language re-dub) and **extending** it are first-class modes, not workarounds.
- **Blockout control**: white-model 3D previz video (or green-screen plates) locks camera path, staging and blocking; Blender/Maya plugins upload straight to Jimeng.

Entry points: Jimeng (jimeng.jianying.com — Omni Reference / Smart Edit / Long Video / First & Last Frames), Doubao (Pro subscription), Xiaoyunque (xyq.jianying.com — character library, 3D director stage, segment reshoot).

## 2. Specs and hard limits

| Parameter | 2.0 | 2.5 |
|---|---|---|
| Single-pass duration | up to 15s | up to **30s** (duration `-1` or 4-30) |
| Images per request | 9 | **30** (each ≤4K, ≤30 MB) |
| Video references | 3 clips, ≤15s total | **10 clips**, single 2-30s, **≤30s total** |
| Audio references | 3 clips, ≤15s total | **10 clips, ≤30s total**; audio-only input now allowed |
| Output resolution | up to 4K | **480p / 720p** on Jimeng web |
| Timestamps | ordering hints only | honored to the second |

Generation parameters (duration, aspect ratio, resolution) are set on the generation page or via API — **they do not belong in the prompt**. The 1.x/2.0 CLI tail (`--resolution ... --duration ...`) is not 2.5 syntax. Exception: in Ultra Long mode, restate duration and ratio at the top of the prompt.

Auto-locked parameters: video editing locks ratio and duration to the input (±0.3s); first/last frame locks ratio to the first image (a mismatched last frame gets stretched); extension locks ratio, duration settable.

## 3. Official prompt formula

Base formula for any 2.5 prompt:

```text
<Subject> performs <primary action or event> in <scene and environment>.
The visuals feature <visual style>.
Use <shot size, camera angle, camera movement, or cuts>.
Audio includes <dialogue, ambience, sound effects, or music>.
```

Any component may be omitted. For long or reference-heavy work, the macro-formula:

```text
Complete prompt = [reference declaration] + [one-line summary] + [plot by timeline] + [global tail]
```

- **Reference declaration.** Each asset by upload order + its role (character / voice / motion / scene). See section 5.
- **One-line summary.** Subject + place + event + genre/style + special camera treatment.
- **Plot by timeline.** Per beat: ➕ positive content (picture + camera + action + dialogue + SFX) and ➖ local bans ("no subtitles", "no BGM").
- **Global tail.** Re-state the must-hold globals (camera position, environment, sound, lighting) and repeat the global bans.

Re-@ the same asset multiple times through the prompt — the official guide says repeated mentions increase accuracy.

## 4. Syntax markers for audio, dialogue and text

2.5 has dedicated markers. Use them — do not describe audio in loose prose:

| Content | Marker | Example |
|---|---|---|
| Music | `( )` | `(Soft, rhythmic piano music plays in the background)` |
| Sound effect | `< >` | `<A bell rings in the distance>` |
| Dialogue | `{ }` | `{Hello, welcome back.}` |
| Subtitles / titles | `【 】` | `【Chapter One: Departure】` |

Dialogue language reinforcement — the formula is `Dialogue language + regional variety or accent + delivery style + speaker + {line}`:

```text
Dialogue language: authentic Los Angeles English. The young man says in natural
Los Angeles vernacular: {No way, you actually made it.}
The girl says softly in Japanese: {もう大丈夫です}
```

Lip shape, speech rhythm and face match the assigned language in one pass — this holds across all 11 supported languages, including mixed-language scenes.

## 5. Reference discipline (the 50-slot system)

The point of 50 slots is not dumping assets in. **Every material's role must be written in the prompt.** Do not rely on text labels inside images; do not make the model infer mappings.

Role template:

```text
@Image 1 defines <subject>'s <appearance, clothing, structure, or material>.
@Video 1 defines <motion, camera movement, or pacing>.
@Audio 1 defines <character or sound type>'s <voice, dialogue, ambience, or music>.
```

Rules:

- **Bind each subject individually.** `<Character A> corresponds to @Image 1. Use only the appearance, hairstyle, and clothing.` The officially forbidden pattern: "@Images 1 through 4 define four characters respectively" — it never states which is which.
- **Add exclusions** for anything that could bleed in: "Do not use the image background." / "Do not use the people in the image." / "Do not use the person's identity, clothing, or scene from the video."
- **Do not restate what a reference already defines.** If a reference video defines the motion, state only which attributes to inherit — re-describing every action conflicts with the reference.
- **Subject Profile** for a recurring character:

```text
[Subject Profile: Conservator]
Appearance and clothing: @Image 1.
Fixed prop: <Sample Case> from @Image 5.
Locations: <Conservation Lab> and <Gallery>.
Motion references: the case-opening motion from @Video 1.
Do not use: other characters' clothing. Do not give this character <Record Board>.
```

- **Select references per scene**, not all at once: `Scene 1 | Use: <list>. Event: ... End state: ...`
- The same character in two states (before / after a transformation) = **two separate image slots**, each bound to its time range. Expect this to be the flakiest binding — budget re-rolls.

Official stability sweet spots:

| Input | Best | Possible but unstable |
|---|---|---|
| Subjects in a reference video/audio | 1-5 | 6-10 |
| Reference clip length | 5-10s per subject | longer |
| Subjects across reference images | 1-8 | 9-12 |
| Multi-view sheets | ≤5 subjects: any | >5 subjects: single view only; separate images per view beat a collage |
| Video-edit source length | ≤20s | longer stalls |

## 6. The 30-second structure: stages and end states

Divide the clip into consecutive stages. **One primary state change per stage, and always state the visible end state** — the end state is what the model steers toward (this is the U11 final-image rule, per stage).

```text
[Generation Goal] Generate a <video type>. The central subject is <subject>,
and the primary event is <story summary>.
[Stage 1] Initial state: ... Primary event: <one primary action>. End state: <visible state>.
[Stage 2] Continue from the previous stage: <what must remain unchanged>.
          Primary event: ... End state: ...
[Stage 3] Primary event: <closing event>. End state: <final visible state>.
[Maintain Consistency] Keep <identity, count, clothing, prop ownership,
spatial direction, audio relationships> consistent.
```

Timestamp rules:

- A time range is an event's **time budget, not an edit point**. Ranges must be consecutive and non-overlapping.
- **Windows of 3 seconds or more.** Shorter windows execute unreliably.
- **One core action + one camera move per window.** Do not demand frequencies ("three actions in one second").
- Second-precision only where it matters: critical handoffs, entrances, transitions, beat hits. `At 5 seconds, the camera whip-pans left and completes the transition.` Relative triggers work too: `Three seconds after the character presses the button, the room lights turn off.`
- Too little content in a window = model freedom; too much = over-cutting and omissions. Match content volume to the budget.

## 7. The anti-collapse skeleton (3 modules)

The official structure for dramatic 30-second work. It maps onto our 11-block skeleton but is leaner:

```text
<One-line tone summary — the logline>

[Module 1 — Reference layer]
Strictly keep @Image 1's face and features consistent. Keep @Image 2's
composition / blockout / spatial relations. Strictly lock character blocking.

[Module 2 — Global settings ("worldview + anti-collapse")]
Base environment & texture (emphasize extreme, realistic physical texture).
Visual style (film look, depth of field, lighting).
Camera language.
Character styling (use the section 8 formula).
Performance core (the acting register for the whole piece).
Prohibitions: <sound bans> + <subtitle bans> + <behavior bans> + <known collapse points>.

[Module 3 — Timestamped storyboard]
[start-end s] [beat name] — physical directives (shot size, composition,
micro-actions) + emotional subtext.
```

Two techniques carry this skeleton:

- **The prohibition list is specific, not generic.** From the official farewell example: "No exaggerated crying, no fast cuts, no large body movements, no extra dialogue, no BGM, no runny nose, no premature dropping of tears." Ban the exact ways this scene can collapse.
- **Directive + subtext.** After the physical directive, explain to the model *why* the action happens: "Emotion analysis: she is not complaining — she is waiting for him to confirm an answer she already guessed." The model acts better when it knows the intent. This is the official guide's signature trick and it composes directly with our Details Law.

## 8. Realistic human formula (anti-AI-face)

```text
Character = [age / ethnicity] + [skin tone / skin texture] + [3-4 facial details]
          + [gaze / soul] + [hairstyle / hair color] + [clothing / fabric]
          + [build / emotion / aura]
```

- **Force-append the fidelity suffix:** "retaining real fine pores and skin texture" (optionally freckles, blemishes). This single clause is the official anti-plastic-skin fix.
- Facial details need 3-4 concrete points: eye shape, brow bone, nose bridge, lips, jawline.
- Gaze/soul = the emotion the eyes carry, separate from the facial geometry.
- Works for animated characters too — swap the texture register.

For one emotional transition, **2-4 observable cues are enough** (eye movement, brow tension, mouth, breathing, throat swallow, hands). More reads as overacting; abstract emotion words leave too much room.

## 9. Camera language

Officially understood without translation: extreme wide / wide / medium / close-up / extreme close-up; push in, pull out, pan, lateral move, follow shot, orbit, dive, dolly out, tilt, handheld shake; low angle, overhead, first-person; one-take shot, dolly zoom, aerial, FPV, bullet time, bounce speed ramp.

For rarer terms, keep the term **and** translate it to observable change: `term + target subject + visual change + foreground/background relationship + direction or speed`. Full pattern and vocabulary in `camera-lighting-vocabulary.md` §10.

Aperture and focal-length numbers are allowed, but the visible result phrased in words is what actually steers the model.

## 10. Transitions

The transition vocabulary (natural cut, fade, dissolve, flash, wipe, occlusion mask, match cut, action/whip cut, motion-relay, zoom-through, ink-wash) lives in `camera-lighting-vocabulary.md` §11. Seedance-specific usage:

```text
cut = [transition type] + [basic constraints] + [cut logic]
```

- Always attach the incantation: **"prohibit rigid cutting, prohibit objects appearing out of thin air"** — it is the official anti-jump-cut clause, repeated in every transition template.
- Transitions can be **delegated**: "From [natural cut / occlusion mask / ink-wash / match cut], choose the one that best fits the style of this film."
- Order-gate effects that must not fire early: "The ink-wash effect must only appear AFTER 25 seconds, triggered by the 'click' sound — absolutely no premature appearance."

## 11. Physics through consequences and triggers

2.5 renders real physics and couples it with audio. Exploit this in four moves:

1. **Declare the physics regime up front.** "Rain reflections on metal, water splashed by tires, and the specular refraction of exhaust flames must strictly obey real-world physics."
2. **Narrate consequences, not just actions.** Tires kick up water curtains; the impact shatters the bridge into a spider-web pattern; the shockwave blows the rain away in a ring. Action chains where each step forces the next ("hand grips jar → lid actually unscrews") double as QA — a broken chain exposes a failed generation instantly.
3. **Negatively constrain the known failure.** "No soft-body or mollusk-like twisting of the mecha structure (must maintain metallic rigidity)." "The amber stays attached to the palm and must not clip through the fingers."
4. **Gate events on triggers.** "Three seconds after she presses the button..." / "only when he says {now}..." — triggers beat raw seconds for anything tied to performance.

## 12. Video editing (partial re-render)

2.5 edits an existing video: replace a subject, swap a background, remove a watermark, change the spoken language — while everything else stays put. The canonical pattern:

```text
[Edit Goal] Edit @Video 1. Within <entire video or time range>,
<add / remove / replace / adjust> <object, region, or audio category>.
[Source Video Role] @Video 1 is the sole editing master. It defines <characters,
scene, actions, composition, camera movement, occlusion, audio, and event order>.
[Target Material Role] @Image 1 defines <attributes of the replacement>.
[Edit Scope] Modify only <object, region, time range, or audio category>.
[Content to Preserve] Keep <everything that must not change> from @Video 1.
```

- **Subject replacement** adds a `[Timeline Inheritance]` block: "<Target> inherits every appearance, motion, occlusion, and exit of <original>, including timing, duration, path, and speed changes." Close with the catch-all: "Except for the object explicitly modified above, keep all other people, props, scene content, camera movements, cuts, and event order from @Video 1 unchanged."
- **The preservation-clause opener.** For filmed footage, enumerate everything to keep before stating any change — down to focal length, aspect and floor perspective: "Fully preserve from @Video 1 the person's identity, face, hair, skin tone, lip movement, original voice, speech rhythm, expression, gestures, camera position, focal length, aspect ratio, wall and floor perspective, and total duration." The longer the keep-list, the less drift.
- **Anchor timing to speech, not seconds**, when the source has narration: "When they say {now look at my hand}, a golden amber appears in the palm." The voice is the timeline.
- **Slice long sources first.** Editing works best on clips ≤20s; longer sources stall or fail.
- **Audio-only edits** work: "Remove only the original background music. Keep the dialogue, lip sync, ambience, and action sound effects; preserve the visuals and editing rhythm."
- **Localization pattern** — shoot once, re-dub per market: "Replace the Chinese narration in @Video 1 with natural fluent Spanish, and replace the presenter with a Spanish woman. Keep the original camera movement, blocking, performance pacing, scene, and product; preserve the overall audio-visual rhythm."
- Background swap scope: "modify only the background outside the subject's silhouette."

## 13. Video extension

Any clip ≤30s extends by 4-30s per pass, nested repeatedly, **hard ceiling 60s**. The new prompt applies only to the appended segment; original frames are untouched. Required verbs: extend forward / extend backward / continue.

Forward:

```text
Extend @Video 1 forward. The first frame of the extended segment directly
continues from the last frame of @Video 1. Maintain continuity in <pose,
prop position, background, camera position, lighting, motion direction>.
Then, <new content>.
Keep each subject as the same continuous instance throughout: do not duplicate
or split it, and keep the person's appearance stable.
```

Backward (prepend a beginning): describe the preceding events, then define @Video 1's **first frame as the extension's explicit end state**. Gotcha: materials that belong to the source video only must be flagged — "<X> must not appear early in the backward extension" — or later characters leak into the past.

- Boundary frames connect visually, not pixel-identically.
- Extensions hold character look, art style **and voice timbre** even without re-supplied references — plot-only extension prompts work.
- Community-proven minimal extension prompt: "Extend the video. Keep character identity, facial structure, body proportions, lighting, art style, and the space fully unchanged. Only change camera movement; do not redesign character or action."

## 14. Ultra Long mode (30-180s)

A separate mode (not the same as extension): one submission, 30-180 seconds. Restate duration and aspect ratio at the top of the prompt. Two working registers:

- **Timestamped** (1-minute ambient pieces): windowed beats with per-window bans — "0-20s (quiet opening): fixed camera... no shake, no characters enter, hard cuts prohibited."
- **Narrative flow** (3-minute pieces): loose event chain with inline references — the official 3-minute example is a cat-waiter vlog listing a full day of beats with 12 image refs assigned by role, closed with "No subtitles throughout, no background music."

Plan pacing in advance — without timestamps or a beat chain the back half drifts. Under the hood the pipeline generates segment-by-segment, carrying the **last ~3 seconds of each segment as the reference for the next** — which is why hand-offs are smooth and why a weak middle segment propagates forward. On Xiaoyunque the same mechanism powers chained extension to 90s plus **segment reshoot**: select a bad span on the timeline and regenerate only it, everything outside stays identical — the cheapest fix for pop-in objects and missed expressions.

## 15. Blockout and green screen

The controllability king: lock space, camera and staging in 3D first, let the model render materials and light. Two granularities:

- **Coarse blockout** — primitive geometry as a "dynamic skeleton" (trajectories, blocking, camera path, cuts, light changes). **Map every primitive to a reference**: "The tall cylinder in @Video 1 corresponds to <Guide>. The rectangular block corresponds to <Display Cart>." Exclude the render style: "Do not use its gray geometry or empty scene." Best practice: **no limbed or winged models in coarse blockouts** — unless you write the full limb motion sequence, they go stiff.
- **Fine blockout** — complete 3D animation; the model re-renders materials, color and style only: "@Video 1 is a fine blockout reference. Preserve structure, action, spatial layout, camera position, camera movement, and cuts. Do not use its original gray materials or empty background. Re-render <subject> as <final subject>..." **Clean the viewport capture first**: remove path lines, coordinate axes, controllers and camera frustums. Coarse currently works better than fine.

Pipeline notes:

- Blender/Maya plugins ("Clay Renderer" / 白模渲染上传器) render the blockout and upload straight to Jimeng as the reference video. Blender ≥3.6 works; no C4D/3ds Max. Color-coding blockout objects is unreliable — disambiguate primitives via prompt text, not material colors.
- No 3D package? Xiaoyunque's 3D director stage reconstructs a blockout from a concept image, offers action/camera/prop libraries, and lets you **drag-draw the camera path in the viewport**, then renders the previz clip for you.
- A **camera-path diagram works as an image reference** too: supply a top-down route sketch as @Image N and write "follow the camera route in @Image N".
- **Green screen, both directions**: upload green-screen footage + scene refs ("composite the person naturally into the classroom from @Image 2"), or convert an existing video's background *into* green screen for downstream comps ("Change all the white backgrounds into green screen backgrounds. Remove the sound, keep it muted.").

## 16. Storyboard grids and keyframes

- **Storyboard grid as input**: one image, ≤15 panels official (practitioners have pushed 50), clean line art, minimal text. Declare the reading order and exclude the style: "@Image 1 provides a 12-panel storyboard grid for shot order and approximate composition. Read it left to right, top to bottom. Do not use the grid's line-art style, text labels, or placeholder characters." Then `Shot 1: ... Shot N: ...`
- **Multi-keyframe sequences**: "Use @Image 1 through @Image N as keyframes in this order", one key state per image. Independent images align better than a grid. Keyframes control stage order and key states, not exact frames.
- **First + last frame** works inside omni-reference mode — declare each anchor separately ("@Image 1 is the first frame... @Image 2 is the last frame..."), never jointly. Same aspect ratio required.
- This is where the `image` skill chains in: character sheets and keyframes from `animatic-keyframes.md` become the reference kit.

## 17. Failure modes and fixes

### Twins / face-blending in multi-person scenes
Fix. Per-subject binding (section 5) + explicit differentiation: "Their movements are not synchronized. Clothing colors, hairstyles, and facial features must all be distinct. No identical clones in the background."

### Same character in two states appears at the wrong time
Pre/post-transformation slots confuse the model. Fix. Bind each state to its time range explicitly; budget re-rolls — this is the flakiest binding in 2.5.

### Random subtitles or unwanted BGM
Fix. "Pure video, no subtitles, no background music" — reliable in 2.5. Repeat in the global tail.

### Plastic AI skin
Fix. "Retaining real fine pores and skin texture" + production language instead of "hyperrealistic 8k".

### Long-context plausibility slips
Over 30s the model can place a plausible object in an impossible spot (a freighter on dry concrete). Fix. State the world's hard constraints in the global tail; verify the full timeline before shipping — errors hide in the back half.

### The one-take that refuses to stay one take
2.5 errs by commission: it completes more instructions than rivals but may cut freely even when told "one continuous take". Fix. "One continuous shot, no cuts of any kind" + a camera path that never motivates a cut; if montage keeps leaking in, drop to a 10-15s window where one-takes are stable.

### Edit mode stalls or ignores the instruction
Fix. Source ≤20s (slice first); name @Video 1 as "the sole editing master"; one edit target per pass.

## 18. Economics and model choice

- Costs are real: a 30s/720p generation on Jimeng runs ~500-700 credits. Production budgets must assume re-rolls, extensions and segment reshoots — fix with edit/extend/reshoot instead of full regeneration whenever possible. Draft at 480p, finish at 720p.
- Versus Minimax H3 (the other frontier model of this launch window): **H3 errs by omission, Seedance 2.5 errs by commission** — H3 delivers a more filmic whole but drops shots from the list; 2.5 executes nearly every instruction but may misuse a reference or break a global constraint. Pick 2.5 for timestamp precision, dense shot choreography, 50-reference kits and the editing/blockout toolchain; pick H3 (or Kling/Veo) when overall cinematic coherence per credit matters more than instruction compliance.

## 19. Worked examples (official, verbatim)

### A. Restrained micro-acting — "Riverside Farewell" (29s one-shot)

The flagship official example for emotional performance. Abridged; the structure is what to copy:

```text
29-Second One-Shot (Ancient Costume Woman's Riverside Farewell)

[Global Scene Setting] Early morning by the river, a blurred small boat in the
background, a lonely farewell. Quiet, restrained. Cinematic, shallow depth of
field, soft natural light. The camera holds a close-up of the woman, imitating
the subjective POV of "him" standing opposite her. Subtle handheld breathing,
one continuous shot with no fast cuts.

[Character Styling] [Age/Ethnicity] 22-year-old East Asian woman, classical
gentle cinematic face. [Skin] Cool-toned fair skin, delicate and moist,
retaining realistic fine pores and natural skin texture. [Facial Features]
Slender elegant eyes (slightly moist), relaxed brows, delicate straight nose
bridge, full lips with a faint gentle smile, soft jawline. [Eyes/Soul] Deeply
affectionate gaze, eyes shimmering like spring water. [Hair] Jet-black hair in
a casual classical low bun, a plain jade hairpin. [Clothing] Minimalist pure
white cross-collar Hanfu. [Physique/Aura] Slender, delicate narrow shoulders,
gentle classical romantic aura.

[Core Performance] Restrained and nuanced. Capture the shifting gaze, the rise
and fall of breathing, slight lip trembling, subtle brow movements, nostril
changes, throat swallowing, and the natural process of a tear sliding down.

[Negative Prompts] No exaggerated crying, no fast cuts, no large body
movements, no extra dialogue, no BGM, no runny nose, no premature dropping
of tears.

[Emotion and Action Storyboard]
Stage 1: 0-3s [Questioning]. She looks directly into the lens, lips slightly
parted, and whispers: {Are you really leaving?} Emotion analysis: she is not
complaining — she is waiting for him to confirm an answer she already guessed.
Stage 2: 3-10s [Resignation] — swallowing the bitterness. ...
Stage 3: 11-17s [Remembering] — a 0.5-second dead-silent pause; her lips twitch
then press together, jaw tightens, throat swallows.
Stage 4: 18-23s [Regret] — she lowers her eyes, and only then do the tears
begin to fall. She shakes her head slightly, almost imperceptibly.
Stage 5: 24-29s [Letting Go] — extreme close-up. She forms a gentle smile and
says in a barely audible but steadied voice: {You can go.} (On the word "go"
there is a faint tremble, forcefully suppressed.)
```

Every stage: one state change, physical directives, emotional subtext, and the bans list names the exact collapse modes of *this* scene.

### B. Physics and prohibitions — sci-fi mecha chase (30s one-shot)

```text
30-Second One-Shot (Sci-Fi Mecha Chase and Transformation)

[Global Setting] A cyberpunk cross-sea bridge in 2077, heavy rain. Emphasize
extreme, realistic physical textures: rain reflections on metal, water
splashed by tires, and the specular refraction of exhaust flames must strictly
obey real-world physics. Hardcore sci-fi cinematic feel, high-contrast neon
(cyber-pink and icy blue), high-speed shutter. High-speed drone POV, one
continuous shot. Subject: a silver-and-black concept mecha motorcycle.

[Negative Prompts] No soft-body or mollusk-like twisting/clipping of the mecha
structure during movement (must maintain metallic rigidity); no human
entities; strictly remove irrelevant subtitles; force mute / no default BGM;
avoid copyrighted IP elements like Transformers or Tron.

[Timestamp Storyboard]
[00:00-00:08] [Extreme Speed] The camera skims the waterlogged road; the
spinning wide tires kick up massive water curtains meters high. Camera
subtext: convey speed through the physical interaction of rain, puddle
reflections and engine flames.
[00:09-00:16] [Evasion] The tires grind the road, sparking orange friction
sparks, executing a tight "S" curve.
[00:17-00:24] [Mid-Air Reassembly] During slow-mo hang time the armor flips,
deconstructs, and reassembles — strictly rejecting "noodle-like" soft-body
transformation.
[00:25-00:30] [Heavy Landing] The tonnage impact shatters the bridge surface
into a spider-web pattern; the shockwave blows the surrounding rain away in
an expanding ring. A frozen "superhero landing" as the final image.
```

Physics regime declared up front, every beat narrates a consequence, and each ban targets a known failure of exactly this material.

### C. Reference orchestration — museum heist one-take (17 refs, translated from the Jimeng manual cases)

```text
Photoreal suspense-film texture. Set at the museum charity gala of @Image 10;
main hall structure, twin staircases and central exhibit stay consistent
throughout; sub-spaces reference @Image 11 and @Image 12; lighting and
materials reference @Image 15 and @Image 17. Follow the camera route in
@Image 16; smart auto-cutting, cinema-grade camera moves.

[0-4s] Camera advances behind the shoulder of the @Image 4 waiter carrying
the @Image 14 silver champagne tray through the main hall; the @Image 5
curator greets guests at the staircase; the @Image 6 reporter raises a
camera. The @Image 1 blue-diamond necklace sits in its glass case.
[4-8s] The @Image 7 woman in red brushes past the @Image 8 magician in black
tails, who smiles faintly at the lens; the @Image 9 security chief watches
beside the case.
[8-11s] The chandelier dies; the hall snaps to the crimson emergency lighting
of @Image 13; the crowd falls silent; <a soft clink from the case>, then
<a short alarm>. (Low strings and heartbeat stop together) — keep only an
inhale, the glass clink and the alarm.
[11-16s] Close-ups in sequence: the curator frozen, the reporter raising the
camera, the woman in red stepping back. Lights return to warm gold; cut back
to the case — glass intact, the @Image 1 diamond gone.
[16-20s] Slow push toward the magician's lowered right hand; a tiny blue
glint inside his silver cuff; he lifts his eyes to the lens and smiles.

No subtitles, no logo, no watermark.
```

Seventeen references, every one role-bound per scene; the camera choreography is supplied as a route diagram (@Image 16), not prose; sound is designed per beat with the `< >` and `( )` markers.

---

*Author: Serge Shima ([t.me/aimastersme](https://t.me/aimastersme) · [sergeshima.com](https://sergeshima.com) · [aimasters.me](https://aimasters.me)) · License: CC BY 4.0 — attribution required · Source: [smixs/visual-skills](https://github.com/smixs/visual-skills)*
