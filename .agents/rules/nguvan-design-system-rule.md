# Quy Tắc Thiết Kế Mặc Định: Hệ Thống Giấy & Mực (Paper & Jade) — main.css

Quy tắc này quy định chuẩn giao diện mặc định cho toàn bộ các sản phẩm nội dung: Slide bài giảng (`slides/`), Kịch bản & Storyboard video 16:9 & 9:16 (`outputs/`), và các trang tương tác trong dự án.

---

## 1. Nguyên Tắc Áp Dụng Mặc Định

> **Quy định**: Nếu người dùng không chỉ định một bảng màu/phong cách giao diện cụ thể khác, hệ thống **BẮT BUỘC MẶC ĐỊNH** áp dụng toàn bộ hệ thống màu sắc, typography và class giao diện từ file `main.css` (Phong cách Thư pháp & Giảng dạy Ngữ Văn: *Giấy & Mực — Jade & Amber*).

---

## 2. Bảng Màu Chuẩn (Design Tokens từ `main.css`)

| Nhóm màu | Biến CSS | Mã Hex / Giá trị | Ý nghĩa & Vị trí sử dụng |
| :--- | :--- | :--- | :--- |
| **Giấy mộc (Nền)** | `--cream`<br/>`--cream-2`<br/>`--cream-3` | `#faf7f0`<br/>`#f0eadd`<br/>`#e7decc` | Nền canvas, nền khối trích dẫn, bề mặt phụ. |
| **Đường vân giấy** | `--paper-line`<br/>`--paper-line-2` | `#e5decf`<br/>`#d6ccb6` | Đường viền card, dải phân cách, viền ô trống. |
| **Mực tàu (Chữ)** | `--ink`<br/>`--ink-2`<br/>`--ink-3`<br/>`--ink-faint` | `#1a1a1a`<br/>`#514c44`<br/>`#7c756a`<br/>`#aba396` | Màu chữ chính, tiêu đề, nội dung phụ, chú thích. |
| **Ngọc Bích (Chính)** | `--jade`<br/>`--jade-deep`<br/>`--jade-pale`<br/>`--jade-dark` | `#3ca57a`<br/>`#2a8167`<br/>`#dceae1`<br/>`#14432f` | Nút hành động, viền nổi bật, huy hiệu chuẩn, đáp án đúng. |
| **Hoàng Kim (Điểm nhấn)** | `--accent`<br/>`--accent-deep`<br/>`--accent-pale`<br/>`--accent-text` | `#e8a24a`<br/>`#ce8a33`<br/>`#f7e7cd`<br/>`#8a551a` | Điểm nhấn quan trọng, thẻ bài học, lưu ý bẫy đề thi. |
| **Xanh Trúc (Phụ trợ)** | `--sage`<br/>`--sage-pale`<br/>`--sage-text` | `#a8c9b8`<br/>`#e1ece4`<br/>`#46685a` | Phân mục bài học, huy hiệu phần mở đầu. |
| **Phản hồi (Semantic)** | `--correct` / `--correct-bg`<br/>`--wrong` / `--wrong-bg`<br/>`--warning` / `--warning-bg` | `#2a8167` / `#dceae1`<br/>`#a84b2c` / `#f3e2d6`<br/>`#c58a2e` / `#f5e7cb` | Màu trạng thái đúng, sai, bẫy cảnh báo trong bài tập. |

---

## 3. Typography Bắt Buộc

- **Phông chữ hiển thị & nội dung**: `--font-sans: "Be Vietnam Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;` (Tối ưu 100% không lỗi chân chữ/dấu tiếng Việt).
- **Phông chữ số & mã hiệu**: `--font-mono: "JetBrains Mono", monospace;` (Dùng cho số trang, thời lượng giây, số thứ tự phân cảnh).

---

## 4. Danh Sách Lớp Giao Diện Bắt Buộc Sử Dụng

1. **Khung & Nền Canvas**:
   - `body.theme-paper-mode`: Chế độ giao diện Giấy & Mực mặc định.
   - `.slide-canvas`: Canvas hiển thị phân cảnh (16:9 hoặc 9:16).
2. **Tiêu đề & Huy hiệu**:
   - `.hero-glow-title`: Tiêu đề chính trang Cover với dải gradient mực ngọc.
   - `.hero-subtitle`: Khung tiêu đề phụ với viền hổ phách.
   - `.slide-super-header`: Tên phân mục bài học.
   - `.slide-main-title`: Tiêu đề chính của từng trang bài học.
   - `.badge-jade`, `.badge-accent`, `.badge-sage`, `.mobile-badge`: Huy hiệu phân mục và nhãn thời lượng.
3. **Thẻ thông tin & Trích dẫn**:
   - `.content-card`, `.mobile-card`: Thẻ bài học nền trắng ngà, viền vân giấy mềm mại.
   - `.quote-box`, `.mobile-quote`: Khung trích dẫn thơ văn nền giấy mộc, viền trái ngọc bích 5px.
4. **Quy trình, Công thức & Bài tập**:
   - `.workflow-step`: Hộp quy trình thành tố cấu trúc.
   - `.pyramid-tier`: Hộp bậc thang công thức phân tích 3 tầng.
   - `.quiz-option`, `.quiz-option.correct`: Thẻ phương án trắc nghiệm (A, B, C, D) và trạng thái đúng.
   - `.word-chip`: Thẻ từ khóa trong ngân hàng từ.
   - `.blank-slot`, `.blank-slot.filled`: Ô điền khuyết với nét đứt ngọc bích.
5. **Thuyết minh & Điều khiển**:
   - `.teleprompter-bar`, `.mobile-teleprompter`: Thanh phụ đề thuyết minh tự động.
   - `.btn-theme-toggle`: Nút chuyển đổi phong cách *Giấy & Mực* ↔ *Dạ Kim*.

---

## 5. Áp Dụng Cho Cả 2 Định Dạng (16:9 & 9:16)

- **16:9 (Video Bài Giảng / Trình Chiếu)**: Sử dụng các class `.content-card`, `.quote-box`, `.workflow-step`, `.pyramid-tier`.
- **9:16 (TikTok / Shorts / Reels)**: Sử dụng các class `.mobile-card`, `.mobile-quote`, `.mobile-badge`, `.mobile-teleprompter` kết hợp với Safe Zone (`Top 240px`, `Bottom 380px`, `Right 120px`).
