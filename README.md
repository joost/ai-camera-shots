# ai-camera-shots

**AI video without direction looks like 1895.** Left alone, image and video models fall back to one shot: eye level, medium distance, centred, camera still. This [Claude Code](https://claude.com/claude-code) skill gives Claude a director's vocabulary, so the prompts it writes say where the camera is, what the angle should do, how the camera moves and how one shot hands over to the next.

<!-- VIDEO: the spec ad (Lumière brothers), every shot planned with this skill. Coming soon. -->

## What it covers

- **Five decisions per shot:** distance, height and tilt, facing, lens and focus, movement. Anything left open falls back to the model's default.
- **34 shot types** grouped by those decisions, each with a fill-in template that works for people, products, food and objects, plus notes for turning the still into a clip.
- **Camera moves:** how to word them, which moves suit which angles, what models still get wrong.
- **Transitions built into the footage:** hidden cuts (object, body and water wipes), whip pans, match cuts, cut on action, first/last-frame bridges, and how to match the end of one clip to the start of the next.
- **Dialogue coverage** and **vertical 9:16** framing.
- **A checklist** to run on every prompt, and a shot-list format for storyboards.

It works with any model: Veo, Kling, Wan, Seedance, Sora, Runway, Midjourney, Flux, Nano Banana, GPT image and similar.

## Install

In Claude Code:

```
/plugin marketplace add joost/ai-camera-shots
/plugin install ai-camera-shots@joost
```

Or copy the skill folder by hand:

```
git clone https://github.com/joost/ai-camera-shots
cp -R ai-camera-shots/skills/ai-camera-shots ~/.claude/skills/
```

## Use

Ask Claude for what you need; the skill loads by itself:

- "Write a video prompt for our iced latte, something that stops the scroll."
- "Plan a 30-second shot list for this product, with two hidden cuts."
- "This generation looks flat. Fix the prompt."

Weak: `A cinematic shot of an iced latte on a café table.`

With the skill: `Low-angle close-up on a 35mm lens, camera resting on the marble café table a few centimetres from the glass and looking slightly up at a tall iced latte; milk folding down into dark espresso, condensation on the glass, morning window light behind it making a rim glow, the café behind softly blurred at f/2.`

## Credits

The list of 34 shot types follows "34 shot types every AI filmmaker should know" by [Rourke Heath / GenHQ](https://x.com/rourke_heath/status/2104501759674577301) and the GenHQ x Magnific 34 Shot Prompt Guide. Transition sources are listed in `skills/ai-camera-shots/references/transitions.md`.

## License

MIT
