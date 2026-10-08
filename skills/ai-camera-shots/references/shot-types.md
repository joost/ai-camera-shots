# Shot types (34)

The list of 34 shot types follows "34 shot types every AI filmmaker should know" by Rourke Heath / GenHQ (https://x.com/rourke_heath/status/2104501759674577301, Sep 2026, inspired by @byemmasvision) and its companion PDF "GenHQ x Magnific 34 Shot Prompt Guide"; see the guide for its original example prompts. The **Any subject** lines are templates for people, products, food, drinks and objects. The **Video** lines are notes for image-to-video.

Contents: [Prompt pattern](#prompt-pattern) · [Distance](#distance) · [Height and tilt](#height-and-tilt) · [Facing](#facing) · [Lens](#lens) · [Focus and light](#focus-and-light) · [Specials](#specials)

## Prompt pattern

The prompts in that guide share one short structure, about 25–35 words, and it works well in general:

```
<style>, <aspect ratio>, <shot + where the camera is>. <what to show or exaggerate>; <light>, <background or focus>.
```

Example: `Photoreal, 16:9, low-angle close-up on a 35mm lens, camera resting on the marble café table and looking up at a tall iced latte. Make the glass feel monumental; morning window light behind it, the café softly blurred.`

Two lessons from that guide:
- **Each prompt says what the shot should do to the subject**, not just its name: "make the figure feel tall", "exaggerate the nose", "flat, graphic framing". The model needs the effect as well as the label.
- **Each one names a visual cue that proves the angle**: "feet in frame", "court lines strongly curved", "horizon runs diagonally", "an oversized sole fills the foreground". When a model ignores an angle, add the cue that only that angle would produce.

For a product brief, add your subject block (materials, brand details, colours) after the shot sentence and keep the shot sentence first.

The templates assume 16:9. For vertical, write `9:16` and check the cue still fits a tall frame: wides need height cues (sky, ceiling, vault above) instead of width cues, and a profile or two people side by side has little room (see Vertical 9:16 in `SKILL.md`).

## Distance

**1 Wide**: establishes place and scale; the subject is small in its environment.
- Any subject: `wide shot, [subject] small in the frame with space all around, [environment] dominant, [base of subject] fully in frame`
- Video: suits a slow push-in, a pull-out reveal or a drone move. Faces and labels smear at this distance.

**2 Medium**: the workhorse; waist-up for people, the object plus its immediate surroundings for products.
- Any subject: `medium shot of [subject] with [nearby context] in frame, natural proportions, background gently blurred`
- Video: good for hand actions and conversation. Use it as the neutral shot between extremes.

**3 Close-up**: emotion, detail, the hero moment.
- Any subject: `tight close-up of [subject] filling the frame from [top edge] to [bottom edge], focus on [key detail], [surface texture] visible, background soft`
- Video: tolerates subtle motion well. Keep the camera nearly still.

**4 Macro**: detail beyond what the eye sees (texture, bubbles, droplets, fibres).
- Any subject: `extreme macro of [tiny detail], filling the frame with [textures], crisp [focal point], soft falloff at the edges, 100mm macro lens`
- Video: small movements look huge, so use slow motion and a very slow push or rack focus. The best way to show liquids, fizz and condensation.

## Height and tilt

**12 Eye-level**: neutral and honest; the default, so use it on purpose.
- Any subject: `camera exactly at [subject]'s height, level horizon, straight-on view`
- Video: pairs with a truck (sideways move) or a static shot. It reads as calm.

**13 Low-angle**: power, scale, heroism.
- Any subject: `low-angle view from below [subject] looking up, [subject] feels tall and monumental, [background] rising behind against [sky or ceiling]`
- Video: tilt up, slow push-in or crane up.

**14 High-angle**: makes the subject small or vulnerable, or shows a layout.
- Any subject: `high-angle view looking down at [subject] on [surface], [surface] visible around it, natural perspective`
- Video: slow crane down or push-in.

**15 Dutch angle**: unease, energy, chaos, party.
- Any subject: `Dutch angle, camera tilted about 25 degrees so [straight lines in scene] run diagonally, [subject] sharp`
- Video: models tend to level the horizon mid-clip, so restate "tilted horizon" in the video prompt. Pairs with handheld or a camera roll.

**16 Overhead**: flat, graphic, flat-lay; shows patterns and arrangements.
- Any subject: `camera directly overhead looking straight down at [subject] on [surface], flat graphic framing, [lines or pattern of surface] clear`
- Video: slow rotation, crane down, or a static shot with hands entering the frame.

**17 Aerial**: location and scale; drone view.
- Any subject: `high oblique aerial over [location], [subject] tiny within it, [landmarks] visible`
- Video: drone flies forward, orbits or rises. A good opener.

**18 Ground-level**: puts the viewer in the scene; foreground objects loom.
- Any subject: `camera resting on [surface] just above it, facing [subject]; [surface texture or nearby objects] large and close to the lens, [subject] rising higher in the frame`
- Video: slow push along the surface. Very effective for anything on a table or bar.

**19 Worm's-eye view**: extreme low angle looking steeply up; monumental.
- Any subject: `worm's-eye view from directly beneath or beside [subject], looking steeply up; [nearest part] oversized in the foreground, [rest of subject] and [sky or ceiling] above`
- Video: tilt up or a static shot. Through-glass versions (looking up through the bottom of a glass) need image-first.

## Facing

**6 Profile**: contemplative, clean outline, graphic.
- Any subject: `side-on profile of [subject], clean outline against [background], light raking across from one side`
- Video: track sideways alongside the subject. For a glass, a profile shows the liquid level and colour layers best.

**7 Three-quarter**: the flattering default; shows depth and two sides.
- Any subject: `three-quarter view, [subject] turned about 45 degrees from camera, front and one side visible`
- Video: a slow arc around the subject from three-quarter to front works well for product reveals.

**8 Rear**: mystery, following; the viewer sees what the subject sees.
- Any subject: `rear view from behind [subject], facing toward [what they look at], [subject's front] hidden`
- Video: follow from behind, or push past the subject toward what they look at.

**9 Over-the-shoulder**: relationships, conversation, "someone is about to take this".
- Any subject: `over-the-shoulder view past [person A] in the soft near foreground, [person B or object] sharp in focus`
- Video: a slow push past the shoulder, or a rack focus from the shoulder to the subject.

**10 POV**: first person; the viewer is the character.
- Any subject: `first-person POV, viewer's own hands holding [object] at the bottom of frame, looking at [scene] ahead`
- Video: handheld. Hands are a weak point, so keep hand motion minimal and simple.

**27 Selfie**: user-generated feel, authenticity, social.
- Any subject: `handheld selfie at arm's length, one arm leading toward the camera, slight wide-lens distortion, [subjects] and [setting] behind`
- Video: handheld micro-shake. Shoot it vertical (9:16) if it should feel native to a phone.

## Lens

**22 Wide-angle close-up**: close but wide; exaggerated perspective with the setting still visible; energetic.
- Any subject: `wide-angle close-up, 24mm look, camera very close to [subject], near parts slightly enlarged, [setting] visible around it`
- Video: a fast push-in or handheld. Great for party energy.

**23 Fisheye**: playful, skate or music-video look.
- Any subject: `fisheye lens, [subject] centred, [straight lines] strongly curved near the edges, centre undistorted`
- Video: handheld, fast follow or FPV. Restate "fisheye distortion" in the video prompt.

**24 Fisheye close-up**: comedic and bulging; the subject almost touches the lens.
- Any subject: `extreme fisheye close-up, [subject] almost touching the lens, [nearest part] exaggerated, background strongly bowed`
- Video: short, punchy shots only.

**5 Overhead fisheye**: a top-down circular world; graphic and surreal.
- Any subject: `overhead fisheye looking straight down at [subject] on [surface], [lines on surface] strongly curved around it`
- Video: slow rotation. Works well for a table full of glasses or a crowd from above.

**25 High-angle close-up**: looking down into the subject; vulnerable, or "looking into the glass".
- Any subject: `close-up from just above [subject], looking down into [it or its opening], [top surface] emphasised, dark soft background`
- Video: a slow push down. For drinks it shows the surface, ice and fizz.

**26 Low-angle close-up**: a heroic detail; jaw, chin or the base of an object.
- Any subject: `tight close-up from below [subject], looking up, [base or underside] emphasised in strong perspective, soft light, blurred background`
- Video: a slow push-in or tilt up. A hero shot for bottles and glasses.

## Focus and light

**29 Foreground occlusion**: shooting past something blurred; voyeuristic, gives depth.
- Any subject: `[subject] partly hidden behind out-of-focus [foreground objects] across the [edge] of the frame, visible part crisp`
- Video: a sideways truck creates parallax, or push through the foreground to reveal.

**30 Foreground focus**: near object sharp, far subject blurred.
- Any subject: `shallow depth of field, [near object] sharp at the edge of the frame, [far subject] heavily out of focus behind`
- Video: rack focus to the background (this shot becomes shot 31). Racks are unreliable; when the shift must land, generate 30 and 31 as two stills and cut.

**31 Background focus**: near object blurred, focus on what lies behind.
- Any subject: `[near object] close to camera and heavily out of focus, sharp focus on [scene] behind`
- Video: rack focus to the foreground (this shot becomes shot 30). Same caveat as 30.

**28 Silhouette**: mystery and graphic shape; hides identity.
- Any subject: `silhouette of [subject] against bright [backlight], subject very dark, clean outline of [defining shapes]`
- Video: static, or a slow push. A light change can reveal the subject.

## Specials

Use at most one per shot. They work best image-first: generate several stills, pick one, then animate it.

**11 Prism reflection**: dreamy, split and repeated image.
- Any subject: `shot through a glass prism held near the lens, part of [subject] split and repeated in soft reflections, [key detail] stays clear`
- Video: slow drift. Models struggle to keep the refraction consistent.

**32 Lens flare**: warmth, sun, a cinematic glow.
- Any subject: `warm backlit close-up, [light source] striking the lens, bright flare and subtle streaks across one side of [subject]`
- Video: a slow sideways move makes the flare sweep. Name the light source so the flare has a reason to exist.

**33 Magnifying glass**: curiosity, inspection, comedy.
- Any subject: `close-up through a magnifying glass held over [detail], only [detail] inside the lens enlarged and distorted, rim and surroundings normal`
- Video: a slow move of the glass across the subject. Distortion consistency breaks easily, so keep it short.

**20 Inside a hole**: an object's-eye view from below; surprising.
- Any subject: `camera at the bottom of [container or hole] looking up at [subject] peering in, [rim material] framing the edges, bright [sky or ceiling] around them`
- Video: static or a slight push up. For drinks: from inside the glass or ice bucket looking up.

**21 Hoop-level**: camera mounted on an object at its natural height, looking at the action.
- Any subject: `camera at [object]'s height, looking down through [object's opening or frame] at [subject] below, wide fisheye curve, strong depth`
- Video: static with the subject moving toward the camera.

**34 Inside-the-fridge**: the camera lives inside a container; the classic drink or food POV.
- Any subject: `POV from inside [fridge, cooler, locker, bag] as [subject] opens it and reaches in, [contents] framing the foreground, cool inside light meeting warm outside light`
- Video: the door opens and light floods in, then the hand reaches in. Keep the reach simple.
