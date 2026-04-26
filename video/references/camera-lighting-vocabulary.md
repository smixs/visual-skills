# Camera, lighting, color, sound vocabulary

Use precise production language. "Cinematic" is not a direction. "35mm, slow push-in, warm window key from frame-left" is.

## Contents

1. Framing
2. Camera movement
3. Lens language
4. Light sources
5. Light direction
6. Light quality
7. Color discipline
8. Sound categories
9. Blocking language

---

## 1. Framing

- extreme wide shot
- wide shot
- medium wide
- medium shot
- medium close-up
- close-up
- extreme close-up
- macro insert
- over-the-shoulder
- POV
- profile
- silhouette
- low angle
- high angle
- top-down
- dutch angle
- locked-off frame

## 2. Camera movement

- static camera
- slow push-in
- fast push-in
- pull-back
- tracking shot
- lateral tracking
- handheld micro-shake
- whip pan
- snap zoom
- rack focus
- tilt up
- tilt down
- orbit
- gimbal glide
- dolly-in
- dolly-out
- crane shot
- aerial shot
- Hitchcock zoom (dolly-zoom)

Universal rule. Pick one dominant move per 5-second shot. Layer one subtle secondary move at most.

## 3. Lens language

- 24mm. Wide, immersive, exaggerated proximity.
- 35mm. Natural documentary.
- 50mm. Intimate, human perspective.
- 85mm. Portrait, compressed background.
- 100mm macro. Texture, detail.
- anamorphic 40mm. Cinematic widescreen.
- shallow depth of field.
- deep focus.
- compressed telephoto background.
- distorted wide-angle proximity.

## 4. Light sources

- cold refrigerator light
- harsh overhead kitchen LED
- moonlight through window
- neon sign spill
- phone screen glow
- car headlights
- streetlamp backlight
- fluorescent office light
- practical lamp
- candlelight
- monitor glow
- emergency red light
- sodium vapor street light
- police strobe
- theater house lights
- stage spotlight
- campfire flicker
- sunset through blinds
- under-counter kitchen LED

## 5. Light direction

- top light
- side light
- backlight
- underlight
- frontal soft light
- rim light
- bounce fill
- window key light
- motivated practical (the light source is visible in frame)

## 6. Light quality

- hard shadow
- soft diffused
- low-key lighting
- high contrast
- silhouette
- specular highlights
- volumetric haze
- steam catching backlight
- wet reflections
- desaturated palette
- cold blue-gray grade
- teal shadows
- clean commercial lighting
- gritty naturalistic
- blown-out overexposure
- crushed blacks

## 7. Color discipline

Define palette with concrete colors. Never write "cinematic colors."

Bad. "cinematic colors."
Good. "Cold blue-gray shadows, desaturated skin tones, greenish fridge spill, black negative space, no warm yellow tones."

If the user bans a color, obey it strictly. Repeat the ban in every clip of a multi-clip sequence.

Common palettes.

- Fincher cold. Cold blue-gray shadows, desaturated skin, black negative space.
- Deakins natural. Warm amber interiors, cool blue exteriors, clean contrast.
- Wong Kar-wai. Saturated warm reds, deep greens, hazy practicals.
- Glazer neon. Black, one dominant neon hue (magenta or teal), hard edges.
- Commercial creamy. Warm creams, soft pastels, clean whites, no harsh blacks.
- Safdie chaotic. Mixed sources, overlapping color temperatures, urban neon spill.

## 8. Sound categories

Even if the model does not generate audio, sound description helps structure rhythm.

Ambient.

- room tone
- distant city ambience
- rain on tin roof
- wind through leaves
- fridge hum
- fluorescent buzz
- traffic wash

Body and action.

- breath
- footsteps
- fabric rustle
- fork clink
- door hinge
- key in lock
- zipper
- stomach growl

Dramatic events.

- sudden silence
- low bass hit
- wet thud
- glass break
- distant thunder
- car door slam
- final sound cue before cut to black

For Veo, wrap sound in syntax. `Audio:`, `SFX:`, or `(parenthetical description)`.
For Seedance 1.5+, include sound in the prompt body.
For Kling, sound descriptions help rhythm planning but audio is not generated.

## 9. Blocking language

Describe physical movement with six inputs.

- Who moves.
- Where they start.
- Where they end.
- What object they touch.
- What they look at.
- What their body reveals emotionally.

Example.

```text
The man stands in the kitchen doorway, shoulders collapsed. He slowly approaches the refrigerator, opens it with hesitation, leans into the cold light, then freezes when he sees the empty shelves.
```

This beats "a sad man goes to the fridge" because it is playable by the model frame by frame.
