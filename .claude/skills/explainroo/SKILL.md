---
name: explainroo
description: Reference for the explainroo CLI, a local renderer that turns a project (script.md + scenes.js + video.json) into a narrated explainer MP4 using Kokoro TTS, Whisper word timing, Chrome and ffmpeg. Use when the user wants to create, preview, voice, check, render or verify an explainer video with explainroo, or asks about its commands, video.json options, or environment variables.
---

# explainroo

Source: LinuxCommandLibrary (`assets/commands/explainroo.md`). Full reference: [reference.md](reference.md).

## Typical workflow

1. `explainroo doctor --fetch` — check Node ≥20.11, ffmpeg, Chrome; download models (~400 MB).
2. `explainroo init <dir> --theme chalk --size youtube --title "..."` — scaffold project.
3. Edit `script.md` (narration, one `## scene-id` heading per scene) and `scenes.js` (drawings).
4. `explainroo preview <dir>` — live preview on port 4400.
5. `explainroo voice <dir>` — narration + word timings.
6. `explainroo check <dir>` — layout/timing/pronunciation problems (exit 1 on errors).
7. `explainroo render <dir> --draft`, then `explainroo render <dir> --workers 4` → `out/video.mp4`.
8. `explainroo verify <dir>` — loudness, black frames, silence, intelligibility.

## Notes

- Install from Git, not npm: `git clone https://github.com/vincentsch/explainroo.git && cd explainroo && npm install && npm link`.
- `--json` prints machine-readable output; `--quiet` suppresses logs.
- `image` needs `OPENROUTER_API_KEY` and costs money (~7–13¢/picture) — confirm with the user first.
- Voice and pronunciation check are English only.

See [reference.md](reference.md) for all commands, `video.json` keys and environment variables.
