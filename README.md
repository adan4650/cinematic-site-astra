# Cinematic Site Generator

One sentence in, cinematic website out. A fully automated pipeline that takes a text brief and produces a premium hero landing page with an AI-generated video background.

Powered by [Higgsfield](https://higgsfield.ai) Seedance 2.0 for video generation and [Claude Code](https://claude.ai/claude-code) for orchestration.

---

## What It Does

```
Input:  "A luxury candle brand called Ember & Oak"
Output: A live deployed website with cinematic video hero
```

The `/generate` command runs a fully automated pipeline:

1. **Brief** - You describe the site. Optionally drop a reference image for the visual direction.
2. **Video** - Claude takes control of your browser, opens Higgsfield, writes an optimized Seedance 2.0 prompt, generates a cinematic hero video, and downloads it.
3. **Build** - Creates a single full-viewport Next.js hero page around the video.
4. **Deploy** - Deploys to Vercel and returns the live URL.

---

## Prerequisites

- [Claude Code](https://claude.ai/claude-code) (CLI or IDE extension)
- [Node.js](https://nodejs.org) 20+
- A [Higgsfield.ai](https://higgsfield.ai) account (free tier works)
- Google Chrome (for browser automation)
- [Vercel CLI](https://vercel.com/docs/cli) (for auto-deployment)

---

## Setup

1. Clone this repo:
   ```bash
   git clone https://github.com/Logiaweb/cinematic-site.git
   cd cinematic-site
   ```

2. Install and connect Vercel:
   ```bash
   npm i -g vercel
   vercel login
   ```

3. Open in Claude Code. The Chrome DevTools MCP auto-loads from `.mcp.json`.

4. Log into Higgsfield.ai in Chrome before running the command.

---

## Usage

```
/generate "A luxury candle brand called Ember & Oak"
```

You can also drop a reference image alongside your brief for the visual direction.

The command will:
- Parse your brief and confirm the interpretation
- Generate a video prompt and ask for your approval
- Take control of Chrome, open Higgsfield, generate the video, and download it
- Build a single-viewport Next.js site in `outputs/ember-and-oak/`
- Deploy to Vercel and return the live URL

---

## How It Works

```
Brief (text) + optional reference image
    |
    v
[Higgsfield Cinematic Skill]  -->  Seedance 2.0 prompt
    |
    v
[Chrome DevTools MCP]         -->  Automates Higgsfield.ai
    |
    v
hero.mp4 (AI-generated video)
    |
    v
[Site Builder Skill]          -->  Next.js project
    +
[Taste Skill]                 -->  Design quality enforcement
    |
    v
[Vercel]                      -->  Live URL
```

---

## Generated Site Stack

- Next.js 16 + React 19 + TypeScript
- Tailwind CSS v4
- Framer Motion (spring physics)
- Single full-viewport video hero (muted, autoplay, loop, no scroll)
- Dark mode, responsive, accessible
- prefers-reduced-motion support

---

## Project Structure

```
cinematic-site/
├── .claude/
│   ├── commands/
│   │   └── generate.md              # The orchestration command
│   └── skills/
│       ├── higgsfield-cinematic/    # Video prompt generation
│       ├── taste/                   # Design quality rules
│       └── site-builder/            # Site template specs
├── outputs/                         # Generated sites land here
│   └── {slug}/                      # Each is a deployable Next.js app
├── .mcp.json                        # Chrome DevTools MCP config
├── CLAUDE.md                        # Project context for Claude
└── README.md                        # This file
```

---

## Examples

After running `/generate`:

| Brief | Output |
|-------|--------|
| "A luxury candle brand called Ember & Oak" | Warm amber palette, liquid/flame video background |
| "A minimal tech startup called Void" | Cool monochrome, abstract geometric video |
| "An outdoor adventure brand called Ridgeline" | Nature tones, fog/mountain atmospheric video |

---

## Credits

- Video generation: [Higgsfield](https://higgsfield.ai) Seedance 2.0
- Design quality: Adapted from [Taste Skill](https://github.com/Leonxlnx/taste-skill)
- Orchestration: [Claude Code](https://claude.ai/claude-code)
- Built by [Adrien Ninet](https://instagram.com/adrien.ninet)
