# Repository review and Astra migration

Reviewed on November 20, 2026. Source: [Logiaweb/cinematic-site](https://github.com/Logiaweb/cinematic-site), default branch `main`, commit [`9f22a3b24abac4d4e4e60b2f10373142b2b52b47`](https://github.com/Logiaweb/cinematic-site/commit/9f22a3b24abac4d4e4e60b2f10373142b2b52b47).

## Scope and architecture

All nine tracked files at that commit were reviewed, including hidden configuration. The original contains a Claude command, three instruction skills, project guidance, MCP configuration, documentation, ignore rules, and an empty output placeholder. It contains no implemented website, root package manifest, executable generator, API integration, test suite, or CI workflow. Other branches and the open pull request are outside this default-branch review.

The workflow is agent-driven: instructions ask the assistant to create video, write a Next.js project, and deploy it. Renaming the model alone would not make Claude's command and skill discovery work in Codex. This adaptation preserves that architecture and the original Git history while providing Codex-native entry points and a standalone ChatGPT prompt.

## Every source file

| Original file | Finding and Astra treatment |
| --- | --- |
| `README.md` | Claude setup and `/generate` usage; rewritten for Codex/Astra, prerequisites, local execution, optional deployment, and ChatGPT usage |
| `CLAUDE.md` | Claude-specific project entry point; replaced with concise `AGENTS.md` routing and verification guidance |
| `.mcp.json` | Claude configuration using `@anthropic-ai/chrome-devtools-mcp@latest`; replaced by an opt-in Codex TOML example using the official `chrome-devtools-mcp` package |
| `.claude/commands/generate.md` | `$ARGUMENTS` command, mandatory stop points, browser-only generation, and automatic deployment; replaced with the `cinematic-generate` skill, capability-based execution, and scope-aware deployment |
| `.claude/skills/higgsfield-cinematic/SKILL.md` | Useful creative library, but rigid settings and unverified reference syntax; retained as an adapted reference behind a concise `higgsfield-cinematic` skill |
| `.claude/skills/site-builder/SKILL.md` | Template specification rather than code; replaced with a focused implementation skill that resolves playback, layout, and verification gaps |
| `.claude/skills/taste/SKILL.md` | Overbroad rules, contradictory defaults, and requirements unrelated to a static hero; narrowed into `cinematic-taste` with reference-led defaults |
| `.gitignore` | Ignored `.env` but not its local/production variants; expanded environment, build, deployment, and local-state exclusions while retaining the generated-output convention |
| `outputs/.gitkeep` | Empty placeholder; retained |

## Functional issues addressed in the instructions

1. **Discovery and invocation.** `.claude/commands`, `.claude/skills`, and `CLAUDE.md` are replaced by `AGENTS.md` and four named skills under `.agents/skills`. Directory and frontmatter names now match. Each skill includes Codex UI metadata with a valid `$skill-name` prompt.
2. **Browser configuration.** The original namespaced package differs from the package documented by Chrome DevTools. The new example uses its official name and Codex's `mcp_servers` format, with a Windows launch alternative. Browser setup is optional, avoiding a mandatory server where connected tools already suffice.
3. **Tool and account assumptions.** An account, a normal browser login, and a repository clone do not prove the agent has media access. The workflow checks actual capabilities, supports connected Higgsfield tools, and allows a supplied video or poster-first build. No free-tier or fixed generation-time guarantee remains.
4. **Autoplay versus reduced motion.** Upstream says autoplay is always required while separately promising no playback for reduced motion. The implementation guidance now starts from a poster, checks preferences before starting, handles changes, and retains fallback media on playback failure. It also specifies a keyboard-accessible pause control.
5. **Viewport clipping.** Upstream requires both fixed viewport height with hidden overflow and minimum viewport height. The new rule uses minimum height and permits vertical overflow for short screens and enlarged text, preserving content and controls.
6. **Build verification.** A dev-server screenshot is insufficient evidence for a production build. Generated sites must include a typecheck script, resolve dependencies and a lockfile, build successfully, and undergo focused browser checks. No application is falsely implied to exist at the repository root.
7. **Media reliability.** A file larger than 500 KB could still be an error response. The revised workflow verifies format/playback, uses an actual poster, retains generation job IDs, and avoids duplicate submissions after a timeout.
8. **Creative consistency.** The upstream orbit example disagrees with its listed angular speed, while other examples describe one-way camera travel as a loop. The adapted guide corrects the orbit example and uses fixed framing in the warm/nature examples. All loops still require visual inspection. Unsupported `@material[...]` placeholders are replaced by descriptive reference labels.
9. **Deployment semantics.** Upstream labels `vercel --yes` as an automatic live deployment without separating preview from production. The adaptation uses the requested provider/project, verifies the result, and distinguishes preview from explicitly requested production.
10. **Design contradictions.** Removed below-the-fold and scroll-indicator references from the single-hero workflow, the inconsistent `LAYOUT_VARIANCE` variable, mandatory skeletons for static content, and blanket animation/font restrictions that could override the user's brand. The cinematic design intent remains.

## Added files

- `.codex/config.toml`: Astra model default, without permission or sandbox overrides.
- Four `agents/openai.yaml` files: skill names, descriptions, and invocation prompts.
- `prompts/chatgpt-astra.md`: self-contained instructions for a chat with or without execution tools.
- `docs/browser-setup.md`: optional setup, separate browser-profile authentication, and troubleshooting.
- `.gitattributes`: consistent text line endings across operating systems.

## Validation and limits

Validation covers skill frontmatter and naming, UI metadata, TOML parsing, relative Markdown references, ignore-rule behavior, and Git whitespace checks. Configuration and prompt review cannot prove a model will follow every instruction or that a future generated site will build.

Migration checks passed: the skill-creator validator accepted all four skills; all four UI metadata files and both TOML files parsed; all 18 local Markdown links resolved; all 13 environment/output/config ignore cases passed; and Git reported no whitespace errors.

No paid video was generated, no sample website was requested or built, and no Vercel deployment was performed as part of this repository migration. Those checks belong to each generated site's execution. The optional browser server was not launched. All external service operations still require actual account access and supported capabilities.

## Attribution and documentation

The source commit contains no license file. Original attribution and Git history are retained; no replacement license is asserted for upstream material.

Compatibility references: [Codex skills](https://developers.openai.com/codex/skills), [Codex MCP](https://developers.openai.com/codex/mcp), [Astra model selection](https://learn.chatgpt.com/docs/models), [Chrome DevTools MCP client setup](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/main/docs/client-configurations.md), [Node release status](https://nodejs.org/en/about/previous-releases), [Next.js installation](https://nextjs.org/docs/app/getting-started/installation), and [Vercel deployment](https://vercel.com/docs/cli/deploy).
