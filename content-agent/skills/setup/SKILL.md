---
name: setup
description: First-run setup for the content agent. Checks the user's machine, lists missing tools (Python, ffmpeg, yt-dlp, faster-whisper), installs them after one approval, and discovers what the user already has in Claude (CLAUDE.md, memory, skills, connectors) with consent per source. Use on first run or when a tool is missing.
---

# Setup

Never install silently. Sequence: check, show the list, ask ONE approval, install, verify.

## 1. Check the machine (read-only)
Report OS, free disk, RAM, and whether each exists:
- Python 3.10+ (`python --version`), pip
- `ffmpeg` and `ffprobe`
- `yt-dlp` (`python -m yt_dlp --version`)
- `faster-whisper` (`python -c "import faster_whisper"`) and `numpy`
- GPU (NVIDIA: `nvidia-smi`). If CUDA libs are missing, use CPU int8; do not block.

## 2. Show the missing list
Table: tool, why it is needed (local video analysis: download a reel the user approved, transcribe, extract frames), approximate size, install command. Ask one question: "Install all of these?" Skip what is installed.

| Tool | Windows | macOS | Linux |
|---|---|---|---|
| Python | `winget install Python.Python.3.12` | `brew install python` | `apt install python3 python3-pip` |
| ffmpeg | `winget install Gyan.FFmpeg` | `brew install ffmpeg` | `apt install ffmpeg` |
| yt-dlp, faster-whisper, numpy | `python -m pip install -U yt-dlp faster-whisper numpy` | same | same |

Commands are defaults; adapt to what the machine has. Do not run anything the user has not approved. Whisper model `medium` downloads on first use (about 1.5 GB): include it in the approval list.

## 3. Verify
Run each version/import check again and report what works. Record results in `content-agent-state.md`. If something fails, log it in `gaps.md` and continue with a lower layer.

## 4. Discover what the user already has in Claude (consent per source)
List what exists, then ask per source whether the agent may read it. Never read without a yes. Never copy keys, tokens, passwords or cookies; if a file contains them, skip those lines and say so.
- Global and project `CLAUDE.md`
- Memory folder
- Installed skills (look for a writing-style skill, video/editing skills)
- Connected connectors (Metricool, vidIQ, Drive, Chrome, others)
- Files in the working folder (exports, analytics, past scripts)
For each approved source, extract only content-relevant facts (niche hints, audience, language, past preferences, off-limits) into `sources.md` with the source named, so the user can check and correct. The user starts from zero on the agent's own data, but not blank on what Claude already knows about them.

## 5. Optional tools
Explain each in one line (what it adds, cost) and let the user choose: Claude in Chrome (read logged-in pages), Metricool, vidIQ, Drive. The agent works without them.
