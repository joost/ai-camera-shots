# Transitions for AI video

A transition is how shot A becomes shot B. There are two kinds:
- **Built into the footage** (in-camera): a pull-out reveal, papers thrown at the lens, a whip pan, the subject leaving the frame. These must be planned before you generate, because they can't be added afterwards.
- **Added in the edit**: fade, dissolve, iris, graphic wipe, sound bridge. These belong to the editor, not the prompt.

This file covers the first kind, plus the editing craft that makes plain cuts between AI clips flow.

Contents: [Where it lives](#decide-where-the-transition-lives) · [Inside one clip](#1-inside-one-clip) · [Hidden cut](#2-hidden-cut-between-two-clips) · [Generated bridge](#3-generated-bridge) · [Motivated cut](#4-motivated-hard-cut) · [Edit-only](#5-edit-only) · [How many](#how-many) · [Worked example](#worked-example-eleven-v4-spec-ad)

## Decide where the transition lives

| Where | What it is | Typical use |
|---|---|---|
| 1. Inside one clip | One generation; the camera move does the transition | Opening reveal, punch in on a detail, moving through a doorway or window |
| 2. Hidden cut between two clips | A ends and B starts in the same filled, blurred or dark state, so the cut is invisible | Location changes that should feel like one continuous move |
| 3. Generated bridge | The model invents the motion between two stills (first and last frame), or morphs one into the other | Transformations: colour change, object becomes another object, day to night |
| 4. Motivated hard cut | A visible cut, but motion or a gesture carries the eye across it | Most montage cuts, scene changes in dialogue or comedy |
| 5. Edit-only | Fade, dissolve, iris, graphic wipe, J/L cut (audio leads or trails the picture) | Time passing, endings, chapter breaks |

## 1. Inside one clip

| Transition | Wording |
|---|---|
| Pull-out reveal | `starts as an extreme close-up of [detail], camera pulls back fast to a wide shot revealing [scene]` |
| Push-in / crash zoom to a detail | `camera pushes in fast from a wide shot to an extreme close-up of [detail]` |
| Push through a portal | `camera moves forward through [doorway, window, keyhole, the glass] and emerges in [new space]` |
| Rack focus | `focus shifts from [near object] to [far subject]` (ends the shot on a new subject without a cut; unreliable, so have a two-stills-and-a-cut fallback) |
| Roll | `camera rolls 90 degrees clockwise while pushing forward` (works best without a visible horizon) |

Name the start framing, the end framing, one move and the speed. Example: `Starts as an extreme close-up of his laughing mouth; the camera pulls back fast to a medium-wide of him lounging in a gilded armchair reading papers.`

Writing "then it cuts to" in one prompt usually produces a soft morph instead of a cut. Models are trained on continuous motion. If you want a cut, make two clips.

## 2. Hidden cut between two clips

**The principle:** shot A ends and shot B begins in the same state (filled, blurred or dark). The cut sits on a frame with nothing to compare, so the eye doesn't see it.

**What carries the cut:**
- **Object wipe**: something is thrown at or passes across the lens until it fills the frame (papers, a hand, a glass, confetti, a passing person or train).
- **Body wipe**: the subject moves into or past the lens (stands up toward the camera, turns, walks in close).
- **Whip pan**: a fast pan into motion blur; B starts in blur moving the same direction at the same speed. Models under-deliver the speed ("whips fast to the left" came back as a slow head turn and a moderate pan, Wan 3.0): generate it, then speed the pan up 3–4× in the edit and add horizontal motion blur that grows toward the cut.
- **Lens block or dip to dark**: into a dark coat, a doorway, a tunnel, a hand over the lens; B starts dark and opens up.
- **Portal**: the camera pushes into a hole, a keyhole, a glass or a mouth; B starts inside or emerges from it.
- **Screen**: a phone or TV screen grows until it fills the frame and becomes the new scene. Shoot it flat-on, filling about 80% of the frame.
- **Arc or roll continuation**: B picks up A's orbit or spin at the same speed. A pillar passing the lens can hide the join.

**Matching checklist:**
- **Same carrier in both shots.** If papers cover the end of A, papers are still falling at the start of B.
- **Same direction and speed.** A whip right ends A, so a whip right starts B.
- **Similar lens and camera height.** A 24mm push won't cut against an 85mm push.
- **Full coverage.** A must actually reach a completely filled frame. State the end condition: "until one sheet covers the entire frame".
- **Action already in progress in B.** No dead starts: the move or gesture continues from the first frame.
- **Matching exposure at the join.** Both fully dark, or both fully blurred.

**Prompting:**
- **Describe the physics, not the effect.** "Seamless transition" tends to produce a visible effect. Write "the dark wool sleeve sweeps across the lens and fills the whole frame".
- **Make the carrier matte and soft.** Models over-sharpen and over-light foreground objects. Say `matte, unlit, out of focus`.
- **Generate longer than you need** so the clip doesn't end before full coverage, then trim.
- **Something passing over or through the camera** (a train, a car, a wave): anchor its path and spell out each stage. "Its wheels rolling on the two rails … thunders right over the camera: the frame goes dark under the passing locomotive, then thick white steam engulfs the lens" worked in one take; without the rails and the stages, the train drifted off the track and the clip jumped to another part of it (Wan 3.0).

**Judge joins with the real clips.** When part of a join lives in the edit (a match-cut zoom, a dissolve, a water or steam layer), the raw clips can't show it. Render a short preview of the two shots around each join before the full cut, and compare the last frame of A with the first frame of B side by side: they should look almost the same.

**Image-first workflow:** the still for shot B should already show the carrier, with the new scene partly visible behind it. Example: the new location with out-of-focus papers falling across part of the frame. B's video prompt then clears the carrier: "the sheets keep falling past the lens and clear within the first second".

**Editing:** cut on the frame where A is fully covered, onto the matching frame in B. Generate a second or two of overlap on each side for flexibility.

**Check it:** run scene-cut detection. A hidden cut shouldn't register, while hard cuts will:
```bash
ffmpeg -i edit.mp4 -vf "select='gt(scene,0.3)',showinfo" -f null - 2>&1 | grep -oE "pts_time:[0-9.]+"
```

## 3. Generated bridge

- **First and last frame:** give the model still A and still B, and it invents the motion between them. Prompt the connecting motion, not just "transition": `continuous clockwise spin maintained throughout`, `the blue drains downward as pink rises from the bottom, camera static`. This is ideal for transformations and product reveals.
- **Match cut by shape** (a visible rhyme meant to be noticed): `Starting on [element in A], match cut to [same element in B], [shared shape, colour or motion] maintained throughout.` Example: a spinning coin becomes a chrome wheel rim.
- **Match on the smallest shared shape, at the same size and place.** A lens ring cut to a hose nozzle's rim felt like a jump; pushing into the eye's pupil and cutting to the nozzle's dark opening (dark circle to dark circle, brown iris to brass rim, both centred and equally wide) read as one movement. Generate the push into the small shape rather than zooming a 720p clip 6×, and let two frames dissolve at the cut.
- **Push into an object to enter its point of view.** A push-in that ends inside a camera's lens is a motivated cut to the view from inside that camera (going dark in the glass, the next shot opening from dark).
- **Last-frame handoff or extension:** use the last frame of A as the first frame of B (or the tool's extend feature) for one continuous camera move across locations.
- **Tool support differs and changes fast.** One survey (prompt-architects.com, Aug 2026) listed: Veo 3.1 with first and last frame plus extend; Seedance 2.5 with last-frame export and a mode that generates between two videos; LTX-2.5 accepting named edits ("hard cut", "match cut") in the prompt; Kling 3.0 with multi-shot syntax but no transition vocabulary. Support also differs by provider: Wan 3.0 via OpenRouter rejected a last frame in Oct 2026 ("does not support last_frame"). Check the current docs of the tool *and* the provider you use, and have a fallback (cut on action, or a cut point where the states match).
- Generate 3–5 variations of a bridge. When it fails, add constraints ("continuous motion, consistent lighting temperature") rather than removing them.

## 4. Motivated hard cut

A visible cut where motion carries the eye across it. This is the default for montage, and it matters more than any flashy wipe.

- **Cut on action:** A ends mid-gesture (turning, reaching, standing up) and B picks up the same gesture from a new angle or place. Generate both clips with the gesture in progress.
- **Exit and enter frame:** the subject leaves the frame (or B starts on an empty frame) and enters B. This allows a change of location, time or costume.
- **Smash cut:** an abrupt contrast, for comedy or shock (a loud scream, then lying on the floor).
- **Visible match cut:** a shape, colour or composition rhyme that the audience should notice.
- **Filled-frame entry:** B opens on a full-frame texture (a curtain, a wall of ice, liquid) that the subject then breaks through. It softens a hard cut.

**Cutting craft between AI clips:**
- **Keep screen direction.** Exit frame right means enter frame left. Reversing it reads as the subject turning around.
- **Change shot size by a clear step, or the angle by 30° or more.** Near-identical framings read as an accidental jump cut.
- **Stay on one side of the 180° line** between subjects.
- **Hold the colour temperature.** A shift is more visible than a framing change.
- **Copy the subject description word for word** between prompts so the character or product stays consistent.
- **Cut on the music's beat.** A beat hit or a whoosh makes any cut feel intended.

## 5. Edit-only

Fade in or out, dissolve, iris, graphic wipe, defocus, J/L cut (audio leads or trails the picture), sound bridge. Add these in the editor; don't prompt them. In a HyperFrames project they belong to `hyperframes-animation` (scene transitions). Dissolves signal time passing or a change of place; hard cuts signal immediacy.

## How many

Use hidden cuts and bridges as accents: 1–3 in a 30–40 s piece, at the moments that matter (the reveal, the location change, the payoff). A hidden cut on every shot becomes the point of the video, which suits a comedy showcase (below) but not a product story. Default to motivated hard cuts on the beat.

## Worked example: Eleven v4 spec ad

Burak Tuyan, Sep 2026, 44 s, x.com/buraktuyan/status/2106018840383717513. A character comedy that chains almost every type:

| Time | What happens | Type |
|---|---|---|
| 0–1 s | Extreme close-up of a laughing mouth; fast pull-back to a medium-wide of him in a gilded armchair reading papers | 1, pull-out reveal |
| ~3.3 s | He flings the papers at the camera; a sheet fills the frame. B opens in the Hall of Mirrors with papers still falling in front of his face | 2, object wipe with the carrier in both shots |
| 5.5 s | Wide-angle close-up, then a worm's-eye wide under the chandelier, then a crash-in to a screaming close-up | hard cut + 1, crash zoom |
| ~8 s | The scream dissolves into motion blur; he is lying face-down on the parquet (high angle) | blur cut, smash-cut contrast |
| ~12 s | He springs up toward the lens; his sleeve and body fill the frame with blur. B starts in matching blur whipping right and settles on him from behind on a balcony, arms spread | 2, body wipe + whip pan |
| 17.9 s | He turns around on the balcony; cut to a full-frame red curtain that he pushes through | 4, cut on action + filled-frame entry |
| 20.0 s | Curtain close-up, then a medium at a table with an apple and wine | plain hard cut on dialogue |
| 22.9 s | He reaches for the apple; cut to the apple thrust at the lens in another hall | 4, cut on action + object to lens |
| 26.2 s | Eating close-up, then an empty room; he rushes in from frame right already putting on a hat | 4, exit/enter frame, allows a costume change |
| 38.1 s | Hard cut to a white end card with the logo | hard cut |

Scene detection on this video flagged 5.5, 17.9, 20.0, 22.9, 26.2 and 38.1 s. It missed the paper (3.3 s), blur (8 s) and body-whip (12 s) joins: those are the truly hidden ones.

**Prompts for the paper wipe:**
- Shot A video: `He flings the stack of papers straight at the camera; sheets fly toward the lens and grow until one matte, out-of-focus sheet covers the entire frame. Camera static.`
- Shot B still: `Photoreal, 16:9, wide-angle close-up of [character] in [new location], staring into the lens; several matte, out-of-focus paper sheets falling in the foreground across the left half of the frame.`
- Shot B video: `The paper sheets keep falling past the lens from top to bottom and clear within the first second, revealing him staring into the camera. Camera static.`

**Prompts for the body wipe plus whip:**
- Shot A video: `He springs up from the floor straight toward the camera; his dark sleeve sweeps across the lens from left to right, filling the whole frame with motion blur. Handheld.`
- Shot B video (from a rear-view balcony still): `Starts in heavy motion blur as the camera whips from left to right, settling into a steady rear view of him on the balcony with arms spread.`

Sources: lumalabs.ai/news/ai-video-transition-prompts; prompt-architects.com/blog/322-transitions-in-ai-video-prompts; flashboards.yaroflasher.com/learn/editing/seamless-transitions; en.wikipedia.org/wiki/Film_transition; flixier.com/blog/exploring-the-basics-of-video-transitions-how-to-make-your-edits-seamless (edit-side basics).
