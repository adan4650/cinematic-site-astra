---
name: higgsfield-cinematic
description: Prepare atmospheric hero-video prompts and obtain usable background media through available Higgsfield tools or a supplied file. Use for cinematic website backgrounds, not narrative videos, ads, or general Higgsfield account management.
---

# Cinematic hero media

Read [the prompt guide](references/prompt-guide.md) for camera, lighting, material, and mood examples. Its settings are creative targets; use only parameters supported by the selected model and interface.

## Art direction

Aim for an 8–10 second, 16:9, looping atmospheric clip with quiet space behind the text. Prefer a locked camera with repeating environmental motion for the most convincing loop. Slow continuous movement is an alternative; inspect the actual loop rather than assuming a prompt guarantees it. Favor textures, light, landscapes, and material detail unless the brief requests a particular product or subject.

Specify composition, one coherent movement, lighting direction and color temperature, color grading, and a credible end-to-start transition. Avoid rendered lettering or logos in the background. Describe reference images you actually inspected and attach them using the integration's supported reference mechanism.

## Execution

Discover current Higgsfield capabilities. Use connected media tools when available; otherwise inspect the authenticated browser UI. Follow the installed integration's required workflow when invoking it. Do not invent model IDs, reference syntax, DOM selectors, or download endpoints. If the requested model is unavailable, explain supported alternatives instead of silently switching a material creative choice.

Use existing spending authorization. Otherwise present the exact prompt, model, duration, settings, and available cost information before requesting generation approval. Keep account authentication with the user. Do not assume a free tier covers this model.

Store the submitted job ID in the generated output's `media-status.md`. Observe completion through that same job or browser result. At a timeout, preserve the ID and explain the pending state. Resume polling rather than launching a duplicate. Report failures without automatic paid regeneration.

## Delivery

Save the actual video as `public/hero.mp4` only if it is an MP4; convert other formats with available media tools or use their correct extension and MIME type. An HTTP success or a large file is not enough: reject HTML/error responses, inspect type and duration when possible, and verify browser playback. Record source and generation settings without credentials or signed URLs.

Create `public/hero-poster.jpg` or another actual supported image from the video. If extraction is unavailable, use a supplied or deliberately authored fallback and label its origin. Keep dimensions and compression appropriate for a background; check wide and mobile crops and compare the loop boundary.

If generation, download, or extraction is unavailable, deliver a usable prompt and poster, state the missing step, and continue building around those assets. Never report a generated video until a real successful result is available.
