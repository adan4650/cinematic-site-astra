---
name: cinematic-site-builder
description: Defines the Next.js hero page template for cinematic sites. Specifies component structure, responsive behavior, video background implementation, below-the-fold section, and deployment config.
---

# Cinematic Site Builder

## Stack

- **Framework:** Next.js 16 with App Router
- **Language:** TypeScript
- **UI:** React 19
- **Styling:** Tailwind CSS v4 (via `@tailwindcss/postcss`)
- **Animation:** Framer Motion (spring physics, scroll fade-in)
- **Directory:** `src/` convention

---

## Project Structure

Every generated site follows this exact structure:

```
{slug}/
├── src/
│   ├── app/
│   │   ├── layout.tsx         # Root layout with font loading
│   │   ├── page.tsx           # Main page - renders hero (single viewport, no scroll)
│   │   └── globals.css        # Tailwind v4 imports + custom properties
│   └── components/
│       └── video-hero.tsx     # Fullscreen video background hero section
├── public/
│   └── hero.mp4              # AI-generated video (from Higgsfield)
├── package.json
├── postcss.config.mjs
├── next.config.ts
├── tsconfig.json
└── .gitignore
```

---

## Component Specifications

### `layout.tsx` - Root Layout

```tsx
// Font loading: Use next/font/google for Geist or Outfit
// Metadata: Generate from brief (title, description, og:image placeholder)
// Body: dark background color (zinc-950 or similar off-black)
// Wrap children in a single div with min-h-[100dvh]
```

Key rules:
- Load font via `next/font/google` - NEVER use `<link>` tags
- Set `className` on `<html>` element for font application
- Background MUST be off-black (zinc-950, slate-950, or neutral-950) - NEVER pure #000000
- Include viewport meta for proper mobile scaling
- Set `overflow: hidden` on `<body>` or root wrapper to prevent scrolling

### `globals.css` - Tailwind v4 Setup

```css
@import "tailwindcss";

/* Custom properties derived from the brief's color palette */
:root {
  --color-accent: /* extracted from brief */;
  --color-bg: /* off-black base */;
  --color-text: /* near-white */;
  --color-text-muted: /* gray-400 equivalent */;
}
```

### `video-hero.tsx` - Hero Section (Client Component)

This is the centerpiece. It MUST be a Client Component (`'use client'`).

**Video element requirements:**
- `muted` - always
- `autoPlay` - always
- `loop` - always
- `playsInline` - always (critical for iOS)
- `poster` frame - extract or provide a still frame for prefers-reduced-motion
- `object-fit: cover` via Tailwind `object-cover`
- Positioned: `fixed inset-0` behind all content (creates parallax-like effect on scroll)
- `z-index: 0` - base layer

**Overlay gradient:**
- Positioned over the video, under the content
- Dark gradient overlay: 30-50% opacity
- Use a multi-stop gradient for natural falloff:
  ```
  bg-gradient-to-b from-black/40 via-black/20 to-black/60
  ```
- This ensures text readability regardless of video content

**Content layout (DESIGN_VARIANCE 7 = asymmetric):**
- Content aligned LEFT, not centered (anti-center bias)
- Padding: `px-6 md:px-16 lg:px-24` (generous, asymmetric)
- Vertical centering via flex
- Max content width: `max-w-2xl` (text shouldn't span full viewport)

**Typography:**
- Brand name / headline: `text-4xl md:text-6xl lg:text-7xl tracking-tighter leading-none font-semibold`
- Subline: `text-lg md:text-xl text-white/70 leading-relaxed max-w-[50ch]`
- Use `clamp()` or Tailwind responsive utilities for fluid scaling

**CTA Button:**
- Spring physics hover effect via Framer Motion
- `type: "spring", stiffness: 400, damping: 25`
- Hover: `scale(1.02)` + slight brightness increase
- Active: `scale(0.98)` (tactile push)
- Animate ONLY `transform` and `opacity` (GPU-safe)
- Style: solid accent color background, rounded, generous padding
- Full-width on mobile (`w-full md:w-auto`)

**No scroll indicator** - the page is a single viewport, no scrolling.

**Accessibility - prefers-reduced-motion:**
```tsx
// Use matchMedia to detect
// If reduced motion preferred:
// - Show poster frame instead of playing video
// - Disable scroll indicator animation
// - Disable CTA spring hover (use simple opacity transition)
```

---

## Package Dependencies (Minimal)

```json
{
  "dependencies": {
    "next": "^16.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "framer-motion": "^12.0.0",
    "@phosphor-icons/react": "^2.1.0"  // optional - only if design reference uses icons
  },
  "devDependencies": {
    "@tailwindcss/postcss": "^4.0.0",
    "tailwindcss": "^4.0.0",
    "typescript": "^5.7.0",
    "@types/node": "^22.0.0",
    "@types/react": "^19.0.0",
    "@types/react-dom": "^19.0.0"
  }
}
```

---

## Color Strategy

Extract mood from the brief, then generate a palette:

| Brief Mood | Base | Accent | Text |
|------------|------|--------|------|
| Luxury / Warm | zinc-950 | amber-500 | white/90 |
| Tech / Cool | slate-950 | sky-400 | white/90 |
| Nature / Organic | neutral-950 | emerald-500 | white/90 |
| Bold / Energy | zinc-950 | rose-500 | white/90 |
| Minimal / Clean | neutral-950 | zinc-400 | white/80 |
| Creative / Artsy | slate-950 | violet-400 | white/90 |

Rules:
- **ONE accent color maximum** (Taste skill Rule 2)
- Saturation < 80%
- No purple/blue AI-gradient aesthetic (THE LILA BAN)
- Dark mode is the default - always

---

## Responsive Behavior

| Breakpoint | Behavior |
|------------|----------|
| < 640px (mobile) | Single column. CTA full-width. Typography scales down. Video plays (poster fallback for low bandwidth). |
| 640-1024px (tablet) | Same layout, slightly more horizontal padding. |
| > 1024px (desktop) | Full asymmetric layout. Left-aligned content. Generous whitespace. |

Typography scaling:
- Headline: `text-4xl md:text-6xl lg:text-7xl` (uses Tailwind responsive, equivalent to clamp)
- Subline: `text-lg md:text-xl`
- CTA: `text-base md:text-lg`

---

## PostCSS Config

```js
// postcss.config.mjs
const config = {
  plugins: {
    "@tailwindcss/postcss": {},
  },
};
export default config;
```

CRITICAL: Do NOT use the `tailwindcss` plugin for v4. Use `@tailwindcss/postcss`.

---

## Next.js Config

```ts
// next.config.ts
import type { NextConfig } from "next";

const nextConfig: NextConfig = {};

export default nextConfig;
```

Keep it minimal. No special video config needed - `.mp4` in `/public` is served statically.

---

## Quality Checklist

Before considering a generated site complete:

- [ ] Video plays muted, autoplay, looping on desktop and mobile
- [ ] `playsInline` is set (iOS requirement)
- [ ] Overlay gradient makes text readable over any video frame
- [ ] Typography uses Geist or Outfit, never Inter
- [ ] Maximum 1 accent color
- [ ] No pure #000000 anywhere
- [ ] `h-[100dvh]` with `overflow: hidden` - single viewport, no scrolling
- [ ] CTA has spring physics hover (transform + opacity only)
- [ ] Mobile: single column, full-width CTA, readable text
- [ ] `prefers-reduced-motion` disables video autoplay and animations
- [ ] No emojis anywhere in code or content
- [ ] All dependencies listed in package.json before importing
- [ ] If reference image was provided: design matches its visual language
