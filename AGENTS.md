# Cinematic Site — Astra

This is an agent workflow repository. There is no root application to run. Generate self-contained sites in `outputs/<slug>/` and run application commands there.

## Task routing

- For a brief requesting a cinematic landing page, read [.agents/skills/cinematic-generate/SKILL.md](.agents/skills/cinematic-generate/SKILL.md).
- For video prompting or generation only, read [.agents/skills/higgsfield-cinematic/SKILL.md](.agents/skills/higgsfield-cinematic/SKILL.md).
- For an existing generated site's implementation, read [.agents/skills/cinematic-site-builder/SKILL.md](.agents/skills/cinematic-site-builder/SKILL.md).
- For visual refinement, read [.agents/skills/cinematic-taste/SKILL.md](.agents/skills/cinematic-taste/SKILL.md).

Repository maintenance does not require generating a site or invoking media tools. Read only skills relevant to the task. User requests and supplied brand references take precedence over aesthetic defaults.

## Execution

Inspect the tools available in this session. Prefer a connected Higgsfield integration when it can perform the media task; otherwise use available browser tools or a user-supplied video. Do not invent tool names, media IDs, completed renders, or deployment URLs. Use the installed service's own skill when it is needed to operate that integration.

Proceed on clear briefs with reasonable assumptions. Ask only for missing details that affect the result or prevent execution. Existing authorization persists: do not repeatedly request approval for the same scope. Before spending credits without authorization, prepare the exact prompt/settings and request the missing approval; do independent site work meanwhile. Deploy only when requested or already authorized, using the intended account and project. A local-only request stays local.

Keep credentials out of prompts, Git, and generated client bundles. Authentication happens through the service's normal sign-in flow. Do not change global Codex settings or install skills globally as part of site generation.

## Output and validation

Create a new slug directory, adding a suffix if it already exists, unless the user asks to edit that existing output. Never overwrite a previous site during generation.

Default stack: Next.js App Router, TypeScript, React, Tailwind v4 with `@tailwindcss/postcss`. Resolve currently compatible packages, save a lockfile, and list every imported dependency. Keep layout/metadata on the server and interactive video/motion in a client component.

Before calling a site complete:

- Run its type check and production build. Run lint if configured; record any checks that could not run.
- Inspect desktop and mobile, short screens or text zoom, keyboard focus, CTA behavior, and console errors.
- Verify reduced motion suppresses decorative video playback, a visible pause control works, and missing video leaves a readable poster fallback.
- Verify real media and any deployment URL before reporting success. If a dependency is unavailable, name the blocked step and deliver completed work honestly.

The root contains instructions and configuration only; validate syntax and local references after editing. Do not claim an application build or paid video generation was tested when only these files were checked.
