# Keyframes for an animatic (opornye kadry)

This is the still-panel layer. A storyboard keyframe is not a frame grab of footage — it is a single drawn image that must carry one story-beat with **no motion and (usually) no face**. The animatic hangs off these panels. A panel that only looks good is wallpaper; a panel must report its story function, its drama, and the motion it cannot show, all frozen.

This file converts a beat sheet / treatment into **opornye kadry**, then into image-generation prompts. It sits on top of `dramaturgy.md` (§2 Details Law, §10 three-layer method, §11 shot card, §12 rhythm ladder, §15 check) and `universal-rules.md` (U1 skeleton, U11 final image). Pairs with `camera-lighting-vocabulary.md` for framing/lens/light tokens, `role-modes.md` §4 for the function taxonomy, `patterns-and-genres.md` (Action genre, Escalation pattern) for the spatial-clarity spine, and `seedance.md` / `kling.md` / `veo.md` to animate each locked frame. Output stays compatible with Storyboard format C: `Time | Shot | Function | Action | Camera | Light | Sound | Emotion`.

The running brief through every example below: drag/drift race spot, cold combative palette (steel blue, cyan, magenta, mercury-white; **red and green as accents only**; amber only as the start-tree's alien pulse or a toxic spill), faces absent or unusably fragmented. Swap subject as the task demands — the method holds.

## Contents

1. What an animatic keyframe must do
2. The keyframe card (a still extension of the shot card)
3. How many keyframes per beat (density ladder)
4. Composing a still that reads as MOTION
5. Emotion without faces in a still
6. The loaded frame for one panel
7. From keyframe to image-gen prompt
8. Worked keyframe board for a 30s race spot
9. Checklist: does this keyframe earn its place

---

## 1. What an animatic keyframe must do

In an animatic the **panel is the unit, not the shot.** A shot has duration, motion, and sound to carry its function across time. A keyframe has one frozen image and must carry the same function in a single glance. So every panel does four things at once, in one still:

- **One readable story-beat** — name it in one sentence before generating. If you cannot, the panel is not ready (`dramaturgy.md` §1).
- **One function tag** — Establish / Reveal / Power / Pressure / Detail / Reaction / Shift / Impact / Aftermath / Exit (`role-modes.md` §4). The tag is the question the panel answers. In a faceless spot **Reaction** is reassigned from a human face to the *machine's* face — the needle jumping, the slick wrinkling, the nose squatting. Treat gauges and rubber as the actor.
- **One emotion** — routed through metal, rubber, light, or anatomy, never named (`dramaturgy.md` §2). Mixed signals = no signal.
- **One implied motion** — the movement the still cannot perform, frozen as its physical residue (§4).

A panel that carries a beat, a function, an emotion, and an implied motion earns its place. A panel missing any of the four is a *fantik* — wrapper without candy (`dramaturgy.md` §3). The discipline of this whole file is: **you cannot prompt "motion" or "emotion" into a still — you prompt the physical consequence each leaves behind.**

---

## 2. The keyframe card

The shot card in `dramaturgy.md` §11 describes a moving shot. A keyframe needs a *still*-specific card: every field describes a frozen image, and three fields are new (implied camera, emotion-via-object, motion-rendered-as-still). Fill every field before generating. Empty fields reveal missing direction.

```text
KEYFRAME CARD
- Panel ID.            01, 02, 03
- Timecode.            on-screen life in the animatic (e.g. 0:10.5, HOLD 2s)
- Function tag.        Establish / Reveal / Power / Pressure / Detail /
                       Reaction / Shift / Impact / Aftermath / Exit
- Beat.                what changes in the story in this one still
- Framing + lens.      ECU / CU / MCU / wide / macro insert / POV + lens token
                       (24mm immersive ... 100mm macro — camera-lighting-vocabulary.md §3)
- Subject / anchor.    the ONE object or anatomy the eye lands on in 0.3s
- Depth layers.        FG job (frame / obstruct / put us inside)
                       MG job (the subject / the act)
                       BG job (stakes / context / rival)
- Implied camera.      the move this still is the first frame OF
                       (push-in, whip, bumper-POV, joust) — what it would do if it ran
- Light + palette.     one motivated source + direction + the surface it rims;
                       concrete colors, amber-ban repeated
- Emotion-via-object.  the feeling a face would show, mapped to an object's state (§5)
- Motion-as-still.     which frozen cue carries the missing movement (§4):
                       smear / partial blur / streak / vector / sharp-blur / held stillness
- Caption / label.     one word: setup / commitment / mistake / recovery /
                       proof-of-speed / result
- Sound.               what audio sits under the held frame, where the cut bites
                       (fill even though it is a still — dramaturgy.md §11)
- Production note.      prop, rig, continuity anchor
```

The card maps straight onto format C: `Function`, `Framing`, `Implied camera`, `Light`, `Sound`, `Emotion-via-object` become the table columns. The three still-specific fields — **implied camera, emotion-via-object, motion-as-still** — are the ones a normal shot card does not force you to name, and they are exactly the ones that keep a panel from going flat.

---

## 3. How many keyframes per beat — the density ladder

**Loudness in the audio = panel count in the board.** Silence gets one held panel; a bang gets a burst. This is the still-panel reading of `dramaturgy.md` §12 (rhythm ladder) and `role-modes.md` §3 (editor density: 3-4 beats/5s drama, 4-7 narrative, 6-9 fast montage). The full 30s beat map is the worked board in §8; split it per `patterns-and-genres.md` §3 (30s = 6×5s).

| Beat | Density | Panels | Why |
|---|---|---|---|
| **Ritual / staging** (quiet) | 1 hero panel, held | 1 panel living 1.5-2.5s | A silent beat is monolithic. Do not subdivide it — its power is that nothing moves while the world holds its breath. One symmetric "breath" frame, most negative space, least motion. |
| **Pressure climbing** (amber stagger) | escalating singles | 3 panels, collapsing length | The Sportsman tree fires three ambers 0.5s apart — three drawable panels, each tighter than the last, cut length collapsing toward the green. |
| **Launch / impact** (bang) | 3-panel micro-burst → up to 6-9 | 6-9 panels at 8fr → 4fr | The audio bang is rendered as panel *density*, not one big image. Hip-hop montage: bumper-POV smear, side wheelspin, tach flare, clutch hand, lane-stripe strobe. |
| **Contest** (sustained roar) | alternating | fragment-cluster ↔ one held detail | Never two bang-clusters back to back. Between every burst, one held quiet panel — loud only works next to quiet. |
| **Aftermath / exit** (cut to silence) | 1 hero panel, held | 1-2 panels, ~2s hold | End on consequence, not explanation. One held still: drifting smoke, hand unclenching, car nosing into dark. |

**Allocation rule.** A 30s spot lands at ~18-26 panels. Plot the board as a descending duration staircase (≈2.5s → 0.5s → 4fr), broken only by the one pre-launch pause and the one post-finish hold. The board should *read* as an accelerating tachometer even on mute. Give a beat a micro-burst only when the audio detonates; everywhere else, one panel that holds is stronger than three that scatter.

---

## 4. Composing a still that reads as MOTION

A keyframe cannot ramp, cut, or whip. Each missing move resolves into one of **six frozen cues**. Never write "motion" — write the artifact motion leaves behind. State the cue in the card's *Motion-as-still* field and again in the prompt's camera/light clause; models default to over-clean stabilization and will sand the speed off unless told (§7).

| Cue | What it is in a still | Renders the implied move |
|---|---|---|
| **Directional motion-blur smear** | Background streaked along the travel axis, subject sharp. Guardrail, lane stripes, tree lamps pulled into horizontal light-rods. | tracking pass, POV launch, the whip-pan aftermath |
| **Frozen partial blur** | One moving element blurred (tyre sidewall, smoke bloom, shift hand mid-throw) while the anchor stays crisp — proof of a single arrested instant. | speed-ramp peak, launch, shift |
| **Streak-frame (implied whip)** | The whole panel raked into motion-streaks with one readable shape surviving (a wheel arc, the shifter) — a "between two shots" blur panel. | whip pan, transition beat |
| **Posture / trajectory vector** | A body or car locked in a pose that can only resolve forward — wrist cocked over the shifter, front wheels lifting, weight slung onto the rear axle. The eye finishes the move. | charged pose, freeze frame, launch |
| **Sharp-subject / blurred-field separation** | Shallow-DOF macro: knuckle, needle, latch razor-sharp, everything else dissolved. Isolation = the cut-to-detail frozen. | insert chain, crash-zoom arrival, hip-hop CU |
| **Freeze-frame stillness** | Deliberately *zero* blur, hard edges, held breath — reads as a stopped clock against the blurred panels around it. | the pre-launch held beat, the loaded spring |

Per-technique kit (triad + the still application):

- **Frozen motion blur** — what it does to emotion: differential blur reads as velocity made tactile, the world torn past a steady subject — where seen: Dod Mantle whip-panned every overtake in *Rush* so the background dissolves. — *in a keyframe* [Shift/Impact]: hero car tack-sharp, entire background raked into horizontal streaks, foreground objects elongated into light-rods. The most powerful single-panel speed trick: **sharp hero + fully smeared world.** Equal blur everywhere = soft photo; differential blur = speed.
- **Tyre wrinkle / partial blur** — emotion: physics you can feel, force arrested at its peak — seen: Goodyear's deliberately silent slow-mo of the slick sidewall folding; Ritchie's speed-ramp as the exclamation mark. — *in a keyframe* [Detail/Reaction]: macro into the rear sidewall, the wrinkle caught at its deepest fold, smoke just blooming at the contact patch, everything else crisp. One arrested ten-thousandth of a second. The hero detail to *hold*.
- **Smoke / debris / spray shape** — emotion: force given a visible body, dread made airborne — seen: NHRA burnout-cam, "a wall of smoke" backlit at ground level. — *in a keyframe* [Pressure/Power]: backlit tyre smoke as a luminous wall (front-lit smoke is dead gray nothing); water-box spray frozen as a constellation of specular droplets, each rimmed on its leading edge. Atmosphere only reads when light passes through it (§5).
- **Posture / lean vector** — emotion: a stillness that can only resolve forward; the eye does the launching — seen: Vaughn's charged poses (*Kingsman*, *Layer Cake*) — every frame loaded with a trajectory. — *in a keyframe* [Power/Shift]: **no neutral panels.** Car at idle = front wheels micro-lifting, body slung onto the rear axle. Hand on wheel = fingers mid-clench. Compose the negative space *ahead* of the subject, the direction it is about to fire into.
- **Leading lines / light streak** — emotion: a rail for the eye that also encodes direction and speed — seen: Papamichael's asphalt-in-frame (*Ford v Ferrari*), the road as the speedometer. — *in a keyframe* [Power/Impact]: lane centerline raking to a vanishing point, sodium/mercury practicals smeared as long reflections down wet asphalt. Keep the texture (chevrons, tar seams, rubber marks) so the streak has something to streak.
- **Off-balance dutch** — emotion: imbalance, loss of grip, threat — seen: Raimi's canted attack frames (*Evil Dead II*). — *in a keyframe* [Impact]: cant the horizon hard at the one loss-of-traction beat — tyre breaking away, car stepping sideways. Reserve it for a single instability beat so it stays loud; dutch as wallpaper reads as bad framing.

**The speed-budget rule** (from the race-truth school): a still sells velocity when **at least three of five coexist in one frame** — (a) camera at/below bumper height, (b) asphalt streaking the lower frame, (c) a near foreground reference passing the edge, (d) sharp hero against motion-blurred background, (e) a mechanical-vibration cue (trembling mirror, doubled needle, smeared rim). One cue is a car photo. Three is velocity. If a "fast" panel cannot name three, reframe lower, drag the camera to the asphalt, throw a cone or barrier into the foreground.

---

## 5. Emotion without faces in a still

A face does four jobs: shows the feeling, shows where it looks, shows the cost, shows the decision. Faces banned, redistribute: **decision → anatomy mid-action; internal state → an object crossing a threshold; looking/rivalry → space** (§6 and `dramaturgy.md` §2). Assign one job per panel and tag it. The emotion must already be frozen *inside the object* — a still cannot let motion blur do the emotional work for it.

Two load-bearing rules:

- **Anatomy only on a decision.** A hand at rest is filler; a hand *deciding* is a shot. Before drawing any hand/foot panel, name the verb — grip / latch / shift / preload / release. No verb, no panel. Render tendons raised, glove leather creasing, one hard side-light carving knuckle texture, the rest in shadow (Leone's hands-before-the-draw; Nike *Take It to the Next Level*, first-person, no hero face).
- **Objects only when they change state.** A static gear-lever says "car stuff" and flatlines. Board the **after** state of a threshold-crossing; the before is implied (Honda *Cog*: every object does something irreversible). Tach pinned in the red, not idling. Ignition lamp blooming live, not dark. Slick caught mid-fold.

Use the substitution table as the core deliverable — when the script wants an emotion and no face is available, render this object at this crop. Cold palette throughout.

| Emotion (a face would show) | Object substitute | Crop | Render note (the still) | Label / tag |
|---|---|---|---|---|
| **Fear / dread** | sweat bead on knuckle; tremor in the mirror reflection (not eyes) | macro / ECU | one hard specular highlight on the bead, cold rim, deep black around it; mirror edge doubled to imply vibration | setup → Pressure |
| **Resolve / commitment** | knuckles whitening on wheel or shifter; foot pinning throttle | CU / MCU | tendons raised, glove leather creasing, grip at maximum; one side-light, cabin in shadow | commitment → Shift |
| **Focus / lock-in** | start-lights reflected in lacquer / headlight glass (not a human eye) | MCU | staging bulbs mirrored as cold points on paint or chrome; tight, centered, still | setup → Detail |
| **Strain (machine at limit)** | tach needle pinned in red arc; slick sidewall wrinkling; exhaust flame | ECU / CU | needle hard against redline, motion-still but unmistakably max; sidewall at deepest fold | proof-of-speed → Pressure |
| **Mistake / panic** | tyre shake (sidewall "goes square"), wheel kicking back, revs over-flared | CU | sidewall deformed wrong, blur direction fighting the lane; tach spiked past the band | mistake → Impact |
| **Triumph / release** | grip relaxing; chute blooming; one nose past the stripe; smoke through headlight beams | CU → WS | fingers unfurling off the wheel; or distant clean geometry of the win, cold backlight through smoke | result → Aftermath / Exit |
| **Anticipation (pre-launch)** | finger over ignition / line-lock; pre-stage bulb lit; held shifter | ECU / CU | finger a hair off the button, bulb just lit cold, everything frozen — the "silence" panel | setup → Pressure |

State-change cheat-sheet (board the live state; the dead is implied): ignition dark → lamp blooming; tach idle → needle pinned red; slick round → wrinkle folded deep; water-box mirror-still → shredded by launch; front wheels planted → lifting; chassis level → squatted; chute packed → bloomed at the trap.

---

## 6. The loaded frame for one panel

A keyframe is a diagram the viewer solves in 0.3s and re-reads with pleasure at 1s. With no face, the geometry and the depth stack do the acting.

> **Core law of the loaded panel.** One focal point, one emotion, three working depth layers, zero dead objects. Answer one question in the first glance; reward a second look.

**Depth-layer jobs (FG / MG / BG).** Write the prompt in three explicit depth clauses, each with a stated job. This is the engine of "reads in one glance, rewards a second" (extends `dramaturgy.md` §10 into a single still). If all three planes carry the same blur or scale, you have one plane, not three — force a sharp MG subject against a soft FG frame and a soft BG stake (shallow DOF is the panel's hierarchy tool, `camera-lighting-vocabulary.md` §3).

| Plane | Default job | Drag-race objects | Function it serves |
|---|---|---|---|
| **Foreground** | frame / obstruct / put us inside | roll-cage bar, mirror edge, harness strap, smoke wisp, wet glass | Pressure, Power |
| **Midground** | the subject / the act | hand on shifter, knuckles on wheel, foot on pedal, tach face | Detail, Shift, Impact |
| **Background** | stakes / context / rival | staging bulb, rival lane headlight, finish line, narrowing barrier | Establish, Reveal, Pressure |

**One-glance + reward** — what it does to emotion: an instantly readable frame creates trust; a frame that rewards re-reading creates density and worth. With no face to anchor on, a muddy panel collapses to nothing. — *in a keyframe*: name the single focal point before generating (tach needle / staging bulb / knuckle), put it on a strong line, demote everything else to support. The second-look reward is a reflection, a bridge object, or a state indicator — one, not a clutter.

**Centerline spine, then break symmetry** — emotion: a single dominant axis (lane stripe, the Christmas Tree, a dividing wall) gives the eye a rail and makes even a chaotic frame readable; breaking it the instant one car noses ahead reads as momentum. — seen: Anderson centers for instant legibility; Bong breaks balanced staging to show a power shift. — *in a keyframe*: build one head-on symmetric "breath" panel — both cars mirrored across the centerline, Tree dead-middle, equal negative space (tag **Establish/Pressure**, hold longest). On the next panel, break the mirror — hero a nose ahead, rival shoved soft, centerline slid off the third (tag **Shift/Impact**). Use the pair exactly once, at the launch; overusing symmetry kills the speed.

**Functional vs decorative clutter — the evidence test.** Keep an object only if it does at least one of: (1) **indicator of state** (replaces the face — tach in the red, white knuckles), (2) **stage of action** (advances the beat — front wheel 7" off the line = pre-stage), (3) **bridge to the next panel** (sets up a match-cut or a reach). Dead detail — coffee cup, mirror dice, dashboard sticker — shows no state, advances nothing, bridges nowhere. Cut it. "Each object is a clue" (Park); functional clutter *loads* the frame, decorative clutter *weakens* it.

**Angle encodes the beat** (no face, so the angle *is* the emotion): low / ground-level = power, threat, launch force (**Power, Impact**); eye-level lateral = parity, rivalry stated (**Establish**); high / top-down = judgment, smallness, aftermath (**Aftermath, Exit**).

---

## 7. From keyframe to image-gen prompt

A keyframe card becomes a still prompt by following the universal skeleton (`universal-rules.md` U1) with weight at the start (U2). **Lead with framing + lens + light + palette + anchor object** — these are the load-bearing tokens for a still; the model puts most attention on the first 30-40% of tokens.

Panel → prompt skeleton:

```text
[Framing + lens]           e.g. "Low bumper-height macro, 24mm, shot past a blurred roll-cage bar"
[Anchor subject + state]   the ONE object at its threshold: "rear slick sidewall wrinkling at the contact patch"
[Depth clauses, 3 jobs]    FG frame / obstruct · MG subject / act · BG stake / rival
[Motion-as-still cue]      "sharp subject against horizontal motion-blurred background, foreground reference elongated into a light-streak, rear rim spokes smeared to a disc"
[Light + palette]          one motivated source + direction + surface it rims; concrete colors; amber-ban
[Texture]                  "fine film grain heaviest in shadow, halation on the practicals, one anamorphic flare, crushed blacks"
[Face rule]                "no face" — or "driver a featureless silhouette against blown rival headlights, only knuckle highlights legible"
[Aspect / no-speed-up note]  "no speed-ramp; build velocity into the static frame"
```

Rules that keep the still honest:

- **Name the differential blur explicitly.** Models default to over-clean stabilization. Write "motion blur on background, fast-shutter look, sharp subject, rim spokes smeared to a disc." Equal/no blur is the most-faked and most-failed cue (anti-fake firewall, §4 speed-budget).
- **Keep faces out or fragmented.** Convert any would-be face to silhouette / contre-jour with a rim and one glint. No features.
- **Render audio as physical consequence, never as a named sound.** "Loud engine" is banned filler (`dramaturgy.md` §2) — prompt "heat-haze warp off the headers, exhaust flame, chassis squat, sidewall wrinkle" instead.
- **Anti-sterile guard.** If the panel could be captioned "clean," "beautiful lighting," or "high quality," it has failed — name the grain, the bloom, the crushed black, the one specular hit (`universal-rules.md` U12). One motivated source dominates; ~70% of the frame stays unlit (`camera-lighting-vocabulary.md` §5-7).

Cross-link the vocabulary file for every framing/lens/light token. Then **the keyframe is the locked first frame**; hand it to `seedance.md` / `kling.md` / `veo.md` with the single dominant move (one per 5s — `camera-lighting-vocabulary.md` §2) to animate it. Name in the model syntax: "low bumper-height camera, asphalt streaking, motion blur on background, sharp subject, no speed-up."

---

## 8. Worked keyframe board for a 30s race spot

A Sportsman-tree drag run, cold palette, no faces — ~13 panels using the card. This is the deliverable template the user fills: each row is a compressed keyframe card, format-C compatible (`Time | Shot | Function | Action | Camera | Light | Sound | Emotion`). Cut length collapses toward the green, holds on the wrinkle, then accelerates to the finish.

| Time | Shot (anchor) | Function | Action (state-change + motion-as-still) | Camera (implied move) | Light (cold) | Sound | Emotion-via-object |
|---|---|---|---|---|---|---|---|
| 0.0–2.5 | Slick into water box | Establish | Front tyre breaks mirror-still water; bulb reflected in the sheet | locked macro, low (held) | steel-blue, wet specular | idle lope, water trickle | coiled stillness |
| 2.5–5.0 | Burnout wall | Power | Rear erupts a smoke wall, car straining on line-lock; smoke backlit luminous | ground-level wide (burnout-cam) | cyan backlight through smoke, red tail bleed | lope → tyre scream | leashed force |
| 5.0–6.5 | Pre-stage bulb + front tyre | Pressure | Tyre creeps, top blue bulb lights, beam line as graphic spine | CU, static | blue glow on wet metal | lope thickens | held breath |
| 6.5–8.0 | Stage bulb + knuckles | Pressure | Second bulb lit, knuckles whiten on the trans-brake (depth: bulb BG, hand FG) | CU, depth layers, static | two blue bulbs, crushed black | idle DROPS to silence | point of no return |
| 8.0–9.5 | Amber stagger (1 of 3) | Pressure → Shift | First amber lights; foot pre-loading the pedal | tree-cam, snap-tight | amber pulse (sole warm, toxic) | vacuum of silence | trigger tension |
| 9.5–10.3 | Held breath frame | Pressure | Staged car dead-still, last amber, tach needle the only tremor | symmetric, locked (HOLD) | amber flare, steel rim | silence (the pause) | loaded spring |
| 10.3–11.6 | LAUNCH lunge | Impact | Both cars squat, front wheels lift, green flares, asphalt smears back | low bumper-POV, fisheye (smear) | green flash + hard flare | BANG, leads pic 3fr | release / violence |
| 11.6–13.5 | **Slick wrinkle** (HOLD) | Detail / Reaction | Sidewall folds and hooks at the contact patch; speed-ramp pause, partial blur | macro slick-cam (frozen ramp) | hard side light, smoke bloom | tyre bite (near-silent) | physics felt |
| 13.5–15.5 | Cabin shake | Pressure | Needle buried in red, mirror doubled by vibration, glass strobing | hard-mount interior (tremor) | strobing exterior, red needle accent | rising rev, gear stab | strain |
| 15.5–18.5 | Bumper POV | Pressure | Asphalt tears under the nose, lane stripes strobe to a vanishing point | low forward hood-cam, 24mm (radial smear) | streaked specular, mercury-white | doppler build | commitment |
| 18.5–22.5 | Joust / parallel pass | Power | Rival closes head-on, offset; cone huge-blurred on the opposite edge | chase tracking + joust (closing) | streaked roadside lights, red tail accent | engine duel, doppler swell | rivalry |
| 22.5–26.5 | Finish | Impact | Slicks blown-up and distorted, two cars inches apart across the line | slight high, finish-cam | cold-white finish pool | sound peak → cut | margin |
| 26.5–30.0 | Hand unclenches / chute | Aftermath / Exit | Fingers release the wheel; chute bloomed, smoke drifting through a beam | ECU then rear wide (settling) | single cold rim, residue haze | hard cut to silence, one breath | consequence / release |

Notes on the board: the 9.5–10.3 held panel is the single most-held still — the pause that triggers the bang. The launch is *not* one hero frame; in a fuller cut, fan 10.3–11.6 into a 6-9 panel micro-burst (§3) — that expansion is what carries the 13 compressed rows up to the ~18-26 panel count of §3. The wrinkle is the one place time expands inside the loud section. No two bang-clusters touch; every burst is separated by a held quiet panel. End on consequence, held ~2s — the vacuum is the punctuation.

---

## 9. Checklist: does this keyframe earn its place

Run before every panel ships. Drop the panel if it fails.

- [ ] **Function tag named.** One of Establish / Reveal / Power / Pressure / Detail / Reaction / Shift / Impact / Aftermath / Exit. No tag → drop it.
- [ ] **One readable beat**, sayable in one sentence. If you cannot caption it (setup / commitment / mistake / recovery / proof-of-speed / result), it is a *fantik* — drop it.
- [ ] **Emotion-via-object** present — the feeling a face would carry, frozen in a knuckle / needle / pedal / smoke / sweat-bead (§5). No state-change, no emotion → drop it.
- [ ] **Speed or drama cue** present — ≥1 of the six motion-as-still cues (smear / partial blur / streak / vector / sharp-blur / held stillness), or a deliberate held-still pause. "Fast" panels carry ≥3 of the five speed cues (§4).
- [ ] **State-change, not static fetish** — the object crosses a threshold (idle→flare, clean→smoked, planted→lifting). No idle anatomy, no parked gear-lever.
- [ ] **Three depth layers**, each with a stated job (FG frame/obstruct, MG subject, BG stake). One focal point; every other object is evidence, not decoration.
- [ ] **Implied camera named** — the move this still is the first frame of, physically mountable on the car (no god-angle render).
- [ ] **Cold palette held** — steel/cyan/magenta/mercury-white, red and green as accents only, amber ≤15% and point-source (toxic, never cozy). One motivated source, ~70% unlit, one hard specular hit. Texture named (grain, halation, one flare), not "clean."
- [ ] **No face**, or a face fragmented past usefulness (silhouette / reflection only).
- [ ] **Sound cell filled** even though the panel is a still — what audio underlies the held frame, where the cut bites (`dramaturgy.md` §11).
- [ ] **Earns its density slot** — a held beat gets one panel, a bang gets a burst; the board reads as an accelerating tachometer on mute (§3).

If a panel survives all ten, it is an *opornyi kadr*, not wallpaper. Hand it to `seedance.md` / `kling.md` / `veo.md` as the locked first frame.

---

*Author: Serge Shima ([t.me/aimastersme](https://t.me/aimastersme) · [sergeshima.com](https://sergeshima.com) · [aimasters.me](https://aimasters.me)) · License: CC BY 4.0 — attribution required · Source: [smixs/visual-skills](https://github.com/smixs/visual-skills)*
