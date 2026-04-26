# Universal rules — apply to every video model

These rules apply to Seedance, Kling, Veo, and any other AI video generator. They exist because all current video models share a common failure mode. They reward concrete physical direction. They punish abstraction, contradictions, and keyword spam. Ignoring these produces muddy generations regardless of which model you target.

Read this file after `dramaturgy.md` and before any model-specific file. The model-specific syntax sits on top of these rules — it does not replace them.

## Contents

1. The non-negotiable. Details intensify emotion (Details Law)
2. U1. Universal prompt skeleton
3. U2. Weight-at-start
4. U3. Show don't tell
5. U4. Natural language beats tag spam
6. U5. One primary camera move per shot
7. U6. Precise lens language
8. U7. Character consistency anchor
9. U8. No contradictions
10. U9. Concrete physical detail over abstract concept
11. U10. Duration discipline
12. U11. The final image rule
13. U12. The three-detail check (audit before sending)

---

## 1. The non-negotiable. Details intensify emotion. Laziness kills the prompt.

This is the most violated rule in AI video, and the one reason most multi-shot prompts fail. The dramaturgy is fine — the writer just got lazy on a single shot, and that one thin shot drags the whole sequence into mush.

Every shot in every prompt owns at least three concrete physical details:

1. **One environmental pressure.** Cold blue refrigerator light. Steam off boiling water. Wet asphalt. Flickering fluorescent. Dripping tap. Curtain breathing in the AC. (Kurosawa: weather is a character. See `dramaturgy.md` §9.)
2. **One physical micro-action.** Jaw locks. Knuckles whiten on the fork. Lips press into a line. He swallows hard. Fingers curl against the doorframe. (Show, not tell — the body is the only place where feelings render.)
3. **One sound anchor or visual motif.** Stomach growl at 2.3s. Reflection in a darkened phone screen. Rain on the same windowpane. A single fluorescent flicker before each cut.

If a shot has none of these — it is filler. Delete it or rewrite it. No exceptions for "establishing", "transition", or "hero product" shots — those are exactly the shots that go lazy first.

Words that do not render and mark the writer being lazy:

- "cinematic", "professional", "high quality", "masterpiece", "stunning", "epic", "amazing"
- "beautiful lighting", "dynamic camera", "intense moment", "powerful scene"
- "he is sad", "she is angry", "he is afraid" — emotions named without a body

Replace each with concrete physical facts. The full theory of why this works lives in `dramaturgy.md` §2 (Second law).

## 2. U1. Universal prompt skeleton

Build every prompt from these layers, roughly in this order:

```text
[Subject / Character]
[Action / Motion]
[Scene / Environment]
[Camera / Shot / Lens]
[Lighting / Atmosphere]
[Style / Mood / Palette]
[Sound / Audio]
[Duration / Aspect ratio / Resolution]
[Continuity rules]
[Negative constraints — only if the model supports them]
```

Model-specific skeletons live in their reference files (`seedance.md`, `kling.md`, `veo.md`). For dramatic / multi-shot / character-locked Seedance work, the production-grade 11-block skeleton in `seedance.md` §6 supersedes this generic skeleton.

## 3. U2. Weight-at-start

Generators put more attention on the first 30-40% of tokens. Lead with subject and action. Style modifiers go at the end. Camera, lighting, and environment live in the middle.

## 4. U3. Show don't tell

The model cannot render feelings. It renders bodies. Translate every emotion into a physical action.

- Bad. "He is scared."
- Good. "His jaw locks. He stops breathing for one beat. His fingers curl against the doorframe."

## 5. U4. Natural language beats tag spam

Video models are not image models. Tag stuffing like "masterpiece, 4k, cinematic, beautiful" fails. Write in full cinematic sentences as if briefing a human DOP.

## 6. U5. One primary camera move per shot

Do not stack three camera moves in a 5-second clip. Pick one dominant move (dolly-in, pan, tracking, static). Layer a subtle micro-adjustment if needed (slight handheld shake, gentle rack focus). More than that produces visual chaos.

## 7. U6. Precise lens language

State the lens. "Shot on 50mm" works across all major models. Quick map:

- 24mm. wide, immersive, exaggerated space
- 35mm. natural documentary
- 50mm. intimate, human perspective
- 85mm. portrait, compressed background
- 100mm macro. texture, detail
- anamorphic 40mm. cinematic widescreen

Full vocabulary in `camera-lighting-vocabulary.md`.

## 8. U7. Character consistency anchor

Anchor identity at the START of every prompt. In a multi-clip sequence, repeat the full identity block in every single prompt. Video generators have no memory between generations. Treat every clip like briefing a brilliant intern with memory damage.

Identity block must include: face shape, eye color, skin tone. Hair color, length, style. Facial hair. Exact clothing items. Distinctive accessories.

Model-specific syntax for character locking:
- Seedance: `@img1` reference + identity block (see `seedance.md` §10)
- Kling: Element Binding with 3-4 reference images (see `kling.md`)
- Veo: reference ingredients / JSON identity (see `veo.md`)

## 9. U8. No contradictions

The model obeys the strongest signal. Contradictions produce artifacts.

- Bad. "Still pond" + "flowing water."
- Bad. "Close-up" + "wide cinematic landscape."
- Bad. "Quiet moment" + "explosive action."

## 10. U9. Concrete physical detail over abstract concept

"Loneliness" does not render. "A man sitting alone, shoulders collapsed, face lit by blue phone glow, empty bottles on the table" does.

This is the same rule as the Details Law in section 1, viewed from a different angle. Section 1 is the audit. This is the principle.

## 11. U10. Duration discipline

Most models work in 5-10 second clips. Longer narratives live in multiple clips stitched in the editor. Do not cram a 30-second story into a 5-second prompt.

Default splits:

- 10s = 2 clips × 5s
- 15s = 3 × 5s
- 30s = 6 × 5s
- 60s = 12 × 5s

Seedance is the only exception. It can pack 2-3 shots into one 5-10s clip via multi-shot syntax (see `seedance.md` §8).

## 12. U11. The final image rule

Every clip needs a clear final frame. The model uses the ending as emotional destination.

- "Ends on his face frozen in the blue refrigerator light" beats "he stands there sadly."

The final image is also one of the five anchors (see `dramaturgy.md` §13). Naming it is non-negotiable.

## 13. U12. The three-detail check (audit before sending)

Before returning the final prompt to the user, audit every shot. Each shot must carry at least one of each:

1. Environmental pressure (lighting, weather, surface, sound of the room).
2. Physical micro-action on the body (jaw, hand, breath, eye, gesture).
3. Sound anchor or recurring visual motif tied to the emotional spine.

If a shot has zero, fix it before sending. If a shot has only one, ask whether you can make it two without bloat. The strongest prompts in this skill's worked examples always have all three.

Empty descriptors that fail this check: "establishing wide shot", "beautiful lighting", "dynamic camera move", "cinematic look", "intense moment", "dramatic close-up". Replace each with three concrete physical facts.
