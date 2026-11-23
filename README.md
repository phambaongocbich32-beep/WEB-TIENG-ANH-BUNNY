# Bunny English World - Little Learners

**Listen • Speak • Read • Write • Play.** Web học tiếng Anh giọng Mỹ (en-US) cho bé 5 tuổi, với hai nhân vật Bunny và Teacher Emma.
Chạy hoàn toàn trên trình duyệt, không cần backend, không cần tài khoản, triển khai được trên GitHub Pages.

## Cấu trúc thư mục

```
index.html            Trang chính
css/style.css         Giao diện (màu pastel, nút lớn, responsive)
js/data-*.js          DỮ LIỆU bài học (tách khỏi logic, dễ bổ sung)
  data-vocab.js         38 chủ đề, 335 từ (hình emoji, nghĩa tiếng Việt, câu ví dụ)
  data-curriculum.js    36 tuần / 3 học kỳ (từ vựng, mẫu câu, câu hỏi nói, truyện, tình huống)
  data-speaking.js      12 tình huống hội thoại, mỗi tình huống 6 lượt
  data-stories.js       20 truyện gốc (4 cấp độ), 6 bài hát/chant, thông tin khủng long
  data-phonics.js       8 cấp độ phonics, 36 nhóm bài
  data-strokes.js       Nét viết 52 chữ cái (hoa + thường)
js/core.js            Lưu tiến độ, giọng đọc, micro, nhân vật, trò chơi trắc nghiệm dùng chung
js/mod-*.js           Các màn hình: vocab, phonics, speaking, listening, reading, writing, games
js/app.js             Điều hướng, trang chủ, Daily Lesson, My Progress, Parent Corner
audio/manifest.json   Danh sách file ghi âm (tùy chọn, xem audio/README.md)
sw.js                 Cache để học được khi mất Internet (cần https hoặc localhost)
```

## Chạy thử trên máy
Mở `index.html` bằng Chrome/Safari (chạy được cả khi mở trực tiếp file). Để dùng micro và chế độ offline, nên chạy qua web server:
`python3 -m http.server 8000` rồi mở `http://localhost:8000`.

## Đưa lên GitHub Pages
1. Giải nén file ZIP. Tạo repository mới trên GitHub (Public), ví dụ `bunny-english`.
2. Bấm **Add file → Upload files**, kéo TOÀN BỘ nội dung thư mục (index.html, css, js, audio, sw.js, manifest.webmanifest, .nojekyll, README.md) vào. Giữ nguyên cấu trúc thư mục. Bấm **Commit changes**.
3. Vào **Settings → Pages**, Source: **Deploy from a branch**, branch `main`, thư mục `/ (root)`, **Save**.
4. Sau 1-2 phút mở `https://TEN-GITHUB.github.io/bunny-english/`. Trên iPad/điện thoại có thể chọn **Thêm vào Màn hình chính**.

## Cách dùng
- Lần đầu mở: nhập tên bé. Bấm **Continue Learning** để học tiếp, hoặc **Daily Lesson** để xem bản đồ 6 phần của tuần (Warm-up, Vocabulary, Sentence Builder, Listening & Speaking, Reading & Phonics, Play & Review).
- Mọi âm thanh chỉ phát sau khi bé bấm. Bấm 🔊 để nghe lại, 🐢 để nghe chậm.
- **Parent Corner** (cần giải phép tính cộng): lộ trình 36 tuần, báo cáo tiến độ, từ cần ôn, gợi ý đồng hành, cài đặt giọng/tốc độ/micro, sao lưu và khôi phục, kiểm tra thiết bị.

## Giọng đọc
- Teacher Emma dùng giọng TTS của thiết bị, ưu tiên giọng nữ en-US. **Đây là giọng tổng hợp, không phải người thật.**
- Chất lượng phụ thuộc thiết bị: Chrome/Edge (Google US English, Microsoft Aria/Jenny Natural), iPhone/iPad/Mac (Samantha/Ava, tải bản Enhanced). Chọn giọng ở Parent Corner → Cài đặt.
- Ưu tiên audio thu âm: đặt file vào `audio/` và khai báo trong `audio/manifest.json` (xem `audio/README.md`). Nếu không có, app dùng giọng hệ thống.
- Nếu thiết bị không có giọng tiếng Anh, app hiện thông báo và vẫn hiển thị chữ/hình.

## Micro và nhận diện giọng nói
- Dùng Web Speech API khi trình duyệt hỗ trợ (Chrome, Edge, Safari). Chỉ mở khi bé bấm 🎤; không ghi âm nền; app không lưu âm thanh.
- Chrome/Safari thường gửi âm thanh tới dịch vụ của Google/Apple để chuyển thành chữ; app có thông báo này cho phụ huynh trước lần dùng đầu tiên.
- App chỉ **so khớp từ khóa** bé nói với các đáp án hợp lý (không chấm điểm phát âm). Bé nói cách diễn đạt khác nhưng đúng ý vẫn được công nhận.
- Nếu không nhận diện được, bé thử lại hoặc chọn đáp án. Có chế độ tắt micro hoàn toàn.

## Phonics
Phát âm chuẩn của từng âm (ví dụ /b/ không có "uh") cần file ghi âm. Khi chưa có, Emma đọc tên chữ cái và từ khóa (ví dụ "B. ball.") kèm ký hiệu IPA trên màn hình; app **không** đọc các chuỗi tự chế như "buh". Có thể thêm file `audio/phonemes/…` (xem audio/README.md).

## Nội dung và bản quyền
Toàn bộ từ vựng, câu, hội thoại, truyện và bài hát được viết riêng cho dự án này, lấy cảm hứng về phương pháp (phonics có trình tự, Pre-A1, đọc theo cấp độ, giao tiếp thực tế). Không sao chép nội dung của Abeka, Cambridge, Reading Eggs hay các giáo trình đã cung cấp. Hình minh họa là emoji và SVG tự vẽ.

## Thêm nội dung
- Thêm từ: sửa `js/data-vocab.js` (định dạng `từ:emoji:nghĩa:câu`).
- Thêm truyện: thêm một dòng vào `js/data-stories.js`.
- Thêm tình huống: thêm vào `js/data-speaking.js`.
- Không cần sửa code giao diện.

## Lưu tiến độ
Lưu trong `localStorage` của trình duyệt (không tài khoản). Sao lưu/khôi phục bằng file JSON ở Parent Corner.


## v3: Meet the World
- Works in the browser: 30 topics, Speak-Check-Improve, Listen-Think-Speak, Vocabulary Universe, 12-area home, YouTube search links (Parent Corner -> Video).
- Needs a server you run: AI Foreign Friends (see server/README.md).
- Not available: real foreign teachers and video calls ("Coming soon").
- Voice: the app ranks en-US natural voices first. Best free result: open in Microsoft Edge ("Microsoft Aria/Jenny Online (Natural)").
