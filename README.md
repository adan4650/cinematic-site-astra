# Cinematic Site — Astra Edition

Turn a short brand brief into a cinematic landing page with **Codex + Astra**, Higgsfield video, and a deployable Next.js project.

Adapted from [Logiaweb/cinematic-site](https://github.com/Logiaweb/cinematic-site). This repository contains agent instructions and reusable skills, not a prebuilt website or an OpenAI API service. Codex creates each website in `outputs/<slug>/` when you give it a brief.

## Start in Codex

1. Clone your copy:

   ```sh
   git clone https://github.com/adan4650/cinematic-site-astra.git
   cd cinematic-site-astra
   ```

2. Open this folder as a Codex project and start a new chat. Choose **Astra** in the model selector. The project configuration defaults to `gpt-6.2-astra` where supported; select an available Astra model if your account or client differs. No OpenAI API key is needed for this repository when using Codex with your ChatGPT sign-in.
3. Send a brief:

   ```text
   Use $cinematic-generate to create a cinematic landing page for Ember & Oak,
   a luxury candle brand. Warm amber light, dark stone, quiet atmosphere.
   Build locally first and use a poster until I choose a video.
   ```

   Or use ordinary language: `Create a cinematic site for my outdoor brand, Ridgeline.`

Codex reads [AGENTS.md](AGENTS.md) and discovers skills in `.agents/skills/`. If your client has not refreshed its skill list, start a new session or explicitly ask it to read [.agents/skills/cinematic-generate/SKILL.md](.agents/skills/cinematic-generate/SKILL.md). The original Claude `/generate` command is replaced by `$cinematic-generate`; typing `/generate` is not a portable Codex command.

## What you need

| Capability | Requirement |
| --- | --- |
| Generate project files | Codex with access to this folder and a shell |
| Install and run a generated site | A supported Node.js LTS release with npm; use Node 24 LTS as a starting point and check the chosen Next.js version's engine requirement |
| Generate new video | Connected Higgsfield tools or an authenticated browser, access to the chosen video model, and enough credits |
| Use existing video | A local video you provide; Higgsfield is optional |
| Preview the site | Available browser tools or a browser you open yourself |
| Deploy to Vercel | Vercel access, a selected account/project, and a request to deploy |

The root has no `package.json`: run npm commands inside a generated site. New media generation may consume credits. A clone alone does not connect Higgsfield, grant model access, log into Vercel, or install browser tools.

## Workflow

1. **Brief:** infer a visual direction, inspect any reference, and choose a new output folder.
2. **Media:** use your existing video, generate with available Higgsfield tools, or build with a real poster while media is pending.
3. **Build:** create a Next.js App Router site with TypeScript, React, Tailwind v4, and restrained motion.
4. **Verify:** run type checking and a production build; inspect desktop, mobile, keyboard access, video failure, and reduced motion.
5. **Deploy when requested:** deploy the verified output, then check the returned URL.

The default composition is a dark, spacious hero with left-aligned type and one accent. It fills the viewport where content fits and remains scrollable when a short screen or enlarged text needs more room. Decorative video has a poster, reduced-motion behavior, and a pause control.

## Browser and Higgsfield setup

Use connected Higgsfield tools first when they support the task. Available browser tools are a fallback. If neither is available, the agent can still build the site and provide a video prompt for you to run manually.

For optional Chrome DevTools MCP, follow [the browser setup guide](docs/browser-setup.md). Its sample configuration is opt-in; the repository does not automatically start a browser server. It uses the official `chrome-devtools-mcp` package.

## Run a generated site

After Codex creates an output, change into its directory:

```sh
cd outputs/ember-and-oak
npm ci
npm run dev
```

Use `npm install` on the first run if the agent could not create a lockfile. Verify with:

```sh
npm run typecheck
npm run build
```

Ask Codex to deploy when ready. For a manual Vercel preview, from the generated site:

```sh
npx vercel login
npx vercel
```

Use `npx vercel --prod` only for an intended production deployment. Generated sites are ignored by this workflow repository, as in the original. To version one, initialize it as a separate repository or deliberately change the output ignore rule.

## Use in regular ChatGPT

Open [the standalone ChatGPT prompt](prompts/chatgpt-astra.md), copy the prompt block into your chat or project instructions, and supply your brief and any reference. Choose Astra if it is available on that surface.

The prompt is self-contained. File creation, browser control, video generation, and deployment depend on tools actually available in that chat. Without those tools, it provides site files, a media prompt, and run instructions and identifies the steps still requiring execution.

## Repository map

```text
AGENTS.md                              Repository guidance for Codex
.codex/config.toml                     Astra default; no permission overrides
.codex/chrome-devtools.example.toml     Optional browser MCP configuration
.agents/skills/
  cinematic-generate/                  End-to-end orchestration
  higgsfield-cinematic/                 Hero-video prompting and delivery
  cinematic-site-builder/               Next.js build and verification
  cinematic-taste/                      Visual direction and interaction quality
prompts/chatgpt-astra.md                Self-contained ChatGPT instructions
docs/browser-setup.md                  Browser setup and troubleshooting
docs/repository-review.md              Complete source review and migration notes
outputs/                              Generated sites (ignored)
```

## Review and credits

See [the repository review](docs/repository-review.md) for every source file examined, the changes, and validation limits.

- Original workflow: [Adrien Ninet / Logiaweb](https://github.com/Logiaweb/cinematic-site).
- Original design guidance credits [Taste Skill](https://github.com/Leonxlnx/taste-skill).
- Video service: [Higgsfield](https://higgsfield.ai).
- Astra adaptation maintained in [adan4650/cinematic-site-astra](https://github.com/adan4650/cinematic-site-astra).

Original Git history and attribution are retained. The reviewed upstream commit contains no license file; this adaptation does not add or imply a license for upstream material.

Reference documentation: [Codex skills](https://developers.openai.com/codex/skills), [MCP configuration](https://developers.openai.com/codex/mcp), and [model selection](https://learn.chatgpt.com/docs/models).
