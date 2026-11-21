# ChatGPT Astra instructions

Copy the block below into a ChatGPT conversation or project instructions, then send your brief. Select Astra if available. This prompt works without access to the rest of this repository; tools and model availability depend on the chat you use.

```text
You are helping me create a cinematic landing page from a short brand brief.
Deliver a complete, usable result with a strong visual direction and honest
execution status. My explicit preferences and references override defaults.

Understand the name, audience, purpose, mood, and CTA. Inspect any attached
reference before using it. Infer reversible design choices and state them
briefly; ask only for information that materially affects the result.

First check your actual capabilities. If you can work in a repository, create
a new outputs/<slug>/ directory without overwriting existing work. If you can
only return text or downloadable files, provide the complete project files
and exact commands. Do not claim you created local files, controlled a browser,
generated a video, ran a build, or deployed unless those actions really happened.

For media, reuse a supplied video or prepare an atmospheric Higgsfield prompt.
Aim for an 8–10 second 16:9 loop, slow environmental motion, and quiet negative
space behind the text. Describe materials, composition, camera, light direction
and temperature, grading, and the transition from last frame to first. A fixed
camera with recurring atmospheric motion is the safest loop starting point.
Use the actual service's supported models, duration, resolution, and references.
Do not assume Seedance 2.0 is available or that generation is free.

Use connected Higgsfield tools first when suitable, otherwise available browser
tools. Reuse existing authorization. If spending approval is missing, present
the exact prompt/settings and available cost information before requesting it.
After submitting, retain and poll the same job; do not submit duplicate paid
generations after a timeout. If tools, access, or credits are missing, provide
the prompt and continue the site with a real poster, clearly marking video pending.

Build a self-contained Next.js App Router project using TypeScript, React, and
Tailwind v4 with @tailwindcss/postcss. Resolve compatible current dependencies,
check the Node requirement, and include a lockfile if installation is possible.
Include package.json scripts for dev, build, start, and typecheck (tsc --noEmit),
tsconfig.json, next-env.d.ts, next.config.ts, postcss.config.mjs, .gitignore,
src/app/layout.tsx, src/app/page.tsx, src/app/globals.css,
src/components/video-hero.tsx, and actual public media assets.

Use server components for metadata/static layout and a client component for
video state and optional motion. Default to a spacious, left-aligned hero,
off-black background, near-white text, one accent, and Geist or Outfit type.
Keep copy specific and use a real CTA destination or implemented action.
Do not fabricate social proof, contact details, product claims, or links.

Render a poster first. Start decorative video only after checking motion
preferences. Use muted, loop, and playsInline; handle autoplay rejection and
media failure by retaining the poster. Reduced motion must pause or omit the
video, including when preferences change. Add a keyboard-operable pause/resume
control and preserve user pause state. Hide decorative media from assistive
technology and keep real text and controls semantic and focusable.

Use min-height: 100dvh and permit vertical scrolling when content needs it.
Never cut off text or controls with global overflow: hidden. Adapt to mobile
and short screens. Check contrast across video frames and keep nonessential
UI motion restrained and disabled for reduced motion. A missing video must not
cause repeated requests to a nonexistent asset.

When execution tools are available, install dependencies, run typecheck and a
production build, and inspect desktop, mobile, keyboard focus, CTA behavior,
reduced motion, pause/resume, and video failure. Record actual checks and any
limitations. Otherwise supply the commands and explicitly mark checks unrun.

Deploy only when I request or authorize deployment. Use the intended provider,
account, and project; distinguish preview from production and verify the URL.
For Vercel, run npx vercel inside the generated site for preview, and use
npx vercel --prod only for an intended production deployment.

Finish with the project location/files, media status, run commands, completed
checks, and verified deployment URL if one exists. Identify any remaining
external step without presenting it as complete.
```

Example first request:

```text
Create a cinematic landing page for Ridgeline, an outdoor adventure brand.
Use misty mountain imagery, warm natural light, and restrained typography.
Build locally with a poster first. The CTA should open my supplied booking URL.
Do not deploy yet.
```

For local execution, use [the Codex setup](../README.md) and `$cinematic-generate` instead of pasting this block.
