---
name: cinematic-generate
description: Create a cinematic landing page from a brand brief, coordinating hero media, a Next.js project, verification, and deployment when requested. Use for complete cinematic site requests, not unrelated frontend work or repository maintenance.
---

# Generate a cinematic site

Produce a complete project in `outputs/<slug>/`. Start with the brief and optional visual reference. Read [video guidance](../higgsfield-cinematic/SKILL.md) when preparing media and [site-building guidance](../cinematic-site-builder/SKILL.md) plus [design guidance](../cinematic-taste/SKILL.md) when building.

## Brief and destination

Extract the name, audience, purpose, mood, headline direction, and CTA destination. Inspect an attached reference before describing or reproducing its visual language. Infer reversible design choices and state them briefly. Ask only for details that materially affect execution. A missing brand name may use a clearly identified working name.

Use a lowercase kebab-case slug with no path separators. Resolve it under the repository's `outputs/` directory. If occupied, choose a numbered suffix; editing an existing output requires an editing request. Save `brief.md` there with the chosen direction and media/deployment scope.

## Hero media

Choose the applicable route:

- **Existing video:** inspect and copy the supplied asset into the output's `public/` folder; derive a poster if tooling permits.
- **Generate with Higgsfield:** prepare the prompt and settings, then use available authenticated tools. Prefer a connected integration over browser automation when it supports the operation. Discover the actual model and its accepted duration, resolution, and reference inputs. Seedance 2.0 is the original creative baseline, not an assumption about current availability.
- **Media pending:** create a deliberate local poster and build the working page now. Save `video-prompt.md` and clearly identify the final video as pending. Do not create a fake `hero.mp4` or request a URL for a nonexistent file.

Reuse existing generation authorization. If approval or credits are missing, ask for the concrete missing decision while continuing independent building. After submission, retain the job ID and poll that job; do not resubmit on a slow response. A failed job is not authorization for repeated paid attempts.

## Build and verify

Create the project and meaningful CTA behavior using the site-building skill. Verify installed dependency compatibility and save the lockfile. Produce concise, brand-specific copy with a clear hierarchy and readable video overlay.

Run the generated site's `npm run typecheck` and `npm run build`, plus lint when configured. Preview desktop and mobile, keyboard access, a short viewport or text zoom, reduced motion, pause/resume, and missing-media behavior. Fix issues before calling the site complete. Record actual commands and results in `verification.md` within the output.

## Deployment and handoff

When deployment is part of the user's request, use the chosen provider and account after verification. For Vercel, run the CLI inside this output and confirm the selected project. Default to preview unless production was requested; do not describe a preview as a production release. Open the returned URL and check the rendered result when browser access is available.

For local-only work, deliver the folder and run commands. Final status should state what was built, media readiness, checks performed, and the verified URL if deployed. If media or deployment is blocked, distinguish the completed local site from the remaining external step.
