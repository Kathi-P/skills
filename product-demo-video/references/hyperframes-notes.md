# HyperFrames technical notes

Lessons from past runs of the product-demo-video skill (first from the Attest experiment). They are not universal rules.

How to use this file:
- Read it before building. Apply only the notes that match the current project.
- Do not test a note just to confirm it. Verify a version specific workaround when you actually need it (you hit the problem, or the composition uses the thing the note is about), against the installed HyperFrames docs or behaviour.
- When a note turns out to be outdated or wrong, update or delete it here instead of working around it in the skill.
- When you do verify a note, replace "version unknown" in its Last confirmed line with the real HyperFrames version.

Every note has the same fields: Applies, Workaround, Last confirmed.

## Setup

**Scaffold a new composition**
- Applies: a project with no HyperFrames composition yet (the skills install command is in the main skill).
- Workaround: `npx hyperframes init <dir>`.
- Last confirmed: Attest experiment, HyperFrames version unknown.

## Timeline

**Retuning the overall pace**
- Applies: the pace needs to change after the timeline is written. `tl.duration()` does not stretch a HyperFrames timeline.
- Workaround: author the timeline once, nest it in a master (`tl.paused(false); tl.timeScale(1 / K); master.add(tl, 0)`, register the master) and change K. This is a workaround that worked in the Attest experiment, not necessarily the method HyperFrames prefers. Check the installed HyperFrames docs for a built in way to scale or retime a composition first, and use that if it exists.
- Last confirmed: Attest experiment, HyperFrames version unknown.

**Initial states**
- Applies: compositions built on a GSAP timeline in HyperFrames.
- Workaround: set initial states with `gsap.set` outside the timeline, not `tl.set` at 0.
- Last confirmed: Attest experiment, HyperFrames version unknown.

**Loops**
- Applies: hero loops and any video whose last frame must meet the first. The requirement is in the skill's motion check; this is one way to meet it.
- Workaround: make every state a reversible tween (overlay opacity, typing from a progress counter) and reset the state while the camera is off it, so the last frame equals the first.
- Last confirmed: Attest experiment, HyperFrames version unknown.

## Lint and static checks

**Template literals in selectors**
- Applies: the composition builds `querySelector` strings with template literals and the HyperFrames static guard rejects them.
- Workaround: build the selector string by concatenation instead. If the guard accepts template literals in the installed version, delete this note.
- Last confirmed: Attest experiment, HyperFrames version unknown.

**Layout and contrast warnings inside a captured UI**
- Applies: layout or contrast checks flag elements inside a captured product UI, which is common with small text.
- Workaround: for each flagged element, review whether it is visible and meant to be readable in the final composition. Fix the ones that affect the viewer: a label the cursor touches, text in a lifted out element, anything the Readable rule in the main skill covers. If the warning concerns an element that is intentionally backgrounded, softened or never read, accept it and document the reason in the hand over. Do not accept warnings in bulk on the grounds that the camera zooms in later.
- Last confirmed: Attest experiment, HyperFrames version unknown.

**Design lint hooks (for example Impeccable)**
- Applies: such hooks are installed in the project.
- Workaround: fix the real tells they flag (a coloured side bar, a cream backdrop used as a default). Keep deliberate looks that suit the product or the destination (a radial glow, a tinted shadow, the product's own font, status outlines hugging text, focus rings) and record a narrow `ignore-value` with the reason. Say so in the hand over.
- Last confirmed: Attest experiment, HyperFrames version unknown.

## Markup and assets

**Whitespace in preformatted blocks**
- Applies: captured or authored markup using `white-space: pre`.
- Workaround: put no whitespace between the line `<div>`s, or the lines double space.
- Last confirmed: Attest experiment, HyperFrames version unknown.

**Brand fonts**
- Applies: the renderer cannot see the fonts the app loads on its own, and only bundled families resolve by name. If the fonts already resolve, skip this.
- Workaround: copy the font files into `assets/fonts` and declare `@font-face`, but only after checking the font's licence and whether it permits this use (embedding in a video, copying out of a package, a client's brand font or a paid family). If the licence does not clearly allow it, or you cannot tell, do not copy the files: ask the user, use a licensed or open fallback, or have the user supply files they are allowed to use. Keep copied files in the project and do not publish them with the video.
- Last confirmed: Attest experiment, HyperFrames version unknown.

**Stacked state layers**
- Applies: several captured states sit on top of each other (the React harness and local app methods in the skill's appendix).
- Workaround: mark the stacked state layers with the layout opt-out for occlusion. Look up the exact attribute in the installed HyperFrames docs before using it.
- Last confirmed: Attest experiment, HyperFrames version unknown.
