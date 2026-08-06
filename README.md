<div align="right"><strong>En</strong> | <a href="README.ru.md">Ru</a></div>

# 🎬 Visual Skills — AI Film Director for Your Movie

![Visual Skills — one toolkit for both images and video](assets/hero.webp)

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet?style=flat-square)](https://docs.claude.com/en/docs/agents/agent-skills)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-orange?style=flat-square)](LICENSE)

Two Claude Skills that turn your agent into a working film crew: `video` writes AI video prompts the way a director, screenwriter and editor would; `image` writes image prompts the way an art director would. Both pick the right model for the task, apply its exact syntax, and return a copy-paste-ready prompt.

Most prompting guides teach you syntax. This one teaches your agent **cinema** — and that is what makes it the strongest tool available for directing AI video. A beautiful frame without dramaturgy is wallpaper. Models render pixels; the skill directs them.

## What's new

**2026-08-04 — Seedance 2.5 production reference.** New [`video/references/seedance-25.md`](video/references/seedance-25.md), built from ByteDance's official User Guide and Prompt Guide (released July 31): the official prompt formulas, the `( ) < > { } 【 】` audio/dialogue/text markers, the 50-slot reference discipline with stability tables, stages + end states for 30-second single-pass clips, video editing (partial re-render), extension to 60s, Ultra Long mode (30–180s), the 3D-blockout / green-screen pipeline, and three official worked examples. Cross-model additions landed too: a transition vocabulary and an uncommon-term translation pattern in the camera file, reference-role discipline and priority declaration in the universal rules.

## Supported models

<table>
  <tr>
    <th colspan="6" align="center"><sub>VIDEO · DEDICATED MODEL FILE, EXACT SYNTAX</sub></th>
  </tr>
  <tr>
    <td colspan="2" align="center" width="33.3%"><a href="video/references/seedance.md"><img width="38" alt="Seedance" src="assets/logos/bytedance-color.svg"><br><b>Seedance</b></a><br><sub>1.0 · 1.5 Pro · 2.0 · 2.0 Mini · 2.5</sub></td>
    <td colspan="2" align="center" width="33.3%"><a href="video/references/kling.md"><img width="38" alt="Kling" src="assets/logos/kling-color.svg"><br><b>Kling</b></a><br><sub>1.6 – 2.6 Pro · 3.0 · Turbo · Omni</sub></td>
    <td colspan="2" align="center" width="33.3%"><a href="video/references/veo.md"><img width="38" alt="Veo" src="assets/logos/deepmind-color.svg"><br><b>Veo</b></a><br><sub>3 · 3.1</sub></td>
  </tr>
  <tr>
    <th colspan="6" align="center"><sub>IMAGE · DEDICATED MODEL FILE, EXACT SYNTAX</sub></th>
  </tr>
  <tr>
    <td colspan="3" align="center" width="50%"><a href="image/references/nano-banana.md"><img width="38" alt="Nano Banana" src="assets/logos/nanobanana-color.svg"><br><b>Nano Banana</b></a><br><sub>2 Lite · 2 · Pro <em>(Gemini image family)</em></sub></td>
    <td colspan="3" align="center" width="50%"><a href="image/references/gpt-image.md"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/logos/openai-dark.svg"><img width="38" alt="GPT Image" src="assets/logos/openai.svg"></picture><br><b>GPT Image</b></a><br><sub>2 · legacy 1.5 / 1 / mini</sub></td>
  </tr>
  <tr>
    <th colspan="6" align="center"><sub>COVERED BY THE <a href="video/references/universal-rules.md">UNIVERSAL-RULES</a> LAYER</sub></th>
  </tr>
  <tr>
    <td colspan="6" align="center">
      <picture><source media="(prefers-color-scheme: dark)" srcset="assets/logos/runway-dark.svg"><img width="17" align="middle" alt="Runway" src="assets/logos/runway.svg"></picture> <b>Runway</b> <sub>Gen-4</sub>
      &nbsp;&nbsp;
      <picture><source media="(prefers-color-scheme: dark)" srcset="assets/logos/luma-color-dark.svg"><img width="17" align="middle" alt="Luma" src="assets/logos/luma-color.svg"></picture> <b>Luma</b>
      &nbsp;&nbsp;
      <picture><source media="(prefers-color-scheme: dark)" srcset="assets/logos/pika-dark.svg"><img width="17" align="middle" alt="Pika" src="assets/logos/pika.svg"></picture> <b>Pika</b>
      &nbsp;&nbsp;
      <picture><img width="17" align="middle" alt="Sora" src="assets/logos/sora-color.svg"></picture> <b>Sora</b>
    </td>
  </tr>
</table>

Model files are updated as new versions ship — Seedance 2.5 has a dedicated production reference built from ByteDance's official guides of July 31, 2026 (30-second single-pass clips, 60s extension, 30-180s Ultra Long mode, 50 reference inputs, video editing, 3D camera blockout); Kling 3.0 Turbo and Omni and Nano Banana 2 Lite are already in.

## Dramaturgy first, syntax second

The heart of the `video` skill is `references/dramaturgy.md` — a working distillation of how great films are actually built, adapted for 5-30 second AI clips:

- **The scene formula.** A scene exists only when five elements are present: the hero's desire, the obstacle, the geometry of the space, the controlled gaze, and the editing rhythm. Anything less is decoration.
- **The Details Law.** Every shot must own three physical details: one environmental pressure (cold refrigerator light, wet asphalt), one micro-action of the body (jaw locks, knuckles whiten), one sound anchor or visual motif. Emotions named without a body do not render.
- **Walter Murch's Rule of Six.** Where to cut, in priority order: emotion 51%, story 23%, rhythm 10%, eye-trace 7%, screen plane 5%, 3D space 4%. Cutting "for pace" alone is item three — serving it before emotion and story is how TikTok mush gets made.
- **The three-jobs rule.** Every shot either changes emotion, advances action, or increases pressure. A shot that does none gets deleted, however pretty.
- **Blocking and staging.** Fincher's motivated camera (every move answers "what changed?"), Spielberg's spatial clarity (even in chaos the viewer knows where the hero, the threat and the exit are), Kurosawa's environment-as-character (one weather, one pressure, carrying the emotion of the scene).
- **Montage as rhythm.** The rhythm ladder — long, shorter, shorter, pause, impact. The pause before the hit matters more than the speed of the cuts. Beat maps for 15 / 30 / 60 / 90 seconds with Hook, Pressure, Crack, Impact and Aftermath.
- **The 14-field shot card and the five anchors.** Every storyboard row carries framing, camera, movement reason, eye-trace, cut type, sound and light; every piece commits to one emotion, one motif, one object, one break, one final image.

Banned everywhere: "cinematic", "epic", "stunning", "masterpiece", "beautiful lighting". Each of those words is a placeholder for a detail the writer failed to invent — and none of them render.

## How the video skill works

The `SKILL.md` body is a thin router; the craft lives in reference files the agent is forced to load in order:

1. **Dramaturgy** (`dramaturgy.md`) — scene formula, beats, shot functions, rhythm.
2. **Universal rules** (`universal-rules.md`) — the 12 rules that hold for every model: prompt skeleton, character anchors, show-don't-tell, duration discipline, the final-image rule.
3. **One model file** — `seedance.md`, `kling.md` or `veo.md`: exact syntax, multi-shot markers, dialogue protocols, reference tags, failure modes with fixes.
4. **Task modules when needed** — storyboards and role modes, animatic keyframes, race-and-speed grammar, genre patterns, prompt-fix skeletons, camera and lighting vocabulary.
5. **Two mandatory checks before output** — the six-point dramaturgy check and the three-detail audit on every shot. A prompt that fails either does not ship.

Output formats: a single prompt, a stitched multi-clip sequence with continuity blocks, a storyboard table, a prompt audit ("what breaks, what's missing, stronger version"), a director treatment, or Veo JSON.

## What the image skill does

Art direction for still images: editorial and product photography, posters, UI mockups, infographics, edits with hard preservation, character continuity across a series, storyboards and animatic keyframes for the video pipeline. It picks between Nano Banana and GPT Image 2 per task (grounding of real places, extreme aspect ratios and cheap batches go to Nano Banana; dense text, brand assets and preservation-critical edits go to GPT Image 2), then writes the prompt in that model's native structure.

The two skills chain: `image` builds the character sheets and keyframes, `video` turns them into motion with a proper motion brief instead of a re-described scene.

## Install

Works in Claude Code, Claude.ai Projects, Cursor, Windsurf, Cline, OpenCode, Hermes — anything that reads the Claude Skill format (plain markdown, no lock-in).

```bash
git clone https://github.com/smixs/visual-skills.git
cp -r visual-skills/video visual-skills/image ~/.claude/skills/
```

Or install the packaged archives: `claude install video.skill` / `claude install image.skill`.

## Usage

> "Write a Seedance prompt — a hungry guy at night finds the last sausage in the fridge, 5 seconds, multi-shot"

> "Storyboard a 30-second film about guilt. Core emotion — guilt. Anchor object — a phone with an unread message."

> "Audit this prompt: [...]. What's broken, how to fix?"

> "Translate this script into 6 × 5-second Seedance prompts."

> "Make a keyframe set for a 15-second product film, then Kling prompts to animate each"

## Author

**Serge Shima** — [t.me/aimastersme](https://t.me/aimastersme) · [sergeshima.com](https://sergeshima.com) · [aimasters.me](https://aimasters.me)

## Credits

Dramaturgy distilled from Walter Murch (*In the Blink of an Eye*), Akira Kurosawa, David Fincher, Steven Spielberg, Jonathan Glazer and Bong Joon Ho. Model syntax verified against official ByteDance, Kuaishou, Google and OpenAI docs plus fal.ai prompting guides, July 2026.

Vendor marks in the model table come from [lobe-icons](https://github.com/lobehub/lobe-icons) (MIT). Each mark stays the property of its owner and is used here only to identify the model it labels.

## License

**CC BY 4.0** — use it, fork it, build on it, commercially too. One rule: **credit the author**. Any copy or derivative — including skills assembled by AI agents from these files — must keep the attribution line: *Serge Shima — [github.com/smixs/visual-skills](https://github.com/smixs/visual-skills)*. See [LICENSE](LICENSE) and [NOTICE](NOTICE).

**Tags:** `claude` · `claude-skills` · `ai-video-generation` · `ai-image-generation` · `seedance` · `kling` · `veo` · `nano-banana` · `gpt-image-2` · `ai-film-directing` · `storyboard` · `prompt-engineering`
