# Cinematic Site Generator

Generate a cinematic hero website with AI-generated video background.

Brief: $ARGUMENTS

---

## Instructions

You MUST read and follow all three skills before generating:
1. `.claude/skills/higgsfield-cinematic/SKILL.md` - for video prompt generation
2. `.claude/skills/taste/SKILL.md` - for design quality enforcement
3. `.claude/skills/site-builder/SKILL.md` - for site template and component specs

---

### Phase 1: Understand the Brief

1. Parse the brief to extract:
   - **Brand/project name** (required)
   - **Industry/vibe** (infer from name if not stated)
   - **Target audience** (infer if not stated)
   - **Mood keywords** (luxury, tech, nature, bold, minimal, creative)
   - **Reference image** (check if the user attached/dropped an image with the command)
2. Generate a slug from the name (lowercase, kebab-case, no special characters)
3. Check if `outputs/{slug}/` already exists - if so, append a number (e.g., `ember-and-oak-2`)
4. **If a reference image was provided:**
   - Read the image to analyze the design style
   - Extract: color palette, typography feel, layout direction, overall mood, any standout UI patterns
   - These become design constraints for the build phase — match the reference's visual language
5. Present your interpretation to the user:
   - "Here's what I'm working with: [name], [vibe], [mood]. Sound right?"
   - If a reference image was provided, mention what you extracted from it

---

### Phase 2: Generate Video Prompt

1. Using the **Higgsfield Cinematic skill**, generate a Seedance 2.0 prompt optimized for a hero background video:
   - 8-10 seconds, 16:9, looping-friendly (end state similar to start state)
   - Atmospheric, cinematic, slow-motion
   - Environmental/textural content that matches the brand mood
   - Camera movement under 2 ft/s
   - Proper lighting with Kelvin temperatures and ratios
2. Run through the Prompt Quality Checklist from the skill
3. Present the prompt to the user for approval

**STOP HERE - Wait for user to approve the video prompt before proceeding.**

If the user wants changes, iterate on the prompt. Only proceed when they confirm.

---

### Phase 3: Generate Video via Higgsfield

Use Chrome DevTools MCP to automate Higgsfield.ai:

1. **Navigate:** Open `https://higgsfield.ai` in the browser
2. **Screenshot:** Take a screenshot to assess current state
3. **Login check:** If not logged in, tell the user to log in manually and wait
4. **Find the creation interface:** Navigate to the video generation area
5. **Enter prompt:** Find the prompt input field and paste the approved Seedance 2.0 prompt
6. **Configure settings:**
   - Set aspect ratio to 16:9 if configurable
   - Set duration to ~10 seconds if configurable
7. **Generate:** Click the generate/create button
8. **Wait:** Poll for completion (take screenshots every 30 seconds to check progress)
   - Typical generation time: 1-3 minutes
   - Timeout after 5 minutes - alert the user
9. **Download:** Once complete:
   - Look for the video in the DOM or network requests
   - Download to `outputs/{slug}/public/hero.mp4`
   - Verify the file exists and has reasonable size (> 500KB)

**IMPORTANT:** The Higgsfield UI may change. If selectors don't work:
- Take a screenshot and assess the current UI layout
- Adapt your interaction approach based on what you see
- Tell the user if you can't find expected elements

---

### Phase 4: Build the Site

Follow the **Site Builder skill** specifications exactly:

1. **Create the project directory:** `outputs/{slug}/`
2. **Create all files** per the site-builder skill structure:
   - `package.json` with all dependencies
   - `tsconfig.json`
   - `next.config.ts`
   - `postcss.config.mjs` (using `@tailwindcss/postcss`, NOT `tailwindcss`)
   - `src/app/globals.css` with Tailwind v4 imports and custom properties
   - `src/app/layout.tsx` with font loading (Geist or Outfit)
   - `src/app/page.tsx` with the hero component (single full-viewport page, no scroll)
   - `src/components/video-hero.tsx` - the centerpiece
   - `.gitignore`

3. **Generate content from the brief:**
   - **Headline:** 2-5 words, impactful, concrete (no "Elevate" or "Unleash")
   - **Subline:** 1-2 sentences, clear value, lighter weight
   - **CTA text:** Action-oriented, specific to the brand

4. **Choose color palette:**
   - If a reference image was provided: extract and match the reference's palette
   - Otherwise: use the brief's mood and the Color Strategy table from the site-builder skill

5. **Apply Taste skill rules** throughout:
   - No Inter font
   - No pure #000000
   - No centered hero (DESIGN_VARIANCE 7)
   - No purple/blue AI gradients
   - Max 1 accent color
   - Spring physics on CTA
   - `h-[100dvh]` with `overflow: hidden` on the page - no scrolling
   - `prefers-reduced-motion` support

6. **Install and run:**
   ```bash
   cd outputs/{slug}
   npm install
   npm run dev
   ```

7. **Preview:** Open in browser and take a screenshot to verify the result

---

### Phase 5: Deploy

Automatically deploy to Vercel after the build is verified:

1. Stop the dev server if running
2. Run: `cd outputs/{slug} && npx vercel --yes`
3. Report the live URL to the user with a screenshot of the deployed site

**If user wants changes after deploy:** Iterate and redeploy. Common requests:
- Different headline/copy
- Color adjustment
- Layout tweaks
- Different video (go back to Phase 2)

After making changes, redeploy with `npx vercel --yes` again.

---

## Critical Rules

- Video MUST be muted autoplay with loop - no audio controls ever
- Always respect `prefers-reduced-motion` (poster frame, no animations)
- Animate ONLY `transform` and `opacity` (GPU-safe, per Taste skill)
- No generic AI aesthetics (enforced by Taste skill Section 7)
- Typography: Geist or Outfit ONLY, never Inter
- Dark mode default - always
- One accent color maximum
- No emojis in code or content
- Left-aligned hero content, not centered (DESIGN_VARIANCE 7)
- Single full-viewport hero only - `h-[100dvh]` with `overflow: hidden`, no scrolling, no below-fold section
- No scroll indicator
