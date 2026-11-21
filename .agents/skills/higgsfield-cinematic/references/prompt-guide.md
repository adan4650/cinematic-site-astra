# Higgsfield Seedance 2.0 - Hero Background Video Prompt Generator

Adapted from the original Logiaweb prompt guide. These are creative examples,
not an API schema. Check the current model's supported settings. The defaults
below yield to the user's brief and the execution guidance in [SKILL.md](../SKILL.md).

## Purpose

Generate production-ready Seedance 2.0 prompts specifically optimized for **hero background videos** on cinematic landing pages. These are NOT narrative shorts or social content - they are atmospheric, looping video textures designed to sit behind text and UI elements.

---

## Hero Background Video Constraints

Use these starting points unless the brief or supported model settings differ:

- **Duration:** 8-10 seconds
- **Aspect Ratio:** 16:9 widescreen
- **Resolution:** 720p
- **Looping:** End state must closely match start state (seamless or near-seamless loop)
- **Audio:** None - videos will be muted on the website
- **Pacing:** Slow, atmospheric, contemplative - NEVER fast cuts or action-heavy
- **Content:** Environmental, abstract, or textural - avoid faces, text, or specific products
- **Camera Movement:** Slow and continuous - dolly, crane, orbit, or static with atmospheric motion
- **Depth of Field:** Shallow to medium - creates cinematic separation, helps text readability

---

## Master Prompt Template

Structure every Seedance 2.0 prompt using these sections:

```
SEEDANCE PROMPT - [BRAND/CONCEPT NAME] HERO BACKGROUND

HOOK & OPENING (0-2s):
[Establishing shot - what the viewer sees first. Must be visually arresting
but atmospheric, not jarring. Sets the mood immediately.]

ENVIRONMENT & ATMOSPHERE (2-5s):
[Location, materials, textures, particles. Describe the world.
Include atmospheric elements: fog, dust, light rays, reflections, smoke.]

CAMERA MOVEMENT (continuous):
[Single continuous movement throughout. Specify:
- Movement type and direction
- Speed in ft/second (keep under 2 ft/s for backgrounds)
- Focal length equivalent (24mm-50mm range)
- Depth of field (f-stop)]

LIGHTING:
[Specify:
- Key light direction, color temperature (Kelvin), intensity
- Fill ratio (keep dramatic: 2:1 to 5:1)
- Volumetric elements (god rays, haze, atmospheric scatter)
- Shadow quality (soft/hard)]

COLOR GRADING:
[Specify:
- Overall temperature (warm/cool/neutral)
- Saturation level (typically desaturated for backgrounds)
- Contrast style (lifted blacks, crushed shadows, etc.)
- Grain/texture level]

LOOP POINT (8-10s):
[Describe how the end connects to the beginning.
The final frame should feel like it could seamlessly precede the first frame.
Use: returning camera position, cycling atmospheric elements, or
matching lighting states.]

OUTPUT: 8-10 seconds, 16:9 widescreen, 720p, no audio
```

---

## Camera Movement Library (Hero Background Optimized)

Use these slow, continuous movements. NEVER use whip pans, fast cuts, or handheld shake for backgrounds.

| Movement | Speed | Best For | Prompt Phrasing |
|----------|-------|----------|-----------------|
| **Slow Dolly Forward** | 1-1.5 ft/s | Drawing viewer in, depth | "Camera dolly forward at 1 ft/second. Gentle lens breathing. No focus shift." |
| **Crane Ascend** | 0.5-1 ft/s | Revealing scale, majesty | "Camera rises vertically at 0.5 ft/second. Tilt maintains horizon." |
| **Orbit** | 5-10 deg/s | Environmental reveal, 3D depth | "Camera orbits 60 degrees clockwise over 8 seconds. Constant 6-foot radius." |
| **Static + Atmospheric** | 0 ft/s | Textural, meditative | "Camera locked static. All motion from environmental elements: particles, light shifts, surface ripples." |
| **Lateral Track** | 1-2 ft/s | Parallax depth, material showcase | "Camera tracks laterally right at 1.5 ft/second. Parallax between foreground and background layers." |
| **Slow Pull Back** | 0.5-1 ft/s | Context reveal, breathing room | "Camera pulls back at 0.5 ft/second. Gradually reveals surrounding environment." |

---

## Lighting Setups (Cinematic Background Optimized)

| Setup | Temperature | Ratio | Mood | When to Use |
|-------|-------------|-------|------|-------------|
| **Golden Hour** | 3000-3500K | Key 100%, Fill 50% | Warm, premium, luxury | Luxury brands, organic products, warmth |
| **Cool Moonlit** | 6000-7500K | Key 100%, Fill 20% | Mysterious, tech, serene | Tech brands, night themes, elegance |
| **Volumetric God Rays** | 3000K directional | Key 100% with haze | Spiritual, transcendent | Premium, aspirational, atmospheric |
| **Chiaroscuro** | 3000K single source | Key 100%, Fill 10-15% | Dramatic, bold, powerful | Strong brands, statements |
| **Soft Overcast** | 5500K neutral | Flat omnidirectional | Calm, clean, minimal | Minimalist brands, clarity |
| **Neon Practical** | Mixed color sources | Variable | Futuristic, tech, energy | Tech products, creative agencies |

---

## Background-Optimized Subject Matter

For hero backgrounds, generate prompts about ENVIRONMENTS and TEXTURES, not people or products:

### Atmospheric Environments
- Fog rolling through valleys or forests
- Rain on glass surfaces with bokeh lights behind
- Underwater caustics and light patterns
- Cloud formations from above or through them
- Desert sand dunes with wind particles

### Material Textures (Macro/Abstract)
- Liquid metal flowing and reflecting light
- Ink dispersing in water (slow motion)
- Fabric billowing in slow wind
- Molten glass or lava with surface movement
- Ice crystals forming or light refracting through them

### Architectural/Urban
- Light and shadow moving across concrete surfaces
- Reflections in glass buildings at golden hour
- Fog moving through modern architecture
- Rain creating ripples on dark stone surfaces

### Nature (Slow Motion)
- Flowers opening (timelapse feel at slow pace)
- Water cascading over rocks with mist
- Aurora borealis with slow movement
- Bioluminescent ocean waves

---

## Three Reference Prompts

### 1. Luxury / Warm / Organic

```
SEEDANCE PROMPT - LUXURY WARMTH HERO BACKGROUND

HOOK & OPENING (0-2s):
Extreme close-up of golden honey-like liquid slowly pouring over a dark
obsidian surface. Surface tension visible. Light catches the liquid edge
creating a glowing amber rim.

ENVIRONMENT & ATMOSPHERE (2-5s):
Dark studio environment. The liquid pools and spreads across the polished
black surface. Micro-bubbles visible in the liquid. Warm atmospheric haze
softens the deep background. Dust particles float through the beam of light.

CAMERA MOVEMENT (continuous):
Camera locked off throughout. 50mm equivalent lens.
f/2.0 shallow depth of field - liquid surface sharp, background dissolves
into warm bokeh. Slight downward angle (15 degrees) looking at the surface.

LIGHTING:
Single volumetric key light from upper-right at 3200K warm amber.
Intensity creates bright liquid highlights against deep shadow.
Fill ratio 5:1 (minimal fill, dramatic contrast).
Volumetric haze catches the light beam - visible god ray effect.
Shadow quality: soft falloff, no hard edges.

COLOR GRADING:
Warm overall temperature. Saturation at 85% - rich but not oversaturated.
Lifted blacks (shadows at dark brown, not pure black). Highlights glow warm.
Subtle 15% film grain. Contrast: medium-high with smooth rolloff.

LOOP POINT (8-10s):
Camera position and exposure remain identical at the start and end.
The liquid pour is continuous - end frame shows same flow state as opening.
Atmospheric particles cycle smoothly.

OUTPUT: 10 seconds, 16:9 widescreen, 720p, no audio
```

### 2. Tech / Cool / Minimal

```
SEEDANCE PROMPT - TECH MINIMAL HERO BACKGROUND

HOOK & OPENING (0-2s):
Wide shot of a perfectly still dark water surface. A single point of cool
blue light reflects from above. At 0.5s, a subtle ripple emanates from
center-frame, distorting the reflection.

ENVIRONMENT & ATMOSPHERE (2-5s):
Infinite dark water plane extending to horizon. Above the water: minimal
geometric light sources - thin horizontal lines of cool white light (6500K)
suspended at various heights. Faint fog sits on the water surface. The space
feels vast, clean, and technological.

CAMERA MOVEMENT (continuous):
Camera tracks laterally left at 1 ft/second. 35mm equivalent lens.
f/4.0 medium depth of field - water surface and nearest lights sharp,
distant lights soften. Camera height: 3 feet above water surface.
Parallax between foreground water ripples and background light geometry.

LIGHTING:
Multiple practical light sources: horizontal light bars at 6500K cool white.
No key/fill setup - lights ARE the environment. Reflections on water create
doubled geometry. Faint volumetric haze between light sources.
Overall low-key - 80% of the frame is near-black.

COLOR GRADING:
Cool temperature throughout. Near-monochrome with subtle blue cast.
Saturation at 30% - almost desaturated but retaining hint of blue.
Deep crushed blacks. Highlights are clean white with no color cast.
Zero grain - perfectly clean digital aesthetic. High contrast.

LOOP POINT (8-10s):
Lateral tracking creates natural loop - geometric light pattern repeats.
Water ripples are continuous. End position has same visual density as start.
Fog maintains consistent presence throughout.

OUTPUT: 8 seconds, 16:9 widescreen, 720p, no audio
```

### 3. Nature / Dramatic / Atmospheric

```
SEEDANCE PROMPT - DRAMATIC NATURE HERO BACKGROUND

HOOK & OPENING (0-2s):
Dense fog bank filling the frame. Depth is ambiguous. At 1s, a shaft of
warm golden light (3200K) pierces through from upper-left, illuminating
suspended particles and revealing depth layers in the fog.

ENVIRONMENT & ATMOSPHERE (2-5s):
Mountain forest clearing at dawn. Massive dark tree trunks frame the edges
(out of focus, foreground). Mid-ground: fog layer at 4-foot height,
slowly drifting right. Background: more trees visible as dark silhouettes.
God rays cut diagonal shafts through the fog. Dust and pollen particles
float through the light beams. Ground: dark moss-covered forest floor,
barely visible beneath fog.

CAMERA MOVEMENT (continuous):
Camera locked at fog-level (4 feet). 35mm equivalent. f/2.8 - foreground
trees blur, fog layer sharp, background trees soft. All motion comes from
drifting fog and floating particles; camera framing remains constant.

LIGHTING:
Golden hour directional key from upper-left at 3200K. Intensity creates
visible volumetric shafts through fog (god rays). Fill is ambient sky
light at 6000K cool blue - visible in shadow areas. Ratio 4:1.
The warm/cool contrast creates chromatic depth. Shadow quality: very soft,
diffused by fog. Dappled light pattern from canopy above.

COLOR GRADING:
Split tone: warm highlights (golden amber), cool shadows (deep forest blue).
Saturation 70% - natural but slightly muted, not vivid.
Lifted blacks to dark forest green. Highlights bloom slightly (halation).
Medium film grain (25%). Contrast: low-medium, fog reduces contrast naturally.

LOOP POINT (8-10s):
Fog drift is continuous and cyclical. God ray intensity matches at start
and end. Fixed framing avoids a camera-position jump at the loop.
Particle float provides visual continuity. Inspect the rendered loop boundary.

OUTPUT: 10 seconds, 16:9 widescreen, 720p, no audio
```

---

## Material References

If the user provides references, attach them with the actual interface's
supported reference mechanism. The following labels are descriptive placeholders,
not literal syntax to send to a model or API:

```
[Attached reference image]: Match the color palette and atmospheric quality
of this image. Use as lighting and mood reference, not literal recreation.

[Attached brand logo]: Extract dominant brand colors. DO NOT include the
logo in the video - use the colors to inform the lighting and grading.
```

---

## Prompt Quality Checklist

Before presenting a prompt, verify:

- [ ] Duration is 8-10 seconds
- [ ] Aspect ratio is 16:9
- [ ] No audio specified
- [ ] Camera movement is slow and continuous (under 2 ft/s)
- [ ] Content is environmental/textural, not people or products
- [ ] Lighting includes Kelvin temperature and ratios
- [ ] Color grading specifies temperature, saturation, contrast, grain
- [ ] Loop point described - end state connects to start state
- [ ] Mood matches the brand/brief
- [ ] Nothing in the video would compete with overlaid text/UI
