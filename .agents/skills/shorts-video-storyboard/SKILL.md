---
name: shorts-video-storyboard
description: Use this skill when the user wants to convert a markdown script or content document into a 9:16 vertical video storyboard (TikTok, YouTube Shorts, Reels) or 16:9 lecture video canvas, with standalone self-contained HTML viewers, batch TTS audio normalization ($[Folder] / [Text n]), safe zones, and JSON manifests.
---

# Shorts & Video Storyboard Workflow (16:9 Lecture & 9:16 Vertical Video)

This skill standardizes the end-to-end workflow of transforming raw educational or promotional markdown scripts into **100% Standalone Interactive Video Canvases** and **Batch TTS Audio Packages** ready for automated video recording, voice generation, and rendering.

---

## 📁 1. Deliverables & Output Directory Structure

Tất cả output sinh nội dung **PHẢI** được lưu vào thư mục `outputs/<project-slug>/` theo chuẩn 5 thư mục:

```
outputs/<project-slug>/
├── 1-scripts/           # Kịch bản gốc (JSON / TXT), teleprompter voiceover text
├── 2-storyboards/       # storyboard.json, director-canvas.html, canvas-16x9-*.html, canvas-9x16-*.html
├── 3-audio/             # audio_batch_input.txt ($[Folder] / [Text n]), WAVs, mapping.txt, info.json
├── 4-frames/            # Ảnh chụp frame phân cảnh (PNG 1920x1080 & 1080x1920)
└── 5-videos/            # Video hoàn thiện (.mp4 16:9 & 9:16)
```

---

## 🖥️ 2. Standalone Self-Contained Canvas Rules ("Zero External Dependencies")

Tuân thủ nghiêm ngặt theo `.agents/rules/standalone-canvas-rule.md`:

1. **Hoàn toàn độc lập (100% Self-Contained)**:
   - Toàn bộ CSS (màu sắc, typography, card, nút bấm) **PHẢI** được nhúng trực tiếp trong thẻ `<style>`.
   - Toàn bộ dữ liệu các phân cảnh và logic điều khiển **PHẢI** được nhúng trực tiếp dạng biến JavaScript (`const STORYBOARD = ...`).
   - **TUYỆT ĐỐI KHÔNG** dùng `fetch('storyboard.json')` để tránh lỗi bảo mật CORS khi mở file cục bộ (`file:///`).
   - Người dùng có thể copy riêng lẻ bất kỳ file HTML nào gửi cho người khác và mở trực tiếp bằng click đúp chuột trên mọi thiết bị mà không cần web server.

2. **100% Real Pedagogical Content (Không dùng văn bản giữ chỗ)**:
   - Mọi phân cảnh từ 1 đến N đều phải render đầy đủ nội dung bài học thật (tiêu đề, thẻ card, công thức, bảng đối chiếu, trắc nghiệm, bẫy sai, đáp án, bài tập về nhà) và lời thoại thuyết minh chi tiết.

3. **Bộ 3 Canvas Chuẩn**:
   - `director-canvas.html`: Canvas Đạo diễn chuyển đổi linh hoạt 16:9 $\leftrightarrow$ 9:16, kèm sidebar, timeline, teleprompter, safe zone và clean recording mode.
   - `canvas-16x9-bai-giang.html`: Canvas chuyên dụng bài giảng 16:9 Full HD (1920×1080).
   - `canvas-9x16-tiktok.html`: Canvas chuyên dụng video ngắn 9:16 (1080×1920) kèm Safe Zone.

---

## 🎙️ 3. Chuẩn Hóa Audio TTS Batch (`$[Tên_Folder]` & `[Text n]`)

Tuân thủ nghiêm ngặt theo `.agents/rules/audio-tts-batch-rule.md`:

1. **Cú pháp thư mục chuỗi dự án**: `$[Tên_Folder]` (ví dụ: `$[BPTT_So_Sanh_16x9_Bai_Giang]`, `$[BPTT_So_Sanh_9x16_TikTok]`).
2. **Cú pháp phân đoạn batch**: `[Text 1]`, `[Text 2]`... tương ứng từng slide/phân cảnh để TTS sinh các file `<Tên_Folder>_01.wav`, `<Tên_Folder>_02.wav`...
3. **Làm sạch văn bản cho TTS**:
   - Loại bỏ toàn bộ thẻ kỹ thuật `[Cue ...]` và `[pause:...]`, thay bằng dấu câu tự nhiên (`.`, `,`, `...`, `:`, `;`, `-`).
   - Thuần Việt hóa và phiên âm phát âm rõ ràng cho TTS (ví dụ: `A bằng Bê`, `không phẩy hai mươi lăm điểm`, `lớp mười`).
4. **Tệp bắt buộc trong `3-audio/`**:
   - `audio_batch_input.txt`: Tệp master nạp vào TTS engine.
   - `16x9_bai_giang_audio.txt` & `9x16_tiktok_audio.txt`: Tệp riêng lẻ theo từng tỉ lệ khung hình.
   - `info.json`: Metadata lưu chi tiết số ký tự, thời lượng ước tính và file mapping.

---

## 📱 4. 9:16 Safe Zone & Layout Discipline

Short-form platforms (TikTok, Instagram Reels, YouTube Shorts) place UI controls over the video:
- **Top 160px – 240px**: Obscured by search bar / header / notch ➔ Keep important text below 240px.
- **Bottom 280px – 380px**: Obscured by caption, username, sound title, progress bar ➔ Keep important text above 380px from bottom.
- **Right 120px**: Obscured by Like, Comment, Share, Bookmark buttons ➔ Keep 120px padding from the right edge.
- **Content Padding**: `padding: 180px 70px 320px 70px;` is the standard safe padding.

---

## 🎨 5. Color & Typography Palette (Default `main.css`)

- **Default Design System**: All storyboards, HTML canvases, and generated preview slides **MUST DEFAULT** to the design system in `main.css` and `.agents/rules/nguvan-design-system-rule.md` unless explicitly requested otherwise.
- **Standard Fonts**: **`Be Vietnam Pro`** (Google Fonts) kết hợp **`JetBrains Mono`** cho số/mã.
- **Palette Giấy & Mực**:
  - Background: `--cream` (`#FAF7F0`) / `--cream-2` (`#F0EADD`).
  - Cards: `--white` (`#FFFFFF`), viền `--paper-line` (`#E5DECF`), viền ngọc `--jade` (`#3CA57A`).
  - Text: `--ink` (`#1A1A1A`), `--ink-2` (`#514C44`), `--ink-3` (`#7C756A`).
  - Accents: `--jade` (`#3CA57A`), `--accent` (`#E8A24A`), `--sage` (`#A8C9B8`).
