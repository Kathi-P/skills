# Product Demo Video

A Claude Code skill for creating animated SaaS product demos with [HyperFrames](https://github.com/heygen-com/hyperframes).

It helps you turn your existing product interface into a short animated video, with smooth camera movements, zooms, cursor interactions and UI elements that lift out of the screen.

Made for landing page hero sections, product launches, LinkedIn posts, YouTube B-roll and client presentations.

## Example

https://github.com/user-attachments/assets/3d78c434-db4f-44e6-a806-5d18964da5af

## How it works

The skill guides Claude through creating a product video:

1. **Explore the product.** Look through the existing codebase, interface components, design system and brand assets.
2. **Plan the video.** Ask about the purpose, main message and visual direction before creating a brief and shot list.
3. **Build the scenes.** Use the product's real interface and animate it with HyperFrames.
4. **Review and refine.** Check still frames, camera movements, timing and transitions.
5. **Render the video.** Export the finished animation as an MP4.

## Installation

You'll need Claude Code (or another compatible coding agent) and Node.js.

Install the skill:

```bash
npx skills add YOUR-GITHUB-USERNAME/skills --skill product-demo-video
```

Install the HyperFrames skills:

```bash
npx skills add heygen-com/hyperframes
```

Alternatively, copy the `product-demo-video` folder into `.claude/skills/` in your project or `~/.claude/skills/` for use across projects.

## Usage

Open your product project in Claude Code and ask:

```text
Create a short animated product demo for this app
using the product-demo-video skill.
```

Claude will explore the project, ask a few questions and help you plan the video before building it.

## What's included

- `SKILL.md`: The creative workflow, animation guidelines, planning and review steps.
- `references/hyperframes-notes.md`: Technical lessons and workarounds from previous experiments.

## Experimental

This is still a work in progress.

I've tried the skill on a couple of our own projects, and while the results are promising, some animations still need manual adjustments. It might also work differently depending on the product and its codebase.

I'm sharing it as a starting point if you'd like to experiment with something similar.

If you improve it or take it in another direction, I'd love to see what you create.

## Credits

Built to work with [HyperFrames](https://github.com/heygen-com/hyperframes), an open-source video creation tool by HeyGen.

This is an independent skill, not affiliated with or endorsed by HeyGen.

Created by [Katharina](https://bykatharina.com).
