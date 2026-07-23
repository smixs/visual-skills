# 🎬 Visual Skills — an AI Film Director for Your Agent

![Visual Skills — one toolkit for both images and video](assets/hero.webp)

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-blueviolet?style=flat-square)](https://docs.claude.com/en/docs/agents/agent-skills)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-orange?style=flat-square)](LICENSE)

**🇷🇺 [Читать на русском](README.ru.md)**

Two Claude Skills that turn your agent into a working film crew: `video` writes AI video prompts the way a director, screenwriter and editor would; `image` writes image prompts the way an art director would. Both pick the right model for the task, apply its exact syntax, and return a copy-paste-ready prompt.

Most prompting guides teach you syntax. This one teaches your agent **cinema** — and that is what makes it the strongest tool available for directing AI video. A beautiful frame without dramaturgy is wallpaper. Models render pixels; the skill directs them.

## Supported models

**Video:** Seedance 1.0 / 1.5 Pro / 2.0 / 2.0 Mini / 2.5 · Kling 1.6 – 2.6 Pro, Kling 3.0 / 3.0 Turbo / 3.0 Omni · Veo 3 / 3.1. Runway Gen-4, Luma, Pika and Sora are covered by the universal rules layer.

**Image:** Nano Banana 2 Lite / Nano Banana 2 / Nano Banana Pro (Gemini image family) · GPT Image 2 (plus legacy 1.5 / 1 / mini).

Model files are updated as new versions ship — Seedance 2.5 (30-second single-pass clips, 50 reference inputs, 3D camera blockout), Kling 3.0 Turbo and Omni, and Nano Banana 2 Lite are already in.

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

> "Напиши промпт для Seedance — голодный мужик ночью находит последнюю сосиску в холодильнике, 5 секунд, мульти-шот"

> "Раскадруй 30-секундный ролик про чувство вины. Главная эмоция — guilt. Опорный объект — телефон с непрочитанным сообщением."

> "Audit this prompt: [...]. What's broken, how to fix?"

> "Translate this script into 6 × 5-second Seedance prompts."

> "Make a keyframe set for a 15-second product film, then Kling prompts to animate each"

## Author

**Serge Shima** — [t.me/aimastersme](https://t.me/aimastersme) · [sergeshima.com](https://sergeshima.com) · [aimasters.me](https://aimasters.me)

## Credits

Dramaturgy distilled from Walter Murch (*In the Blink of an Eye*), Akira Kurosawa, David Fincher, Steven Spielberg, Jonathan Glazer and Bong Joon Ho. Model syntax verified against official ByteDance, Kuaishou, Google and OpenAI docs plus fal.ai prompting guides, July 2026.

## License

**CC BY 4.0** — use it, fork it, build on it, commercially too. One hard rule: **credit the author**. Any copy or derivative — including skills assembled by AI agents from these files — must keep the attribution line: *Serge Shima — [github.com/smixs/visual-skills](https://github.com/smixs/visual-skills)*. See [LICENSE](LICENSE) and [NOTICE](NOTICE).

**Tags:** `claude` · `claude-skills` · `ai-video-generation` · `ai-image-generation` · `seedance` · `kling` · `veo` · `nano-banana` · `gpt-image-2` · `ai-film-directing` · `storyboard` · `prompt-engineering`
