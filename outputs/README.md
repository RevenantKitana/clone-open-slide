# Local Output Directory (`outputs/`)

Thư mục này quản lý toàn bộ nội dung được tạo ra (generated content), kịch bản, storyboard, audio/voiceover, ảnh frames và video thành phẩm.

---

## 📁 Cấu Trúc Dự Án Chuẩn (Chuẩn hóa theo Pipeline 1-5)

Mỗi khi tạo nội dung cho một chủ đề mới, tạo thư mục theo định dạng: `outputs/<ten-chu-de-slug>/` với 5 bước được phân định rõ ràng:

```
outputs/
├── README.md                      # Tài liệu hướng dẫn cấu trúc này
├── _template/                     # Cấu trúc mẫu chuẩn
│   ├── 1-scripts/
│   ├── 2-storyboards/
│   ├── 3-audio/
│   ├── 4-frames/
│   └── 5-videos/
│
└── <ten-chu-de-slug>/             # Thư mục cho từng sản phẩm nội dung cụ thể
    ├── 1-scripts/                 # Kịch bản thô (.md), kịch bản voiceover/teleprompter (.txt)
    │   ├── script.md
    │   └── voiceover_script.txt
    ├── 2-storyboards/             # Manifest JSON & Director Canvas HTML (9:16 hoặc 16:9)
    │   ├── storyboard.json
    │   └── director-canvas.html
    ├── 3-audio/                   # Audio TTS từng scene (.wav/.mp3), merged audio
    │   ├── scene_01.wav
    │   ├── scene_02.wav
    │   └── full_voiceover.wav
    ├── 4-frames/                  # Ảnh chụp màn hình từng phân cảnh (1080x1920)
    │   ├── scene_01.png
    │   ├── scene_02.png
    │   └── ...
    └── 5-videos/                  # Video xuất bản hoàn thiện (.mp4)
        └── final_9x16.mp4
```

---

## 🚀 Quy Trình Sinh Nội Dung (Pipeline)

| Bước | Thư mục | Định dạng file | Mục đích |
| :--- | :--- | :--- | :--- |
| **1** | `1-scripts/` | `.md`, `.txt` | Kịch bản gốc, prompt, phân đoạn thoại voiceover & teleprompter. |
| **2** | `2-storyboards/` | `.json`, `.html` | Cấu trúc phân cảnh (`storyboard.json`) và HTML Director Canvas preview thời gian thực. |
| **3** | `3-audio/` | `.wav`, `.mp3` | File đọc giọng TTS từng phân cảnh và file ghép âm thanh tổng. |
| **4** | `4-frames/` | `.png`, `.jpg` | Frame hình ảnh chụp tự động bằng Playwright từ Canvas. |
| **5** | `5-videos/` | `.mp4`, `.mov` | Video hoàn thiện cuối cùng kết hợp Frames + Audio qua FFmpeg. |

---

## 💡 Ưu điểm

- **Trực quan tức thì**: Mở `outputs/` là thấy ngay danh sách các dự án và từng giai đoạn sản xuất.
- **Tách biệt hoàn toàn**: Không làm rác mã nguồn gốc của framework open-slide.
- **Tự động hóa an toàn**: Gitignore đã được cấu hình để không commit các file media dung lượng lớn (video/audio) lên repository.
