# Camera moves for AI video

The shot types set the composition. The move sets what happens to it over the clip. Video models follow one clearly worded move far more reliably than a stack of them.

## How to word a move

Make the camera the subject of the sentence. Give a direction, a speed and what the shot ends on:

`The camera slowly pushes in from a medium shot to a close-up of the glass over 5 seconds.`

- Speed words: *slow, steady, smooth, gentle* versus *fast, snap, whip, crash*. Leave speed out and you get a model-default medium drift.
- End point: "ending on the flag", "until the glass fills the frame". This stops the move from wandering.
- When nothing should move: `static camera, locked-off tripod, the frame stays perfectly still`. Positive wording describes the state you want instead of naming the thing you don't.
- Many tools offer camera-movement presets or controls. When one matches the move you want, use it instead of describing the move in words, and keep the words for the subject's action.

## Moves

| Move | What it does | Wording |
|---|---|---|
| Static / locked-off | Calm; puts all attention on the action in frame | `static camera, locked-off tripod` |
| Push-in (dolly in) | Focus, tension, "look at this" | `camera slowly pushes in toward [subject]` |
| Pull-out (dolly out) | Reveals the context; good for endings | `camera slowly pulls back to reveal [scene]` |
| Truck / track | Moves sideways past the subject; creates parallax with the foreground | `camera tracks sideways left to right past [foreground] keeping [subject] centred` |
| Follow / lead | Moves with a walking subject, behind or in front | `camera follows behind [subject] at walking pace` |
| Pan | Turns left or right from a fixed spot; surveys a scene, reveals | `camera pans slowly right from [A] to [B]` |
| Tilt | Turns up or down from a fixed spot; shows scale, reveals height | `camera tilts up from [base] to [top]` |
| Orbit / arc | Circles the subject; showcases a product | `camera slowly arcs 90 degrees around [subject]` |
| Crane / pedestal | Moves straight up or down; reveals the scene from below or above | `camera rises from table height to above the glass` |
| Drone / FPV | Flies over, through or into the scene; opener energy | `drone flies forward over [location] toward [subject]` |
| Handheld | Documentary feel, user-generated, party energy | `handheld camera with subtle natural shake` |
| Whip pan | Very fast pan with blur; a transition between shots | `fast whip pan to the right with motion blur` |
| Rack focus | Shifts focus from near to far or back; redirects attention. Unreliable (see below) | `focus shifts from [near object] to [far subject]` |
| Crash zoom | Sudden zoom; comedy, punch, beat hits | `sudden fast zoom in on [subject]` |
| Roll | Camera rotates around the lens axis; disorientation, transition | `camera slowly rolls 20 degrees clockwise` |
| Slow motion / speed ramp | Liquids, impacts, the money moment | `in slow motion` / `speed ramps from normal to slow motion as [event]` |

## Which moves suit which shots

| Shot | Moves that suit it |
|---|---|
| Wide, aerial | slow push-in, drone forward, pull-out reveal |
| Medium, three-quarter | slow arc, truck, static |
| Close-up, macro | static, very slow push, rack focus, slow motion |
| Low-angle, worm's-eye | tilt up, slow push-in, crane up |
| High-angle, overhead | slow rotation, crane down, static with hands entering |
| Profile | track alongside |
| Over-the-shoulder | push past the shoulder, rack focus |
| POV, selfie | handheld |
| Dutch, fisheye | handheld, roll, fast follow |
| Foreground occlusion | truck for parallax, push through the foreground |
| Foreground / background focus | rack focus between the two |
| Silhouette | static or slow push, light change |
| Specials (prism, magnifier, inside-a-hole, fridge) | static or one slight move; the effect is the motion |
| Talking single, reaction | static, or a very slow push |

**In vertical 9:16**, prefer moves along the lens axis or up and down (push, pull, tilt, pedestal, crane). Trucks, pans and orbits show little width and push the subject out of the narrow frame.

## What models still do badly

- **Several moves at once** (orbit plus crane plus zoom): pick one.
- **Dolly zoom (vertigo effect)**: rarely comes out right. Fake it in post or skip it.
- **Rack focus**: often the focus doesn't shift, or faces drift while it tries. When the shift must land, make two stills (near sharp, far sharp) and cut between them.
- **Face-safe order of moves**, from safest to riskiest for faces: locked → slow push-in → slow pull-back → tilt or pedestal → slow sideways truck → arc or orbit. Observed in Wan 3.0 (Sep 2026); a sensible default for other models until tested.
- **Precise 360° orbits**: the background and any text on the back of the object get invented. Use 45–90° arcs.
- **Long continuous takes**: quality drops after a few seconds. Cut instead.
- **Fast moves with fine detail**: text, logos and faces tear. Slow down, or let the edit provide the speed (cut on the beat) rather than the camera.
- **Moving to an angle the still doesn't show** in image-to-video: the model has to invent the unseen side. Generate a new still for the new angle instead.
