---
name: ai-camera-shots
description: Pick and phrase camera shots and transitions for AI image and video generation (shot size, camera height, subject angle, lens, focus, camera movement, dialogue coverage, vertical 9:16 framing, and in-camera transitions such as hidden cuts, object or body wipes, whip pans, match cuts, cut on action and first/last-frame bridges) so generations look directed instead of generic. Use whenever writing a first prompt, or reviewing or fixing one, for AI image or video models (Wan, Kling, Veo, Sora, Runway, Seedance, Hailuo, Higgsfield, Seedream, Magnific, Midjourney, Flux, Nano Banana, GPT image and similar), planning a shot list or storyboard for AI clips, turning a still into a clip, making cuts between AI clips smoother, or when a generation looks flat, stock-like or "too AI", even if the user never mentions camera angles. Not for animating HTML elements or edit-side dissolves and wipes in an editor.
---

# AI camera shots

Generic AI output usually comes from prompts that describe *what* is in the frame but not *where the camera is*. The model then falls back to its default: eye level, medium distance, centred, static, a normal lens. Naming the shot is the cheapest way out of that default.

**The project's own camera rules come first.** This skill gives the vocabulary and sensible defaults. If the project has its own camera grammar (a look bible, a format file, a style skill), follow that and use this skill to phrase it. Example: in deadpan comedy the locked eye-level camera is the straight man, so a Dutch angle, fisheye or flashy move there is a deliberate break (a gag in itself) that has to be chosen, never a default.

Before the first shot, fix the **aspect ratio** (see [Vertical 9:16](#vertical-916)) and whether the piece is **dialogue or montage** (see [Dialogue](#dialogue-and-coverage)). Both change which answers below work.

## Five decisions per shot

Answer these for every shot. Anything left open falls back to the model's default.

1. **Distance**: how much of the subject fills the frame (wide, medium, close-up, macro).
2. **Height and tilt**: where the camera sits vertically (worm's-eye up to aerial) and whether the horizon is level (Dutch angle).
3. **Facing**: which side of the subject we see, or whose eyes we look through (profile, three-quarter, rear, over-the-shoulder, POV, selfie).
4. **Lens and focus**: focal length, distortion, what is sharp, what sits in front of the subject (fisheye, 85mm f/1.8, foreground occlusion).
5. **Movement** (video only): what the camera does during the clip (static, push-in, orbit, handheld).

Optionally add one special (lens flare, prism, an object's-eye view). More than one per shot turns into a gimmick.

In a sequence, decide one more thing per shot: **the join**, meaning how this shot hands over to the next (see Transitions below).

Full vocabulary:
- `references/shot-types.md`: the 34 shot types, grouped by the decision they answer. Each has a template for any subject and a video note (the list follows the GenHQ x Magnific guide, credited there). Read it when choosing or phrasing shots.
- `references/camera-moves.md`: camera movement wording, which moves suit which angles, and what models do badly. Read it for any video or image-to-video prompt.
- `references/transitions.md`: transitions built into the footage (hidden cuts, object and body wipes, whip pans, first/last-frame bridges, cut on action), how to match the end of one clip to the start of the next, and a shot-by-shot breakdown of an ad that chains them. Read it whenever planning more than one shot.

## Pick shots by what the beat must do

| The beat needs to | Reach for |
|---|---|
| Establish place or scale | wide, aerial, high-angle |
| Sell product detail or texture | macro, close-up, low-angle close-up, foreground focus |
| Make the subject powerful or heroic | low-angle, worm's-eye, low-angle close-up |
| Make it small, or show a layout | high-angle, overhead |
| Feel intimate or emotional | close-up, profile, foreground focus |
| Put the viewer inside the scene | POV, over-the-shoulder, selfie, ground-level |
| Feel energetic, chaotic, like a party | Dutch angle, fisheye, wide-angle close-up, handheld |
| Build mystery or anticipation | rear, silhouette, foreground occlusion |
| Stop the scroll with surprise | object's-eye views (inside a hole, inside the fridge, hoop-level), magnifying glass, prism |
| Look clean and graphic | overhead, profile, silhouette |
| Cover a conversation | eye-level singles, over-the-shoulder, reaction shots (see [Dialogue](#dialogue-and-coverage)) |
| Let a line or punchline land | static eye-level single; how long to hold depends on the style (see [Dialogue](#dialogue-and-coverage)) |

For a sequence, change the distance between consecutive shots (wide, then close, then medium). Two cuts at the same size and angle read as a jump cut. For a reveal, start obscured (occlusion, silhouette, rear) or far away, and end close.

## Writing the prompt

- **Lead with the shot.** Put the camera phrase in the first sentence ("Low-angle close-up of ..."). A long subject description otherwise takes over, and early words tend to carry more weight. A structure that works: `<style>, <aspect ratio>, <shot + where the camera is>. <what the shot should do to the subject>; <light>, <background or focus>.` Then add the subject details.
- **Say what the angle should achieve, and name a visual cue that proves it**: "make the glass feel monumental", "the bar top runs diagonally", "the coaster fills the foreground". When a model ignores an angle, add the cue only that angle would produce.
- **Write it as one phrase, not a tag list.** "Low-angle close-up on a 24mm lens, camera at bar-top height looking up at the glass" works better than "low angle, close-up, 24mm, cinematic".
- **Anchor the camera physically.** Say where the camera is relative to something in the scene: "camera resting on the table", "camera at the bottom of the hole looking up". Physical placement survives better than abstract labels, especially for unusual angles.
- **Add a lens and aperture when depth matters.** 14–24mm exaggerates perspective and space, 35–50mm looks natural, 85–135mm compresses the background into soft bokeh, and a 100mm macro lens shows tiny detail. Use f/1.4–2.8 for shallow focus.
- **For focus shots, name what is blurred, not only what is sharp.**
- **Don't contradict yourself.** Use one distance, one height and one facing. "Overhead worm's-eye" or "macro establishing shot" makes the model pick one at random.
- **Write what should be seen, never what shouldn't.** Negations often backfire: "no lips" gave lips, and "an empty snack wrapper" gave full bags. Name the state you want ("static camera, locked-off tripod"), and pick objects whose default look is that state.
- **"Cinematic" alone does almost nothing.** Replace it with an actual shot, lens and light.

## Image to video: split the work

For product and brand shots, generating the still first and then animating it is the most controllable route.

- **The image prompt carries the composition**: distance, height, facing, lens, focus and light. A video model can't move to an angle the still doesn't show without inventing content, so get the angle right in the still.
- **The video prompt carries what changes**: one camera move, the subject's action and the speed. Restate the subject in a few words. Re-describing the whole image invites drift.
- **One camera move per clip.** Orbit plus crane plus zoom usually turns to mush.
- **Say "static camera, locked-off tripod" when you want no movement.** Models otherwise often add a slow drift.
- **Keep montage clips short (3–6 s per shot).** Faces, hands and text drift more the longer a clip runs.
- **Control the move with a last frame.** If the tool supports first and last frames, generate the end still with the same image prompt at the target framing (for example, pushed in to a close-up). Support differs by model *and* by provider (Wan 3.0 via OpenRouter rejected a last frame in Oct 2026), so check before planning around it. Without one, prompting "ends in the same pose" is often ignored: cut on an action, or pick the cut point in the edit where the two states match.

## Vertical 9:16

Most shot vocabulary (and every template in `references/shot-types.md`) assumes 16:9. In a tall frame:

- **Compose natively** in 9:16; don't plan a 16:9 frame and crop it. Close-ups and mediums work best, and a **centred subject usually beats the rule of thirds** in a narrow frame.
- **Use the height in wides:** space or architecture above, the subject in the lower-middle, a foreground object at the bottom. Swap width cues ("the lawn stretches out") for height cues ("the vault rises above").
- **No side-by-side two-shots:** the faces end up at the edges with dead space between. Cover two people with alternating singles, or stack them in depth (one face near and low, one far and higher).
- **Moves along the lens axis or vertical** (push, pull, tilt, pedestal) suit the frame. Sideways trucks, pans and lateral action push the subject out of it quickly. A profile is shown better by a tilt than by a track.
- **Leave room for the platform UI:** eyes on the upper-third line (35–40% from the top); faces and captions between about 15% and 75% of the height.

## Dialogue and coverage

For scenes where people talk (sketches, lip-sync clips, interviews), the camera's job is to make the conversation easy to follow:

- **Cover it like a real shoot:** one wide or master to set where everyone is, then a single for each speaker, over-the-shoulders, and separate reaction shots. In vertical, singles carry most of it.
- **Keep the 180° line.** All cameras on one side of the speakers: A always looks screen-right, B always screen-left, and the eyelines meet.
- **Match the singles:** same lens, camera height and shot size for both speakers, so cutting between them feels even (shot/reverse shot).
- **One speaker per clip,** close or medium close (faces and lip-sync break down in wides). Camera static or a very slow push; ask for minimal head movement. For a talking face inside a locked-off two-shot, lip-sync a crop of that speaker and paste it back; routes, voices and lip-sync checks are in the `ai-talking-characters` skill.
- **Keep hands out of talking shots.** A hand holding a pen or tool warps while the mouth moves. Give the hand action its own insert, without speech.
- **Reactions are their own clips,** static and at eye level. How long to hold one is a style choice: deadpan holds 1–2 s after the line (the non-reaction is the joke), while fast-cut comedy and interviews cut away right after it.
- **Cut at the end of a line, on a reaction, or on an action** (a turn, a look). If a clip runs on, cut where the face matches the next shot (mouth closed, same head position).

## Transitions

Transitions you want in the footage must be planned before generating. A body wipe can't be added in the edit. First decide where each transition lives:

1. **Inside one clip**: the camera move is the transition (a pull-out reveal, a push through a doorway).
2. **Hidden cut**: clip A ends and clip B starts in the same filled, blurred or dark state (papers thrown at the lens, a sleeve sweeping past, a whip pan), so the cut disappears. Put the same carrier in both clips, match direction and speed, and describe the physics ("one matte sheet covers the whole frame"), not "seamless transition". Two generations never meet in exactly the same state; when the carrier must fill the frame (water, steam, smoke), add its full-cover moment as a layer in the edit that both clips pass through.
3. **Generated bridge**: give the model a first and last frame and prompt the motion between them. Best for transformations.
4. **Motivated hard cut**: cut on action, exit and enter frame, smash cut. This is the montage default. Keep screen direction and change shot size by a clear step.
5. **Edit-only** (fade, dissolve, J/L cut): do it in the editor; don't prompt it.

Use hidden cuts and bridges as accents (1–3 in a 30–40 s piece). Details and prompt examples are in `references/transitions.md`.

## Plan around what video models get wrong

- **Text and logos warp when they move.** Keep branded objects facing the camera with little motion, or add the text in post.
- **Hands doing fine tasks glitch** (stirring, pouring, opening). Frame so only part of the hand shows, or let the object move instead.
- **Liquids hold up better in slow motion and macro.** Fast pours turn to jelly.
- **Dutch tilt and fisheye distortion get "corrected" mid-clip.** Restate them in the video prompt.
- **Faces smear in wide shots.** Don't let a wide carry an expression.
- **Rack focus is unreliable.** The focus often doesn't shift, or faces drift while it tries. For a shift that must land, make two stills (near sharp, then far sharp) and cut between them; treat a prompted rack as a bonus take.
- **Unusual angles work better image-first.** For inside a hole, inside the fridge or hoop-level, generate several stills, pick the best, then animate it.
- **Static props morph and styles drift over a clip.** A prop that should stay put can sprout parts (a lens grew on a camera box seen from above, Wan 3.0), and stylised characters drift toward photoreal over 5 s. Use the early seconds, start a follow-on clip from an early frame, and patch a static prop back from the still in the edit.
- **Water or rain on the lens reads as weather.** "Water runs down the lens" gave a rainy scene. For a liquid wipe, let the clip deliver the splash and add the covering sheet of water in the edit.

## Check every prompt

Run this on a first draft before generating, and on an existing prompt when reviewing or fixing one:

- [ ] The shot phrase comes first, and distance, height, facing and lens/focus are answered (or left open on purpose).
- [ ] One distance, one height, one facing: no contradictory labels.
- [ ] It says what the angle should achieve, plus one visual cue that proves it; unusual angles are anchored to something physical.
- [ ] Everything is worded positively, with no "no …" or "without …".
- [ ] Video: one camera move with a speed and an end point, or "static camera, locked-off tripod".
- [ ] It fits the aspect ratio and the project's own camera rules.
- [ ] Known weak spots are planned around: moving text, hands in talking shots, faces in wides, rack focus, fast moves over fine detail.
- [ ] In a sequence: the size or angle changes from the previous shot, screen direction holds, and the join is decided.

## Output format

When asked for a shot list, storyboard or clip prompts, give each shot in this shape:

```
Shot 3 · 12–18 s · "the bloom"
Shot: low-angle macro, camera at the base of the glass, 100mm macro, f/2.8
Why: the colour change starts at the bottom, so the camera starts there
Image prompt: <full prompt, shot phrase first>
Video prompt: <one move + action + speed, or "static camera">
Watch out: <the one thing most likely to break>
Join: <how this shot ends and the next begins, e.g. "hard cut on the beat" or "hidden: the stick passes the lens; the next shot opens with the stick still filling the left of the frame">
```

For a single image, give the image prompt (shot phrase first) and one line on why that shot.

## Example

Weak: `A cinematic shot of an iced latte on a café table.`

Strong image prompt: `Low-angle close-up on a 35mm lens, camera resting on the marble café table a few centimetres from the glass and looking slightly up at a tall iced latte; milk folding down into dark espresso, condensation on the glass, morning window light behind it making a rim glow, the café behind softly blurred at f/2.`

Matching video prompt: `Slow push-in toward the glass over 5 seconds; the milk keeps folding into the coffee in slow motion; camera otherwise steady.`

A three-shot sequence for the same coffee: overhead (the hand sets the glass down on the table), then the low-angle close-up above (the pour), then foreground focus (the glass sharp, a customer blurred behind it reaching in). Each cut changes distance and height.
