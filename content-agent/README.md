# content-agent

A Claude Code plugin that acts as a personal content agent for short-video creators. It works for any niche and any language (it asks you first). Arabic users: the agent answers in your language and dialect once you tell it.

## What it does
Phases (each ends with worked examples, see below):
0. Source qualification: which of your tools and data sources work.
1. Extraction: your own numbers, audience, best and worst videos, your writing voice.
2. Interview (grilling): intent, ambition, off-limits, constraints.
3. Competitive landscape: close accounts, patterns that earn views, verified gaps.
4. Strategy: angle, pattern portfolio, hook rules, posting guide, targets.
5. Learning plan: practice-based, weekly cycle.
6. Publishing support: captions, hashtags, keywords. You post yourself.
7. Closed loop: short weekly review, changes proposed with evidence, you decide.

## What it never does
- It never posts, schedules, sends or spends money for you without an explicit yes.
- It never enters passwords or keys, and never reads or copies secrets.
- It never tells you how to film or edit (optional module, off by default, only offered after asking you).
- It never claims results you did not get, and never copies another creator's video end to end. Inspiration means taking a mechanism, not the content.

## Install
In Claude Code (2.1.275 or later):
```
/plugin marketplace add hamza-tricking/content-plugin
/plugin install content-agent@content-plugin
```
Or from a downloaded copy: `claude --plugin-dir <folder>`.

Then:
1. Install the plugin folder in Claude Code (local plugin path or the zip contents).
2. Run `/content-agent:start`. On first run it runs the `setup` skill:
   - checks your machine (Python, ffmpeg, yt-dlp, faster-whisper, GPU),
   - shows the list of what is missing, with size,
   - installs after ONE approval from you, skipping what is installed,
   - looks at what you already have in Claude (CLAUDE.md, memory, skills, connectors) and asks per source before using it.

## Optional tools (the agent works without them and logs what is missing)
| Tool | Adds | Cost |
|---|---|---|
| Claude in Chrome | reading your logged-in Instagram/TikTok pages and analytics | free |
| Metricool connector | posting-time and account metrics | depends on your plan |
| vidIQ connector | Instagram own-account insights, outlier search | credits (the agent asks before spending) |
| Google Drive connector | backup of your files, uploaded once at the end if you agree | free |

## Your data
Everything is created in your own working folder (`vault/`, `strategy/`, `dna/`). Nothing personal is shipped with the plugin.
