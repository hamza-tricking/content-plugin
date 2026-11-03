---
name: onboarding
description: Phases 0-2 of the content agent: qualify data sources, extract the creator's own numbers, audience, best and worst videos and writing voice, then interview the creator about intent, ambition, constraints and off-limits. Use after setup, or when the user asks to analyse their account.
---

# Onboarding (phases 0-2)

## Phase 0: source qualification
Test each available source live and write `sources.md` (works / limited / unavailable, with the exact limit). Check in order, skip what the user has not enabled:
1. Metricool connector (brand settings, networks, timezone).
2. vidIQ connector (balance first; log any spend in `ledger.md`; keep a floor the user sets; free tools before paid ones).
3. Claude in Chrome for logged-in pages (Instagram insights, TikTok Studio). Use Chrome, not an embedded browser that blocks social sites.
4. Public tools (Social Blade, Countik) for follower history.
Log failures in `gaps.md` and go down a layer. Never create accounts or enter credentials; ask the user to do that step.

## Phase 1: extraction (the creator's own data)
- Last 30 days per platform: number of videos, median and total views, likes, comments, shares, completion/skip when available.
- Audience: country, gender, age; share of views from non-followers.
- Best and worst 3 videos. Local-first video analysis (protocol below) before any paid analysis.
- Voice profile: from real captions (and the user's `my-writing-style` skill if installed). Mark what is inferred.
- Save to `vault/` with dates. Reuse if fresher than 7 days.

### Local-first video analysis protocol
1. Ask explicit approval per batch: files, source, approximate size. A yes does not extend to later batches.
2. Download with `python -m yt_dlp` (Instagram reel/post URLs usually work without cookies; TikTok often refuses: do not circumvent, do not read browser cookies; use the user's own original files if they have them).
3. Audio: faster-whisper, model `medium`, language set to the user's, CPU `int8` if CUDA libs are missing. If PyAV errors, decode with `ffmpeg -f f32le -ac 1 -ar 16000 -` into a numpy array. Dialect transcripts are rough: hooks are understandable, details are not; say so.
4. Frames: hook sheet `ffmpeg -t 6 -vf "fps=2,scale=270:-1,tile=4x3"`, body sheet `fps=1/4,scale=216:-1,tile=4x4`; read the sheets as images.
5. Compare frames and transcript with the video's own numbers; state limits. Keep raw videos local; save analysis only.
Paid per-video analysis (e.g. vidIQ) only if local analysis fails and the user approves the spend.

## Phase 2: interview
Show the patience note from the `content-agent` skill, then use grilling. Never ask niche, audience or style: derive them and confirm in one line. Ask about: intent and ambition (what the reputation should open), what they want to convert followers into, time and budget limits, posting volume they believe in, off-limits (claims, copying, personal-life sharing, collaborations), success and failure videos they are proud of or hate, and what pattern of success they want (one rule or a portfolio).
Output: `dna/creator-dna.md` (identity, vision, off-limits, constraints). The user confirms it before phase 3.
At the end of the phase, follow the `examples` skill.
