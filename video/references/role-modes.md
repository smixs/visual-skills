# Role modes

This skill fuses three mindsets. Switch role based on the task stage. The dramaturgy layer sits underneath all three roles. For the full dramaturgy method (scene formula, Murch Rule of Six, blocking as choreography of desire, staging and subtext, three-layer storyboard, shot card template, rhythm ladder), load `references/dramaturgy.md`. Director mode leans heaviest on that file.

## Contents

1. Director mode
2. Screenwriter mode
3. Editor mode
4. Shot function taxonomy

---

## 1. Director mode

### Trigger

User asks to "придумать сцену", "разработать концепцию", "визуализировать идею", "сделай как Финчер", "предложи трактовку", "какой вайб", or shares a raw idea without structure.

### Mindset

Every shot must answer at least one of these questions. If a shot answers none, delete it.

- What changes emotionally?
- What new information appears?
- What action moves the story?
- What pressure increases?
- What does the viewer need to notice?
- Why does the camera move?
- Why does the cut happen here?

### Output format. Director treatment

```text
Core idea. [one sentence, the point of the piece]
Emotional arc. [start -> middle -> end, three emotion states]
Visual motif. [one recurring visual element]
Rhythm. [pace logic. slow build, rapid montage, still + sudden burst]
Camera language. [dominant grammar. handheld intimacy, locked precision, gliding observer]
Lighting. [dominant source and direction]
Sound. [texture. ambient layers, music role, silence moments]
Ending image. [final frame in one sentence]
```

### Style references

Use one dominant director reference per scene. Translate into concrete camera, light, rhythm, blocking. Never stack three or more references.

- Fincher. Precise motivated camera. No handheld drift. Cold palette.
- Kurosawa. Weather as emotional pressure. Rain, wind, heat.
- Spielberg. Readable staging. Clear geography. Emotional wide shots.
- Edgar Wright. Sound-driven montage. Match cuts on sound events.
- Jonathan Glazer. Music-video visual idea translated to drama.
- Wong Kar-wai. Longing. Reflections. Slow emotional drift.
- Safdie. Anxiety. Handheld pressure. Overlapping sound.
- Wes Anderson. Symmetry. Controlled blocking. Color blocks.

---

## 2. Screenwriter mode

### Trigger

User asks to "напиши сценарий", "разбей на биты", "придумай диалог", "адаптируй историю в видео", "нужен story arc."

### Mindset

Translate every beat into physical action the camera can see. Tag each beat with a shot function (see section 4). Every beat must have subtext.

### Output format. Beat breakdown

```text
Beat 1. [function] - [physical action]. Subtext. [what it means].
Beat 2. [function] - [physical action]. Subtext. [what it means].
...
Final image. [what the viewer takes with them].
```

### Dialogue format (for Veo specifically)

Write spoken lines in ready-to-paste Veo syntax.

```text
He says, in a flat exhausted voice, "We are fine. We are fine."
```

Cut lines until they fit 8 seconds of natural speech.

### Internal monologue rule

Veo cannot render internal monologue. Translate into visible bodily signal.

Bad. "He is thinking about his father."
Good. "He stops mid-motion. His eyes drift off-axis. He swallows. He resumes."

---

## 3. Editor mode

### Trigger

User asks to "собери монтаж", "задай ритм", "сделай динамично", "разбей на склейки", "как смонтировать", "сколько кадров в 5 секундах."

### Mindset

Dynamic montage is built through structure, not speed. Random fast cuts create visual soup. Readable fast cuts create propulsion.

### Rules

- Clear shot function per cut.
- Escalating frame tightness (wide -> medium -> close).
- Different camera angles per cut.
- Motivated cuts (sound event, action beat, emotional shift).
- Contrast speed and pause.
- Sound-driven transitions.
- One silence or stillness moment before a major impact.

### Output format. Timecoded beat sheet

```text
00.0-00.8. [shot function] - [framing] - [camera] - [sound cue]
00.8-01.6. [shot function] - [framing] - [camera] - [sound cue]
...
```

### Density

- Emotional drama. 3-4 beats per 5s.
- Standard narrative. 4-7 beats per 5s.
- Fast montage. 6-9 beats per 5s.

More than 9 beats in 5s creates incoherent motion regardless of model.

---

## 4. Shot function taxonomy

Every beat should carry at least one function tag. This is the editor's grammar.

- **Establish.** Where we are. Wide or master shot. Sets geography.
- **Reveal.** What appears. New information enters frame.
- **Power.** Who controls the scene right now. Staging reveals the hierarchy before dialogue does.
- **Pressure.** Tension builds. Movement toward threat or decision. Environment can carry this (flickering light, rain, steam, a tight corridor).
- **Detail.** Important object, hand, eye, texture, gesture. Macro or close-up. The anchor object often lives here.
- **Reaction.** Emotional consequence. Face response to a beat.
- **Shift.** Inner change. Body language turning point. The moment before the decision becomes visible.
- **Impact.** Decisive visual event. The drop. The hit. The break.
- **Aftermath.** Emotional residue. Stillness after impact.
- **Exit.** Final state. The image the viewer leaves with.

A full scene usually moves. Establish -> Power -> Pressure -> Detail -> Reaction -> Shift -> Impact -> Aftermath -> Exit.

A montage sequence can compress or loop. Use function tags to keep the structure readable even at high speed.

Each tag is also a question the shot must answer. Establish. Where. Power. Who commands. Pressure. What pushes. Detail. What to notice. Reaction. What it cost. Shift. What changed inside. Impact. The moment. Aftermath. The residue. Exit. The image carried out.
