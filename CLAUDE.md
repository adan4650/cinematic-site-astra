# Cinematic Site Generator

A standalone system that generates cinematic hero websites with AI-generated video backgrounds via Higgsfield/Seedance 2.0 - fully on autopilot.

---

## How It Works

One brief in, live deployed website out. The `/generate` command orchestrates the full pipeline:

1. **Brief** - Parse the text brief + optional reference image for visual direction
2. **Video Generation** - Generates a Seedance 2.0 prompt, then automates Higgsfield.ai via Chrome DevTools MCP to create and download the video
3. **Site Building** - Creates a single-viewport Next.js hero page (no scroll) using the Site Builder skill with Taste design quality enforcement
4. **Deploy** - Automatically deploys to Vercel and returns the live URL

---

## Project Structure

```
.
├── CLAUDE.md                                    # This file
├── .mcp.json                                    # Chrome DevTools MCP config (auto-loads)
├── .claude/
│   ├── commands/
│   │   └── generate.md                          # Main generation command
│   └── skills/
│       ├── higgsfield-cinematic/SKILL.md        # Seedance 2.0 prompt generation
│       ├── taste/SKILL.md                       # Design quality enforcement
│       └── site-builder/SKILL.md                # Next.js hero page template specs
├── outputs/                                     # Generated sites land here
│   └── {slug}/                                  # Each site is a deployable Next.js project
└── README.md                                    # Setup guide for sharing
```

---

## Command

### `/generate`

Usage: `/generate "A luxury candle brand called Ember & Oak"`

Takes a text brief and produces a complete cinematic hero landing page with AI-generated video background. See `.claude/commands/generate.md` for full documentation.

---

## Skills

| Skill | Purpose |
|-------|---------|
| `higgsfield-cinematic` | Generates optimized Seedance 2.0 prompts for hero background videos (8-10s, 16:9, looping) |
| `taste` | Enforces premium design quality - no generic AI aesthetics, strict typography/color/layout rules |
| `site-builder` | Defines the Next.js hero page template, component structure, and responsive behavior |

---

## Stack

- Next.js 16 + React 19 + Tailwind v4
- App Router with `src/` directory
- TypeScript
- Framer Motion (spring physics)

---

## Output

Generated sites land in `outputs/{slug}/` as complete, self-contained Next.js projects. Each is auto-deployed to Vercel during generation. To run locally:
- `cd outputs/{slug} && npm run dev`

---

## Requirements

- Chrome DevTools MCP (configured in `.mcp.json`, loads automatically)
- Higgsfield.ai account (user must be logged in for browser automation)
- Vercel CLI (`npm i -g vercel && vercel login`)
- Node.js 20+
