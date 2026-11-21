---
name: cinematic-site-builder
description: Build or revise a Next.js cinematic hero landing page with resilient video playback, accessible motion controls, responsive layout, and verified deployment readiness. Use for cinematic site implementation, not unrelated applications.
---

# Cinematic site implementation

## Project

Use Next.js App Router, TypeScript, React, and Tailwind v4 as the default. Preserve a compatible existing stack when editing. Resolve currently compatible versions, check Node engine requirements, install dependencies before importing them, and save a lockfile. Motion is optional; use `framer-motion` only when it improves the requested interaction.

Create a self-contained project under the output slug with:

```text
src/app/layout.tsx              Server layout, fonts, title and description
src/app/page.tsx                Main page and real CTA destination/content
src/app/globals.css             Tailwind import, tokens, responsive styling
src/components/video-hero.tsx   Client video state and motion controls
public/                        Actual poster and optional verified video
package.json                   dev, build, start, typecheck scripts
package-lock.json              Resolved dependencies
tsconfig.json
next-env.d.ts
next.config.ts
postcss.config.mjs
.gitignore
```

Use `@import "tailwindcss";` and the `@tailwindcss/postcss` PostCSS plugin. Use `tsc --noEmit` for `typecheck` and `next build` for `build`. If linting is added, configure its actual tool and script; do not assume a `next lint` command exists. Load fonts through `next/font` when viable, with a deliberate local/system fallback if a build cannot fetch them. Do not point metadata at a nonexistent social image.

## Hero and playback

Keep metadata and static page structure on the server. Isolate playback state and any motion library in a client component. Layer a cover image/video, a directional dark overlay, and semantic foreground content. Use the design skill's defaults when the user has not specified a direction.

- Render a real poster first. Do not start video playback before the client knows the user's motion preference; this also keeps server and initial client output consistent.
- When motion is allowed, attach the real source, set `muted`, `loop`, and `playsInline`, and attempt playback. Handle a rejected `play()` promise or video error by keeping the poster visible.
- For `prefers-reduced-motion: reduce`, keep the poster and pause or omit the decorative video. Listen for preference changes, clean up listeners, and never resume while reduced motion is enabled.
- Provide an accessible, keyboard-operable pause/resume control for the continuously looping background. Reflect actual playback state and honor a user pause across unrelated renders. Do not show a functioning-looking video control when no video exists.
- Hide decorative media from assistive technology. Keep the heading, copy, links, and controls in accessible HTML above it.

CSS that merely hides a playing video is insufficient reduced-motion handling. A source must be absent until available, not a permanent 404 request. `preload="none"` or `"metadata"` is appropriate until playback is needed.

## Layout and interactions

Use `min-height: 100dvh` for the hero. Allow vertical scrolling if content exceeds the viewport; do not apply global `overflow: hidden`. Clip only the decorative media layer and prevent accidental horizontal overflow. Keep the intended single-hero composition without cutting off controls on short mobile screens or at enlarged text sizes.

Use one H1, legible copy widths, visible keyboard focus, and enough overlay contrast throughout the clip. Mobile content becomes one column. A CTA needs a real destination or implemented action. If the destination is missing, finish the layout with explicitly provisional behavior and identify the missing input before claiming production readiness; do not invent URLs or use a dead `href="#"`.

Keep UI motion subtle and limited to transform/opacity. Disable nonessential entrance and hover motion under reduced motion. Add loading states only where asynchronous work actually exists.

## Verification

Run type checking, the production build, and configured lint. Inspect the rendered site at desktop and mobile sizes, plus a short viewport or text zoom. Check console errors, keyboard traversal, CTA behavior, pause/resume, reduced motion on initial load and after a preference change, denied autoplay, and unavailable video. Verify the poster asset loads in each fallback state.

Review representative frames for contrast and mobile cropping. Record completed checks and limitations in the output's `verification.md`. Publish only within the user's deployment request; use a verified provider URL and distinguish preview from production.
