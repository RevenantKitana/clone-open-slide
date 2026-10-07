# Quy Tắc Chuẩn Hóa Kịch Bản Audio TTS Batch ($[Tên_Folder] & [Text n])

Quy tắc này quy định chuẩn định dạng kịch bản giọng đọc (Voiceover / Text-to-Speech) phục vụ nạp vào hệ thống TTS Batch Generator để tạo âm thanh tự động cho toàn bộ dự án video bài giảng (16:9) và video ngắn (9:16).

---

## 1. Cú Pháp Đầu Vào (Input Syntax) Bắt Buộc

### 1.1. Thẻ Thư Mục Dự Án (`$[Tên_Folder]`)
- Dùng cú pháp `$[Tên_Folder]` ở đầu mỗi khối kịch bản để chỉ định thư mục lưu trữ đầu ra tương ứng.
- Có thể kết hợp nhiều dự án trong **1 tệp input duy nhất** (Batch Multi-Project), hệ thống sẽ tự động tách và xử lý lần lượt theo từng thư mục.
- **Ví dụ**:
  ```text
  $[BPTT_So_Sanh_16x9_Bai_Giang]
  [Text 1] Nội dung lời thoại slide 1...
  [Text 2] Nội dung lời thoại slide 2...

  $[BPTT_So_Sanh_9x16_TikTok]
  [Text 1] Nội dung lời thoại phân cảnh 1...
  [Text 2] Nội dung lời thoại phân cảnh 2...
  ```

### 1.2. Nhãn Phân Đoạn Từng Câu / Slide (`[Text n]`)
- Mỗi phân đoạn audio độc lập bắt buộc bắt đầu bằng nhãn `[Text 1]`, `[Text 2]`, `[Text 3]`...
- Mỗi `[Text n]` sẽ được engine TTS kết xuất thành 1 tệp audio riêng lẻ: `<Tên_Folder>_01.wav`, `<Tên_Folder>_02.wav`...

---

## 2. Quy Chuẩn Xử Lý Văn Bản Tiếng Việt Cho TTS

1. **Bảng mã**: Bắt buộc **UTF-8 có dấu** chuẩn xác.
2. **Ngắt nghỉ & Nhịp điệu tự nhiên**:
   - Sử dụng dấu câu chuẩn (`.`, `,`, `!`, `?`, `...`, `:`, `;`, `-`) để engine TTS điều chỉnh trường độ và độ cao giọng nói.
   - **LOẠI BỎ TOÀN BỘ** các thẻ kỹ thuật dùng cho video/teleprompter như `[Cue 1.1]`, `[pause:500ms]`, `[pause:1000ms]` trong tệp TTS batch để tránh việc TTS phát âm các ký tự này.
3. **Thuần Việt hóa & Phiên âm đọc chuẩn**:
   - Các công thức, ký hiệu toán học / ngữ pháp phải được viết bằng từ tiếng Việt:
     - `A = B` $\rightarrow$ `A bằng Bê`
     - `A ≠ B` $\rightarrow$ `A khác Bê`
     - `B > A` $\rightarrow$ `Bê lớn hơn A`
     - `0.25đ` $\rightarrow$ `không phẩy hai mươi lăm điểm`
     - `0.5đ` $\rightarrow$ `không phẩy năm điểm`
     - `0.75đ` $\rightarrow$ `không phẩy bảy mươi lăm điểm`
     - `90%` $\rightarrow$ `chín mươi phần trăm`
     - `Lớp 10 / THPT` $\rightarrow$ `lớp mười và Trung học phổ thông` (hoặc `lớp 10 và THPT` tùy ngữ cảnh).

---

## 3. Cấu Trúc Đầu Ra Chuẩn (Output Deliverables)

Khi chạy qua TTS Generator, kết quả đầu ra trong thư mục `outputs/` hoặc `outputs/<project-slug>/3-audio/` phải tuân theo cấu trúc:

```
outputs/
├── <Tên_Folder>/
│   ├── <Tên_Folder>_01.wav           # Audio phân đoạn 1
│   ├── <Tên_Folder>_02.wav           # Audio phân đoạn 2
│   ├── ...
│   ├── <Tên_Folder>_n.wav            # Audio phân đoạn n
│   ├── <Tên_Folder>_FULL_MERGED.wav  # Tệp ghép nối trọn vẹn toàn bài (WAV / MP3 / FLAC)
│   ├── <Tên_Folder>_mapping.txt      # Bảng timeline mapping thời gian từng câu
│   └── info.json                     # Metadata chi tiết số từ, thời lượng, trạng thái
```

---

## 4. Danh Mục Tệp Sinh Tự Động Trong Mỗi Dự Án

Mỗi dự án bài giảng trong `outputs/<project-slug>/3-audio/` **BẮT BUỘC** sinh 4 tệp chuẩn:
1. `audio_batch_input.txt`: Tệp Master tổng hợp nạp vào tool TTS (chứa cả 16:9 và 9:16).
2. `16x9_bai_giang_audio.txt`: Tệp riêng bản 16:9 Video bài giảng.
3. `9x16_tiktok_audio.txt`: Tệp riêng bản 9:16 TikTok / Shorts.
4. `info.json`: Tệp lưu trữ thông tin độ dài ký tự, ước tính thời lượng giây và danh sách file mapping.
