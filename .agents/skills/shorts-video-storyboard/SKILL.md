---
name: shorts-video-storyboard
description: Use this skill when the user wants to convert a markdown script or content document into a 9:16 vertical video storyboard (TikTok, YouTube Shorts, Reels) with scene segmentation, durations, voiceover teleprompter cues, safe zones, and a JSON manifest. Triggers on requests like "tạo video storyboard từ kịch bản", "tạo video ngắn 9:16", "chuyển kịch bản thành storyboard", "make short-form video scenes".
---

# Shorts & Video Storyboard Workflow (9:16 Vertical Video Canvas)

This skill standardizes the end-to-end workflow of transforming raw educational or promotional markdown scripts into a **Pre-production Vertical Video Canvas (9:16)** ready for automated video recording / rendering.

---

## Deliverables & Output Directory Structure

Tất cả output sinh nội dung **PHẢI** được lưu vào thư mục `outputs/<project-slug>/` theo chuẩn 5 thư mục:

```
outputs/<project-slug>/
├── 1-scripts/           # Kịch bản gốc, prompt, teleprompter voiceover text
├── 2-storyboards/       # storyboard.json & <name>-storyboard.html (Director Canvas)
├── 3-audio/             # File audio TTS theo từng scene & file voiceover gộp
├── 4-frames/            # Ảnh chụp frame phân cảnh 1080x1920 (PNG)
└── 5-videos/            # Video hoàn thiện (.mp4 9:16)
```

Whenever the user asks to generate a video storyboard from a script, the agent must produce:

1. **`outputs/<slug>/2-storyboards/storyboard.json`** — Structured machine-readable manifest containing:
   - `aspectRatio`: `"9:16"`
   - `resolution`: `{ "width": 1080, "height": 1920 }`
   - `safeZones`: Top (240px), Bottom (380px), Right (120px)
   - `scenes`: Array of `{ id, title, duration (seconds), startTime, voiceover, visualCues }`
   - `totalDuration`: Total video duration in seconds (typically 50s–80s for short-form).

2. **`outputs/<slug>/2-storyboards/<name>-storyboard.html`** (or `director-canvas.html`) — Self-contained Interactive Director Canvas with:
   - **1080 × 1920 Stage**: Fixed 9:16 canvas centered and scaled to viewport.
   - **TikTok / Reels Safe Zone Overlay** (toggleable via UI button `Safe Zone`).
   - **Auto-Play Simulation**: Plays scene-by-scene with real-time progress bar and seconds counter.
   - **Teleprompter Subtitles Overlay** (`#canvas-subtitles`).
   - **Scene Director Sidebar**: Lists all scenes, click-to-seek, and full voiceover script.
   - **Clean Render Mode** (Press `C`): Hides all editor UI for clean recording.
   - **Global Automation API**: Exposes `window.VideoAPI = { getScenes, seekTo, play, pause, ... }`.

---

## 9:16 Safe Zone & Layout Discipline

Short-form platforms (TikTok, Instagram Reels, YouTube Shorts) place UI controls over the video:
- **Top 160px – 240px**: Obscured by search bar / header / notch ➔ Keep important text below 240px.
- **Bottom 280px – 380px**: Obscured by caption, username, sound title, progress bar ➔ Keep important text above 380px from bottom.
- **Right 120px**: Obscured by Like, Comment, Share, Bookmark buttons ➔ Keep 120px padding from the right edge.
- **Content Padding**: `padding: 180px 70px 320px 70px;` is the standard safe padding.

---

## Scene Pacing Rules

- **Hook (Scene 1)**: 4s – 6s (Big bold headline, immediate curiosity trigger).
- **Core Content Scenes**: 5s – 8s each (Single idea per scene, vertical card stacks).
- **Interactive / Quiz Scenes**: 6s – 8s each (Question on top, stacked options with highlight).
- **Outro & CTA (Final Scene)**: 4s – 6s (Key takeaway + Call to Action: Like, Save, Follow).
- **Total Duration**: 50s to 75s (Optimized for short-form retention).

---

## Color & Typography Palette

- **Canvas Background**: Deep dark navy/black (`#0A0E1A`).
- **Surface Cards**: Contrast midnight blue (`#121829` with `border: 2px solid #1F293D`).
- **Accents**: Neon Cyan (`#25F4EE` or `#38BDF8`), TikTok Pink/Red (`#FE2C55`), Amber (`#F59E0B`), Emerald (`#10B981`), Purple (`#A855F7`).
- **Type Scale**:
  - Hero Titles: 72px – 84px (900 weight, gradient text).
  - Section Titles: 48px – 56px (800 weight).
  - Quotes: 36px – 42px (italic, 6px left border).
  - Body & Cards: 26px – 32px.
