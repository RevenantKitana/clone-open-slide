# Quy Tắc Tệp Canvas HTML Độc Lập Hoàn Toàn (100% Standalone Self-Contained)

Quy tắc này quy định tiêu chuẩn kỹ thuật bắt buộc khi tạo bất kỳ tệp HTML Canvas / Storyboard nào trong thư mục `outputs/` hoặc khi bàn giao sản phẩm cho người dùng.

---

## 1. Nguyên Tắc "Zero External File Dependencies" (Không phụ thuộc tệp ngoài)

> **Yêu cầu cốt lõi**: Mỗi tệp HTML Canvas (`director-canvas.html`, `canvas-16x9-*.html`, `canvas-9x16-*.html`) phải là một thực thể hoàn chỉnh độc lập 100%. Người nhận có thể sao chép riêng lẻ duy nhất 1 tệp HTML gửi qua Zalo, Email, Telegram, Google Drive hoặc USB và mở bằng cách click đúp chuột (`file:///...`) mà **KHÔNG CẦN Web Server** và **KHÔNG BỊ LỖI**.

### Yêu Cầu Kỹ Thuật:
1. **Inline CSS đầy đủ**:
   - Toàn bộ biến màu, tokens thiết kế (`:root`), font chữ, layout và các class component (`.content-card`, `.quote-box`, `.badge-jade`, `.hero-glow-title`...) **PHẢI** được khai báo trực tiếp bên trong thẻ `<style>` của chính file đó.
   - **KHÔNG** sử dụng đường dẫn tương đối `<link rel="stylesheet" href="../../../main.css" />` đơn độc mà không có fallback inline styles.
2. **Inline Dữ liệu & JavaScript**:
   - Toàn bộ dữ liệu các phân cảnh (tiêu đề, nội dung, lời thoại, thời lượng, cấu trúc html) **PHẢI** được nhúng trực tiếp dạng biến JavaScript (`const STORYBOARD = ...` / `const SCENES = ...`).
   - **TUYỆT ĐỐI KHÔNG** dùng lệnh `fetch('storyboard.json')` để tải dữ liệu vì trình duyệt sẽ chặn CORS khi mở file cục bộ (`file:///`).
3. **Typography An Toàn**:
   - Khai báo phông chữ chuẩn Google Fonts (`Be Vietnam Pro`, `JetBrains Mono`) kèm fallback font hệ thống rõ ràng (`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`).

---

## 2. Nguyên Tắc "100% Real Pedagogical Content" (Không để văn bản giữ chỗ)

1. **Tuyệt đối không dùng vòng lặp placeholder** (ví dụ: `Phân cảnh TikTok số ${i}` hay `Trang bài giảng số ${i}`).
2. **Mọi phân cảnh từ 1 đến N** đều phải chứa đầy đủ:
   - Nội dung bài học thật (Khái niệm, công thức, bảng đối chiếu, câu hỏi trắc nghiệm, đáp án, bẫy sai, bài tập về nhà).
   - Lời thoại thuyết minh hoàn chỉnh có ngữ nghĩa rõ ràng, tương ứng với nội dung hiển thị trên màn hình.
   - Layout hoàn chỉnh theo đúng chuẩn hệ thống *Giấy & Mực (Paper & Jade)*.

---

## 3. Danh Sách Bộ 3 Canvas Chuẩn

Trong mọi dự án xuất bản (`outputs/<project-slug>/2-storyboards/`), bắt buộc cung cấp đủ bộ 3 file canvas độc lập:
1. **`director-canvas.html`**: Canvas tổng hợp của Đạo diễn (hỗ trợ chuyển đổi 16:9 $\leftrightarrow$ 9:16, Sidebar danh sách cảnh, Teleprompter, Safe Zone, Clean Recording Mode).
2. **`canvas-16x9-bai-giang.html`**: Canvas chuyên dụng 16:9 Full HD (1920×1080) cho video bài giảng và trình chiếu.
3. **`canvas-9x16-tiktok.html`**: Canvas chuyên dụng 9:16 (1080×1920) cho video ngắn TikTok, YouTube Shorts, Reels.
