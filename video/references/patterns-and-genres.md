# Montage patterns and genre modules

## Contents

1. Montage patterns (6 ready structures)
2. Genre modules (7 archetypes)
3. Multi-clip story structure

---

## 1. Montage patterns

These are pre-built structures that solve common scene types. Pick one, fill with your specifics.

### Pattern 1. Escalation

Use for tension builds, reveals, dramatic emphasis.

```text
wide -> medium -> close-up -> macro -> reaction close-up -> impact
```

### Pattern 2. Anxiety

Use for psychological pressure, internal conflict, impending bad news.

```text
face -> object -> hand -> face -> object closer -> sound cue -> sudden stillness
```

### Pattern 3. Discovery

Use for revealing a hidden element, exploration, search.

```text
POV -> empty space -> searching hand -> hidden object -> rack focus -> emotional reaction
```

### Pattern 4. Catastrophe

Use for comedic or dramatic disaster. Tiny object failures play bigger than explosions.

```text
anticipation -> object instability -> reaction -> object falling -> impact -> silence -> emotional collapse
```

### Pattern 5. Commercial product drama

Use for ads with a hero product.

```text
lifestyle setup -> product reveal -> macro texture -> human reaction -> use moment -> hero product shot
```

### Pattern 6. Music video loop

Use for rhythmic repetition, transformation, performance.

```text
gesture A -> cut -> gesture A from new angle -> cut -> transformation -> repeat gesture A -> release
```

---

## 2. Genre modules

Each genre has a distinct visual grammar. Match style and rhythm to the genre.

### Domestic tragedy

Ordinary objects treated with extreme seriousness. Tiny event as cosmic disaster.

- Style. Cold night interior. Mundane location. Dramatic close-ups. Slow push-ins. Macro inserts. Sudden silence.
- Tone. Tragicomic. Absurd sincerity.
- Pace. Slow build, longer reaction shots.
- Example. A man discovering his fridge is empty, played like a Greek tragedy.

### Music video

Rhythm. Repetition. Visual motif. Transformation.

- Style. Repeated gestures. Match cuts. Performance fragments. Visual loops. Color-coded sections. Aggressive lens changes.
- Tone. Emotional intensity. Sensory overload with readable structure.
- Pace. Fast, beat-driven.

### Commercial

Clarity. Product logic. Sensory detail.

- Style. Clean lighting. Intentional macro. Clear product visibility. Controlled movement. Readable final hero shot.
- Tone. Desire. Transformation. Benefit shown through action.
- Pace. Medium, building to hero shot.

### Psychological drama

Pressure. Stillness. Negative space.

- Style. Locked frames. Long close-ups. Reflections. Obstructed framing. Quiet sound design.
- Tone. Internal conflict. Hidden tension. Emotional compression.
- Pace. Slow, sustained.

### Action

Spatial clarity above all else.

- Style. Establishing geography. Clear direction of movement. Impact inserts. Wide shots between close-ups. Strong eyeline continuity.
- Tone. Urgency. Force. Readable chaos.
- Pace. Fast but geometrically clear.

### Fashion

Symmetric framing. Controlled palette. Repeated silhouettes.

- Style. Slow motion micro-beats. Macro fabric detail. Confident stillness. Rim light.
- Tone. Assured. Sensual.
- Pace. Slow, intentional.

### UGC / Social

Authentic. Vertical. Quick.

- Style. Handheld. Natural light. 9:16. Vertical compositions. Direct-to-camera gestures. Quick beats.
- Tone. Immediate. Casual. Urgent relevance.
- Pace. Rapid, thumbnail-readable.

---

## 3. Multi-clip story structure

AI video generators have no memory between generations. Longer videos live in multiple clips stitched in the edit.

### Default splits

- 10s. 2 clips x 5s
- 15s. 3 clips x 5s
- 30s. 6 clips x 5s
- 45s. 9 clips x 5s
- 60s. 12 clips x 5s

Exception. Seedance multi-shot can pack 2-3 shots into a single 5-10s clip.

### What every clip must repeat

Every clip is self-contained. The model has no memory. Repeat this block in every clip.

- Character identity (face, hair, clothing, distinguishing marks)
- Clothing items, exactly named
- Location description
- Visual style (palette, grade, reference)
- Camera language (dominant grammar of the whole piece)
- Lighting logic (dominant source and direction)
- Continuity rules (what must remain constant)
- Color palette with specific colors

Yes, every single clip. Yes, even if it feels repetitive. That repetition is the only thing keeping the output consistent.

### Timecoded internal beats

Inside each 5-second prompt, use timecodes.

```text
0.0-0.8. [action / camera / light]
0.8-1.6. [action / camera / light]
1.6-2.5. [action / camera / light]
2.5-3.7. [action / camera / light]
3.7-5.0. [action / camera / light]
```

Density by genre.

- Emotional drama. 3-4 beats per 5s. Longer reactions.
- Standard narrative. 4-7 beats per 5s.
- Fast montage / music video. 6-9 beats per 5s.

Use timecoded structure for Seedance and Veo. Kling prefers flowing prose.

### Continuity across clips

When moving from clip N to clip N+1, the first beat of the new clip should match the final beat of the previous clip. Character in same pose. Same light. Same color temperature. This is what makes them cut together cleanly in the editor.

Example. Clip 1 ends on him reaching into the fridge. Clip 2 opens on his hand inside the fridge at the same height and light.
