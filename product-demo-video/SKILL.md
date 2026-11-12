---
name: "product-demo-video"
description: "Use when someone wants a product demo, product film, hero loop or motion video for a SaaS or web product, built from the project's real UI, design system and content and rendered with HyperFrames."
---

# Product demo video

Short product films made from real interface, built as HTML with HyperFrames and rendered to MP4. Used for LinkedIn, YouTube B-roll, landing page heroes and client launch videos.

The target is the feel of product feature videos from Figma, Payload, Linear and Vercel, not a screen recording with captions. A screen recording shows the product. A product film stages it, and above all it moves smoothly.

HyperFrames has its own skills for the technical side (composition format, GSAP timing, lint, preview, render). Install them if missing with `npx skills add heygen-com/hyperframes -y` and follow them for anything about how to render. Lessons from past runs that depend on the HyperFrames version or on a product's build are in `references/hyperframes-notes.md`. Read it before building and apply only the notes that match the current project. Verify a version specific workaround when you actually need it, and update or remove outdated notes when you meet them. This skill decides what the video says, what it looks like and how it moves.

The order is fixed: gather context, interview, video brief, shot list, build. Never start drafting a video brief or a shot list before the interview is done.

Two kinds of rules are kept apart on purpose. Section 1 holds the requirements that apply to every product. Section 6 holds the default style, the look this skill reaches for first: a floating window on a backdrop, lifted out elements, camera pushes. The default style is a starting point. The brand, the destination, the references or the user can change any of it, and when a video departs from it, say so in the video brief and choose the alternative on purpose.

## 1. Always

These hold whatever the style. Each lives here once; the later sections and the checks point back to it.

- **Real interface.** Every state shown is captured from the product's real rendering (section 2 and the appendix), never rebuilt by hand from code or memory and never invented. Steps, counts, labels, hints and layouts match the product as it ships today.
- **Honest.** Show only what the product really does or will do, with no invented capabilities. A video may show part of a flow: one segment, one feature, one moment. It may not imply that the skipped steps or features do not exist (a checkout with no discount field, an editor with no undo). When a feature is optional or off by default, show it the way the product shows it, with its labels and warnings. Note in the shot list what was left out and why.
- **Believable content.** Real looking names, numbers, dates and states, never lorem ipsum or round placeholder values, and never labels like "Sample", "Test" or "Demo" inside the UI. Show empty, filling and done states, because a UI that is only ever full looks fake. Check each state against how the product renders it on the page (a screenshot or the person's word), not against component code. Prefer the original content over an empty state message when that is what the page does.
- **Readable.** Everything the viewer must read is readable at phone size. If it is too small as a thumbnail, lift it out as its own element or remove it. Simplify captured text only when a fully real screen is too busy: keep real words on what the story is about, let the surrounding text become soft placeholder bars, keep real anything the cursor touches, and never blur out the labels that make a flow honest.
- **Smooth.** Nothing pops, cuts or stalls. Everything travels on eased paths in one consistent family (section 7).
- **Time to read.** Hold times come from the time budget in section 9. If the budget does not fit the place, cut content, never reading time.
- **One message, works muted.** One message per video, carried by the UI and any staged text without sound. Most people watch muted.
- **A film, not a recording.** The staged feel comes from camera, lifted out elements and a deliberate frame. Section 6 gives the default way to get there.

## 2. Gather context

The video should look and read like the actual product. Collect what already exists before asking the user anything, so the questions are specific and nothing is asked that the project already answers. Look in the repo, any project notes or docs and any attached files.

Design system
- `frame.md` if present: this is HyperFrames' design system file, use it as is
- Tailwind config, `globals.css`, token files, CSS variables: colours, type, radius, spacing, shadows
- Fonts and how they are loaded
- If there is no `frame.md`, write one from these tokens so every composition shares it

Components
- UI library folders (`components/ui`, shadcn, Storybook stories), dashboard screens, cards, tables, buttons, inputs
- HyperFrames works with plain HTML. Capture the real rendered markup of every state you will show, using the methods in the appendix at the end: a React harness, a locally running app, a public site, and what to do when the product cannot be rendered. A hand rebuild drifts from the product (wrong step counts, missing hints, different layouts)
- Prefer markup to screenshots: markup stays sharp at any zoom and can be animated piece by piece. When the product cannot be rendered (a native or third party app, a tool behind a login you cannot use), ask the user for the screens, say so in the video brief and keep camera pushes modest so the pixels hold

Product and brand
- README, landing page copy, CMS content, docs, pricing, changelog
- Logo as SVG, favicon, brand colours
- The real feature names and the real wording the product uses

Earlier videos in this project
- Look for a saved video brief from a previous video (see section 4). Reuse its decisions, such as backdrop, host site and look references, instead of asking again

If there is no repo, ask for the website URL and use HyperFrames' website capture skill as the starting point.

Summarise what was found in a few lines and say what is missing.

Where the video will live
- If it goes on a page (landing page, site, docs), open that page (its code in the repo, or the live URL) before the interview. Note its background, primary colour, fonts, tone and headline pitch. The video's backdrop, type and message must fit that page, and when they differ from the product's own look (a marketing site can use another palette and fonts than the app), say so and let the user decide which wins.

## 3. Interview

Ask before drafting. Use the question tool if one is available, otherwise ask in plain text. Ask up to 4 questions in one round and run at most two rounds. Build the options from what section 2 found (real feature names, real audiences) and put a recommended option first where there is a clear one. Skip any question that the user's messages, the conversation so far or the project already answers. If an answer is open ended, ask one follow up in plain text; a plain text follow up does not count as a round. Questions 3 to 5 are asked only when they apply, and if more than four questions apply in total, the rest go in the second round.

Always settle, but only ask what is still open. Purpose and main message (questions 1 and 2) must be established before the video brief. If the user's messages, the conversation, the project or a saved video brief already establish one of them, do not ask it again: state it back in one line as an assumption and let the brief confirmation correct it. If only half is known, ask only the missing half.

1. **Purpose and place.** Where will this video live and what should it lead to? Examples: LinkedIn post to show skill and win clients, hero loop on a landing page, YouTube B-roll, launch video for a client, sales follow up. The place decides length, format, sound and how much explaining is needed, and what should happen next (book a call, try it, remember the studio, simply get it) sets the last shot.
2. **Main message.** After watching, what is the one thing the viewer should understand or feel? Offer 2 or 3 candidate messages drawn from the product's real features and copy. If nothing in the project suggests one, ask for it directly. A video with two messages has none.

Ask only when it applies:

3. **Host site.** Only when the product works on top of a website or app (see section 5). Which site should it run on? Offer: the project's own design system or landing page design system if one exists (recommended), one of the user's own sites, or an invented brand built from real references. Real client sites are off limits unless the user says otherwise.
4. **Backdrop.** It depends on where the video goes, so decide it against the destination. For a page, look at the page first, then offer 2 or 3 options that fit it (matching its background, a contrasting brand tint, light or dark, a photo, a texture), recommended one first. Be creative: nothing is banned. Cream, off-white, blobs or gradients are fine when they fit the destination and are chosen on purpose, and only generic when they are a default.
5. **Look references.** Only when none have been shared in the conversation. Ask for 1 to 3 product videos whose feel the user wants, as frame stills or links, and what they like about each. The answer is mostly about composition and motion feel. Colour and type come from the product unless the user says otherwise. If none are given, use the default style and motion rules in sections 6 and 7 and say so, so the user can correct them.

Do not ask as questions:

- **Audience.** It follows from the place. State the assumption in the video brief and let the user correct it there.
- **Constraints.** Ask at the video brief confirmation instead (see section 4).

If the user does not know the message, propose one based on the product and ask them to react to it. That is faster than a blank question.

## 4. Video brief

After the interview, write a video brief of five lines or fewer: message in one sentence, audience (as assumed from the place), place and format, length, closing action, and the host site if there is one. If the product does not suit the default composition (section 6), add one line naming the composition and why. The length decides the scope: a 5 to 10 s loop shows one feature or one moment, 15 to 30 s one flow with a result, and only longer pieces cover several things. If the message needs more than the length allows, change the message or the length in the brief, before any shot list.

If references were given, add a reference breakdown of up to six lines before the shot list, covering the composition, how the backdrop behaves, the camera moves, the cursor and the use of type that the stills actually show. Describe only what is visible in the stills, never guess at motion or at things not shown, and say which parts are unknown. Do not carry over a reference's colours, fonts or textures unless the user asks.

Confirm the video brief and breakdown with the user before writing the shot list. At the same time ask once whether anything must be shown or avoided, what feel they want (calm, snappy, playful or technical, default calm) and whether the video has sound. Write every assumption into the video brief itself (audience, feel, any invented business or data), so one reply can correct them. If they confirm without answering, carry on with those defaults and list them in one line. If something the user said contradicts the default style or the story guidance (sections 6 to 8), say so once and let them decide.

Once the video brief is confirmed, save it in the project next to the composition (for example as `video-brief.md`), including the backdrop, host site and look references. The next video in this project can then start from it.

## 5. The host site

Some products work on top of a website or app: translation and localisation overlays, CMS and visual editors, analytics, feedback and review tools, chat widgets, cookie tools. For these, the host site is part of the picture, and if it looks fake the whole video looks fake. A generic invented site made of flat illustrations and placeholder blocks reads as a template and undermines the product on top of it.

Do not invent a site from nothing. The quality bar is fixed: the host site must pass as a real, art directed site in a one second glance. The quantities below are guidelines, not minimums. Scale the host site to what the product touches: a product that acts on one section or component can sit on a single carefully designed section, and that is often more convincing than a thin full page. Build it like a real project:

- **Start from a real design system.** Use the project's design system or landing page design system, or the user's own site, as the base for tokens, components and layout. If there is none, capture two or three real sites in the same category with the website capture skill and borrow structure, spacing and type scale, then invent the brand name, copy and imagery so nothing is recognisable as a real company
- **Real photography, not flat illustration.** Use real photos for products, people and places, from the project's assets or a photo source such as Unsplash. Vector icons and illustrated products make a site look like a mockup
- **Art directed, not generic.** The demo content has its own personality: a considered type pairing, characterful details, imagery chosen with care. A neutral admin grey demo reads as filler
- **Page depth.** When the product works across a whole page, a real page has an announcement bar, a header with logo, search and cart, a hero with a specific headline and a real image, a varied product or content grid, social proof such as reviews or press, and a footer. Show the part of the page with the most real content. When the product works on one section, build that section to the same standard and skip the rest
- **Variety and specifics.** Different products, believable names and prices, copy that sounds like the brand. No repeated identical tiles, no generic taglines
- **Readable scale.** Inside the product window, give the host site most of the width (about 60 percent is a good starting point) and keep its text legible at phone size
- **Restrained overlays.** Product overlays such as outlines, highlights and badges go on the few elements in focus. If every element carries an outline the site reads like a wireframe or debug view
- **Enough content to be believable.** For a full page, aim for five or more varied real photos and the sections listed under page depth. A sparse page with two photos reads as a mockup, so either give it that depth or narrow the shot to one section that is complete in itself. Say early that the host site is the weakest part of any demo like this and offer the product's own site, or a rebuild of a captured real site with invented names, as alternatives
- **Intentional states.** Pending, empty or unfinished states must look like designed UI, not like broken or disabled content

## 6. Default style

This is the house look, chosen to get the film feel. Colour, typeface, texture, corner radius and cursor style come from the brand or the product, or from references only when the user names them. Stills show composition and framing but cannot show motion, so smoothness is set by section 7 and checked in the render. Everything below can be overridden (see the start of this skill).

Composition
- **Centred anchor.** The product window sits centred, floating with margin, with rounded corners and a soft shadow. When the video carries on-screen copy, the window sits right of centre and a text column on the left stays clear in every camera position, including pushes. The window is the product's UI itself: a rounded, softly shadowed panel with no browser or OS chrome (no traffic-light dots, no URL bar), unless the product is a desktop app, the product lives on a web page that has to read as a website, or the user asks for a frame
- **Alternatives, chosen when the product asks for them.**
  - *Bleed crop:* the window is cropped by one or two edges of the frame and runs off them, with the backdrop still visible on the others, so it reads as a crop of a larger product. Use it when the whole window would be too small to read at the size the video is seen (a wide table, a hero loop on a phone)
  - *Elements only:* no window, a few lifted out elements on the backdrop. Use it for a single component, a widget or an overlay
  - *Device frame:* a phone or desktop frame for native or mobile products
  - Anything else the product needs, named in the video brief. Whatever the composition, it should read as staged, with deliberate framing and camera or lifted out elements. The one thing to avoid is a raw edge to edge screen recording
- **Separate elements.** Some UI elements are separate from the window: lifted out and shown larger beside or in front of it, with the window still visible but softened behind, or placed alone on the backdrop. These are the details the viewer should read. A lifted out element can also be a small stack: two components at the same width with a small gap, such as a card and the menu it opens
- **Zoom in parts.** The camera pushes into one part of the window. The crop is deliberate and a little of the backdrop stays visible at the edge, so it reads as camera and never as a mistake
- **Backdrop.** By default something sits behind the UI in every scene: a gradient, a colour field or a texture built from the brand (a faint pattern of lines, tiles or grain in a tone of the brand colour works well), or a photo, light or dark. Never an unconsidered bare white or black void. It is taken from the brand, the destination page or the person's answer, and checked against where the video will sit
- **One idea per scene.** One element, one action, one change. If a scene needs two, split it
- **Same element returns.** An element seen in the window is later seen lifted out, so the viewer knows where it came from

Text
- The UI carries the story. No caption strip under the video
- Default to no staged text and no title card. On a landing page or any page that already carries words, show the product alone: window, lifted out elements, cursor and camera, with nothing beside it. Add on-screen lines or an opening or closing card only when the place needs them (for example a muted LinkedIn or social post that must carry its message by itself) or the user asks. A card must say something specific to this product, never a generic tagline
- When on-screen lines are used: 3 to 5 short second-person benefit lines, one per beat, large enough for a phone, in the destination page's heading font; never a made-up person, and never a claim the product cannot back up
- Staged headline type is for what the UI cannot say. It is set in the brand or product font, placed inside the scene with real margin, one short line at a time, and it animates in with the same easing family as everything else
- State changes are animated inside the UI itself: text typing in, strikethroughs drawing, chips and statuses appearing

Camera
- 2D by default: push in, pan, scale, lift out. Add 3D tilt or parallax only if the references show it or the user asks

## 7. Motion

Smoothness is the priority. This section is the one place for it; the checks in section 11 point here.

Purpose
- Every move does a job: explain, direct attention, show a change. No decorative loops
- Add only what does a job. Everything added to the UI must either exist in the product or help the viewer: direct attention, show what changed or explain a connection. Camera moves, lift outs, dimming what is not in focus and a single callout are fine. Highlight sweeps, shimmer, glows and badges for features the product does not have read as fake. Test: if you removed it, would the viewer miss where to look or what happened? If not, cut it. Most of the energy comes from the interaction itself: the cursor, the typing, the selections, an element lifting out, the result travelling to where it lands. Products with little interaction (dashboards, analytics, admin views) get their energy from data moving: numbers counting, rows arriving, a chart drawing, a result travelling
- One focus at a time. Soften or blur what is not the subject
- Stop early

Flow
- **Everything is connected.** Elements travel from where they live to where they are shown, they do not pop in or cut. A lifted out element scales and moves out of the window along a continuous path
- **The camera flows.** A push in continues into the next framing without a hard cut. Avoid cutting to a different flat scene. If a cut is unavoidable, hide it behind a movement or a match on the same element
- **Every camera move needs a reason:** the card grew, a detail must be read, something travels to another place. Never re-frame for each step. Start from one fixed framing and add a move only when something would otherwise be unreadable. A narrow, tall UI in a 16:9 frame is best shown with at most one ease out while it is tall and one ease back in when it is short. Count the moves in the shot list and justify each one
- **Overlap the moves.** The next move starts while the previous one is still settling, so nothing stops dead between beats. Then give the key result a real hold

Timing
- **One easing family.** Use smooth curves throughout, for example GSAP `power3.inOut` for camera and layout moves and `expo.out` or `power3.out` for arrivals. Never linear. A slight overshoot is allowed on small elements only
- **Durations.** Most moves take 0.6 to 1.2 seconds, small UI feedback 0.2 to 0.4 seconds. Avoid anything faster than 0.2 seconds unless it is a click response
- **Consistent.** Similar moves use the same duration and easing across the whole video, so it feels like one hand made it. That includes one palette, one type system and one cursor style
- **Stagger.** Items in a group arrive 40 to 80 ms apart

Cursor
- For mouse driven products (touch products get a tap marker, keyboard driven ones show the keys). It moves on a smooth curve with easing, never in straight robotic lines. It leads the eye to the next click and is styled to match the product
- Scale it so it is clearly visible at phone size and survives downscaling, at a constant size on screen whatever the camera scale. Place it by its tip: the arrow tip lands exactly on the target
- A click is shown by the UI responding, and the click itself must be readable: a short hold before the click, a dip of the cursor, a ripple, the target pressing in, and focus rings before text is typed into a field. The app then swaps state at once, a beat later, as a real app does, and never as a slow crossfade between two layouts

Output
- Final export at 60 fps if the platform allows it, otherwise 30 fps, and keep it consistent. Draft renders in section 11 may be lower quality
- Use sub pixel positioning and transforms, never top and left changes, to avoid jitter. Add light motion blur on fast moves if the engine supports it

## 8. Story and length

Story
- One message, one outcome. The strongest demos pick the single most important thing the product does and make the viewer feel it. A feature tour fails
- Frame around the outcome for the user, not the product's internal structure. Show the problem state, the action, the result
- Show the magic moment early. The first 2 to 5 seconds already show the product doing its thing. No logo splash, no warm up
- End on the result and one clear next step, not on a feature list
- Match craft to product. The polish of the demo is read as the polish of the product

Length by place
- Hero loop or ambient background: 5 to 10 seconds, no sound, the last frame meets the first
- LinkedIn or Shorts: 15 to 30 seconds, one message
- Landing page explainer: 45 to 90 seconds
- The ranges say how much a place can carry. Holds still come from the time budget in section 9
- Never longer than the message needs. Cut anything that repeats a point

## 9. Shot list

Time budget first. Before writing shots, list the real UI steps the video must show and give each the time a first time viewer needs to read it: usually 1.5 to 2 s on screen, each cursor move at least 0.6 s, and any text a hold of about 0.5 s plus 0.3 s per word. Starting points for holds: a code or data card about 3 s, a record or result about 2 s, typing at most 2.5 s, an end screen 2.5 s after the last element lands. Fast products (a command palette, a keyboard shortcut) can run tighter. Add the transitions and the result. That sum is the real length.

Before storyboarding, also list every action in the real flow (each button, each optional feature such as an approval step or an import option, each limit) from the UI code and the docs, and take the steps, counts and labels from the captured rendering, not from the code or from memory. This is the list the honest partial flow in section 1 is checked against.

If the sum is longer than the range for the place, cut by scoping: show one feature, one moment or one segment of the flow, or fewer states. A shortened flow stays accurate and does not imply the missing parts are absent; say in the shot list what was left out. Never compress the moves or the reading time, and never stretch the length to fit a flow that is too big. If the message needs the longer length, say so in the video brief and let the user decide. When someone says the video feels too fast, add time to the holds, not to the story.

Write the video as a list of shots with timing. Each shot names the move and the one idea, and says why it is there. If a shot has no reason, cut it. Check that the first shot lands the hook and the last shot lands the closing action from the video brief. For each transition, say how it flows into the next shot, usually by the same element continuing or travelling.

Shot vocabulary
- **Context**: the full window centred and floating on the backdrop
- **Lift out**: an element travels out of the window and settles larger, window softened behind it
- **Push in**: the camera moves into one part of the window, cropping on purpose with backdrop at the edge
- **Cursor flow**: a cursor completes the core task, clicks and inputs visibly change state
- **State change**: one element morphs through states (empty, filling, done)
- **Stack build**: the first element arrives alone and holds the focus, then moves up or aside as the next one opens, and the focus moves to it. The relationship animates, not only the new element
- **Match cut**: an element in one scene becomes the subject of the next
- **Data in motion**: numbers count, rows appear, a chart draws, something travels between systems
- **Resolve**: everything settles back to the window and one closing line or logo

## 10. Formats

- LinkedIn: 1:1 or 4:5
- Shorts and Reels: 9:16
- YouTube B-roll, landing pages and client launch videos: 16:9
- Separate lifted out elements adapt easily to any format. The window layout needs its own framing per format

## 11. Build, check, export

Follow the HyperFrames skills for composition, lint and preview, and `references/hyperframes-notes.md` for version specific lessons. The word render means one of three things here, and only these:

1. **Stills.** Before animating anything, render a still of every scene at full size and at phone size. Show the first one to the user for a look check, with the top two backdrop options if the backdrop is still open.
2. **Draft render.** Internal. The fastest quality the engine offers, run as often as needed and not sent as a deliverable. It is where the motion checks happen.
3. **Final export.** The 60 fps (or 30 fps) MP4 from section 7. Run it once, after the user has approved the draft, then send it with a one line note on what it shows. If the user has said to deliver without review, skip the wait.

Composition check on the stills:

- Would the host site and the UI pass as real in a one second glance?
- Does the composition match the video brief (the default floating window with a backdrop behind it, or the named alternative)?
- Are crops deliberate, with backdrop visible at the edge where the composition calls for it, and nothing cut by accident?
- Does each scene carry exactly one idea?
- Do all scenes share one palette, one type system and one cursor style, all taken from the brand or product?
- Does it look like a film of the product or a screen recording with captions? Only the first is acceptable
- Does it pass the Always rules in section 1: readable at phone size, matching the product as it ships, honest about anything left out?

Motion check on the draft render. Pull frame strips across the lift outs and the resolve with ffmpeg and look at them, then step through every transition frame by frame against section 7:

- Any hard cut, pop in, stall or dead frame between moves?
- Any jitter or shimmer on text and edges?
- Does the rendered duration match the video brief? A 10 s brief that renders at 20 s is fixed or flagged before sending
- For a loop, does the last frame meet the first?
- Is there one frame that tells the story on its own? Use it as the poster, since many people see only that (a thumbnail, a paused autoplay)

If any answer is wrong, fix it before showing the draft. Then watch the draft against the video brief: would someone who has never seen the product understand the main message, and would they see the product doing its thing within the first 5 seconds? Stop there and wait for the user's approval before the final export.

In the hand over, list any lint warnings you chose to keep and why.

## Voice for on screen text

Short, plain, specific. Real feature names from the product. No buzzwords. Follow the product's own voice and any writing preferences the user has given or the project's docs define.

## Appendix: capturing the real UI

Use this when you need the product's real interface as markup in section 2. The goal is the same for every method: for each state the video will show, record the rendered markup and the product's own CSS and fonts, so HyperFrames can animate real elements instead of a rebuild or a screenshot.

Pick the method that fits the product. Say in the video brief which one you used.

### A. React app, flows built from components

Works when the screens are React components and the data layer can be mocked. Nothing runs against a production database.

1. Bundle a small harness outside the app that imports the real page or flow components.
2. Render them in jsdom with a mocked data layer: stub `fetch` and seed the query cache.
3. Drive the flow with real click and input events and record the markup of every state.
4. Compile the app's own Tailwind or CSS with its build tool and use its font files.

Pitfalls:
- A control's hidden input often shares its id and sits at the page's top-left. Target the visible element (`role` selectors).
- Prefix ids per captured state so one page can hold all of them.
- Measure target positions before applying any camera transform.
- Disable the app's CSS transitions and animations (`transition: none !important`) so every frame is a function of timeline time.
- Keep every font stack declared, the monospace stack included.

### B. Any web app that runs locally (Next.js, Payload admin, server rendered, other frameworks)

Works when you can start the app locally with seeded or dev data. Never point it at production.

1. Start the app with realistic seed data.
2. Drive the flow in a headless browser (Playwright is usually installed) with real clicks and typing.
3. In every state, save the page's markup with the computed styles it needs, or the compiled stylesheet next to it, plus the font files.
4. Apply the same pitfalls as above: disabled transitions, per state id prefixes, measured target positions.

### C. A public website or a live product you cannot run

Use HyperFrames' website capture skill on the URL. It gives you the page's markup, styles and assets as a starting point. Invent names and copy if the site is a stand in for a real client (see section 5).

### D. The product cannot be rendered

Native or mobile apps you do not have source for, third party tools, products behind a login you cannot use, hardware.

- Ask the user for screens or a recording of each state the video needs.
- Say in the video brief that these are screenshots, so the user knows the limits.
- Keep camera pushes modest so the pixels hold, and lift out only elements that stay sharp at the larger size.
- Where one small part is simple (a button, a card, a toast), rebuild only that part from the screenshot with the product's tokens and say so.

### Check before building

- Compare each captured state against the product as it ships, ideally with the user's own screenshot of the real thing. Steps, counts, labels and hints must match.
- Open one captured state at the largest zoom the video will use. Text and edges must be sharp.
