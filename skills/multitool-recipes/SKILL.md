---
name: multitool-recipes
description: Proven step-by-step pipelines for MULTITOOL: reel from raw clips, render to real photo in 4K, speech-to-text via free HF Whisper, AI-site picker, PC cleanup to Recycle Bin, ancestor search in war archives, publishing a GitHub project. Use when a task matches one of these.
---

# MULTITOOL recipes

Tested pipelines. Follow the matching recipe step by step instead of improvising; adapt only what the task needs. Talk to the user in their language.

## R1. Reel from raw clips (9:16, any length)
1. Find the clips (chat uploads, or the PC's Downloads/Videos by newest date). Stage them; make 540×960 proxies and one contact sheet per clip (1 frame / 2 s).
2. Speech: transcribe the talking clips (R3). Mark lines usable as a hook.
3. Research only if asked: top reels in the niche from other creators (TikTok search → playCount from the video page), note hook style, captions, cut rhythm.
4. Structure: **hook (0–2 s: before→after or a question on a plate)** → intro speech → process montage cut on the beat (0.5–1.5 s shots, light speed ramps) → main speech with cutaways on the words → result reveal → end card (brand, address, CTA).
5. Never reuse the same shot; one source moment once. Face shots stay lip-synced to their audio.
6. Text: word-highlight subtitles on a dark plate (Inter Black ~70 px, y≈1270), one accent plate for the key phrase, chips for process steps, progress bar.
7. Audio: voice first (×3 gain, compressed), music bed ducked to ~10% under speech, ~20% in montage, **no transition whooshes unless asked**; loudnorm −14 LUFS.
8. QC: 10 frames tiled, levels per section, duration exact, size < 100 MB. Deliver in chat (> 30 MB can't be written to the PC).

## R2. Render or sketch → real photo, 4K
1. Crop away logos/plates rather than painting over them; check the exact band edge by row brightness.
2. Free route: FLUX.1 Kontext Space (`black-forest-labs-flux-1-kontext-dev.hf.space`) via Playwright: input file in `%LOCALAPPDATA%\Temp\.playwright-mcp`, prompt = "ordinary real-life smartphone photo… keep the same geometry, roof colour, materials, camera angle" + concrete real-world imperfections (uneven lawn, dust on paving, reflections in glass).
3. Save the result: `browser_evaluate` fetch → base64 into a file in that folder → `device_stage_files` → decode.
4. Upscale: AuraSR-v2 Space (×4) → resize to 3840 px wide; light grade only (WB, slight contrast, lens distortion 1%, small vignette, fine grain). Heavy grading makes it look fake.
5. Anonymous ZeroGPU quota runs out after ~3 runs: say so and offer the paid route (Creative Claw / CellCog nano-banana) or a retry later.

## R3. Speech-to-text without local Whisper
1. Extract mono 16 kHz mp3 (24–32 kbps) per clip.
2. The file needs a public URL: ask the user before a temporary branch in their own repo, push audio only, transcribe, delete the branch right after (via the GitHub branches page if git push --delete fails).
3. In the browser on `hf-audio-whisper-large-v3.hf.space`: fetch the mp3 → `/gradio_api/upload` → `/gradio_api/call/transcribe` → read the stream. One clip per call; null = quota hit.
4. Word timing: split phrases at energy dips (100 ms RMS), distribute words by syllables. Tell the user timing is approximate; fix obvious mishearings by meaning and say which.

## R4. AI website picker (user signs in and pays there)
| Need | First choice | Alternatives |
|---|---|---|
| Video from text/photo | higgsfield.ai | klingai.com, runwayml.com, lumalabs.ai, hailuoai.video, pika.art |
| Image / photo edit / render→photo | higgsfield.ai | krea.ai, leonardo.ai, ideogram.ai, HF FLUX Kontext |
| Voice-over | elevenlabs.io | vidIQ voiceover (credits), HF Chatterbox Space |
| Music | suno.com | udio.com, Abracadabrax (credits) |
| Upscale | HF AuraSR-v2 | Finegrain enhancer, krea.ai |
Drive the page with the built-in browser (text first, screenshots only to check visuals); download into the PC folder the user wants.

## R5. PC cleanup (no deletion rights)
1. Inventory only connected folders; summarise in code (sizes, dates, groups).
2. Group candidates: audio fragments, old reels, duplicate installers, sources of finished work, temp Office files (`~$`, `~WRL`). Exclude: family photos, backups, Claude rule sets and briefs, study materials, anything the user named.
3. Ask with a multi-select; respect conditions in "Other".
4. Write `ochistka.ps1` (Microsoft.VisualBasic FileSystem.DeleteFile → SendToRecycleBin, UTF-8 BOM) + `ZAPUSTIT_ochistka.bat` launcher that removes itself; put them on the Desktop; the user double-clicks. Report freed MB and what was kept.

## R6. Ancestor in WWII archives (Pamyat Naroda and others)
1. Ask for full name, birth year, region, any family memories (front, wounds, awards, later city).
2. pamyat-naroda.ru search by surname + name (middle name only sorts), filter by year; open person cards and award documents; read award sheets for battle details.
3. Born after ~1927: likely not at the front; look for post-war service, home-front labour medals, local archives.
4. Confirm with family facts; separate confirmed from likely; give links to the documents.

## R7. Publish a project on GitHub
1. Build the repo locally: README (banner, badges, what/why, install, usage `/<skill> <task>`), INSTALL.md, LICENSE, CHANGELOG, CONTRIBUTING, assets, dist zips, `.claude-plugin/` marketplace for one-command install.
2. Prefill github.com/new in the browser; the user clicks **Create**; then attach the repo with push access and push.
3. Topics, avatar and social preview are set by the user (settings pages); give exact steps.
