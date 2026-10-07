# Quy Tắc Độ Phủ Lời Thoại vs Nội Dung Hiển Thị (Voiceover & Content Coverage Rule)

Quy tắc này áp dụng cho toàn bộ quy trình biên soạn kịch bản (`1-scripts/`), sinh storyboard (`2-storyboards/`), và tạo audio thuyết minh (`3-audio/`) trong các dự án sinh nội dung bài giảng / video shorts.

---

## 1. Nguyên Tắc Cốt Lõi: Thoại >= Content Hiển Thị

> **Công thức chuẩn**: `Lời thoại (Voiceover / Teleprompter) >= Nội dung hiển thị trên màn hình (On-Screen Content)`

- **Bao phủ 100% (Full Coverage)**: Toàn bộ tiêu đề, phân mục, ý chính trong các thẻ (cards), câu trích dẫn ngữ liệu thơ văn, các phương án trắc nghiệm (A, B, C, D), giải thích đáp án và các lưu ý trên màn hình **PHẢI** được đọc hoặc nhắc đến tường minh trong lời thoại.
- **Không bỏ sót (Zero Omission)**: Tuyệt đối không để màn hình hiện 3 ý / 4 phương án / 1 đoạn trích dẫn dài mà lời thoại lại chỉ đọc lướt 1 ý ngắn rồi chuyển cảnh.
- **Mở rộng & Diễn giải tự nhiên (Expansion & Context)**: Lời thoại không chỉ đọc nguyên văn mà cần có lời dẫn dắt sư phạm, phân tích mở rộng ngữ cảnh, tạo cảm xúc và sự liền mạch cho người học/người xem.

---

## 2. Tiêu Chí Đồng Bộ Chi Tiết

| Thành phần hiển thị | Yêu cầu đối với Lời thoại (Voiceover) |
| --- | --- |
| **Tiêu đề / Badge** | Lời thoại phải xướng tên tiêu đề và phân mục bài học để định hướng người nghe. |
| **Thẻ nội dung (Cards / List)** | Đọc và giải thích đầy đủ từng ý/thành tố trong thẻ, không bỏ sót gạch đầu dòng nào. |
| **Ngữ liệu / Trích dẫn (Quotes)** | Đọc rõ ràng trọn vẹn câu thơ/câu văn trích dẫn làm ngữ liệu phân tích. |
| **Câu hỏi & Trắc nghiệm (Quiz)** | Đọc câu hỏi, đọc các phương án chọn lựa chính (A, B, C, D) và giải thích tại sao đúng/sai. |
| **Điền từ / Thực hành** | Đọc câu mẫu, nêu các từ khóa trong ngân hàng từ và công bố kết quả hoàn chỉnh. |
| **Lưu ý / Bẫy đề thi** | Đọc rõ từng lỗi sai / bẫy đề thi cần tránh để khắc sâu bài học. |

---

## 3. Khớp Thời Lượng & Tốc Độ Đọc (Pacing & Duration)

- Tốc độ đọc chuẩn tiếng Việt bài giảng / giáo dục: **140 – 160 từ / phút** (~2.3 – 2.6 từ / giây).
- Thời lượng mỗi cảnh (`duration` trong JSON/HTML) phải được tính toán tương ứng với độ dài lời thoại:
  - Cảnh 15–20 từ: ~7–9 giây.
  - Cảnh 25–35 từ: ~10–14 giây.
  - Cảnh 40–60 từ: ~15–22 giây.

---

## 4. Phạm Vi Áp Dụng & Tránh Xung Đột

- Quy tắc này chỉ điều chỉnh nội dung sư phạm, kịch bản thuyết minh và dữ liệu storyboard trong thư mục `outputs/`.
- Không làm thay đổi hay xung đột với các quy tắc kỹ thuật mã nguồn core của framework (`packages/core`, `packages/cli`, quy tắc Biome linter, changeset).
