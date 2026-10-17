# Ôn Thi Tiếng Anh — Website luyện thi tốt nghiệp

Website HTML/CSS/JavaScript thuần, có thể deploy miễn phí trên GitHub Pages. Không cần Node.js hoặc database.

## Chức năng
- Bài tập mỗi ngày: lựa chọn câu theo ngày từ ngân hàng câu hỏi hiện hành.
- Trắc nghiệm: grammar, vocabulary, cloze test, reading; kiểm tra và xem giải thích.
- Sentence transformation: viết lại câu, đối chiếu với đáp án mẫu.
- Thi thử có đồng hồ và lưu kết quả.
- Ôn câu đã làm sai.
- Admin tại tab **⚙ Quản lý câu hỏi**: thêm/sửa/xóa, tìm/lọc, xuất/nhập JSON, khôi phục câu mẫu.
- Có sẵn **65 câu trắc nghiệm và 25 câu viết lại** trong `questions.js`.

## Chạy trên máy
1. Giải nén file ZIP.
2. Mở thư mục `On_Thi_Tieng_Anh` trong VS Code.
3. Nhấp đúp `index.html` để chạy; hoặc dùng extension Live Server.

## Đưa lên GitHub Pages để lấy link public
1. Đăng nhập github.com, tạo repository mới, ví dụ `on-thi-tieng-anh`. Chọn **Public**.
2. Tải lên ba file `index.html`, `questions.js`, `README.md` ở **gốc** repository, không bọc thêm thư mục.
   - Cách nhanh: **Add file → Upload files → Commit changes**.
3. Vào **Settings → Pages**.
4. Dưới **Build and deployment**, chọn **Deploy from a branch**; chọn nhánh `main` và thư mục `/(root)`, rồi **Save**.
5. URL thường có dạng: `https://TEN_GITHUB.github.io/on-thi-tieng-anh/` (thay `TEN_GITHUB` bằng username GitHub). GitHub sẽ hiển thị URL chính thức trong Settings → Pages sau khi triển khai.

## Thêm câu hỏi
Vào tab **⚙ Quản lý câu hỏi** → **+ Trắc nghiệm** hoặc **+ Viết lại** → nhập nội dung → **Lưu câu hỏi**. Các thay đổi được lưu tự động bằng `localStorage` trên trình duyệt đó.

**QUAN TRỌNG VỀ GITHUB PAGES:** GitHub Pages là hosting tĩnh. `localStorage` không đồng bộ giữa các máy, không lưu trực tiếp trên GitHub và không chia sẻ thay đổi của Admin cho người truy cập khác. Chỉnh trên máy A sẽ không xuất hiện trên máy B. Dùng **Xuất JSON** để sao lưu/chuyển máy. Nếu muốn cập nhật ngân hàng câu hỏi cho **tất cả người dùng** qua website công khai, bạn cần sửa `questions.js` và commit lên GitHub, hoặc tích hợp cơ sở dữ liệu/backend (ví dụ Supabase/Firebase) với xác thực quản trị.

**Không có đăng nhập Admin:** Tab Admin có thể truy cập bởi bất cứ ai, nhưng mỗi người chỉ thay đổi được dữ liệu cục bộ trong trình duyệt của mình, không sửa được kho câu hỏi gốc trên GitHub. Không coi đây là hệ thống quản trị có bảo mật.

## Thêm câu vào file gốc (áp dụng cho tất cả người dùng mới)
- Mở `questions.js`.
- `rawMCQ`: `[topic,question,[A,B,C,D],correctIndex,explanation,optionalPassage]`, `correctIndex`: A=0, B=1, C=2, D=3.
- `rwRaw`: `[originalSentence,modelAnswer,hint]`.
- Commit `questions.js` lên GitHub. Người dùng **chưa từng sửa câu trong Admin** sẽ thấy dữ liệu cập nhật khi tải lại (nếu đã sửa Admin, họ đang dùng bản localStorage và có thể bấm Khôi phục bộ mẫu để nhận dữ liệu trong file mới).

## Lưu ý chấm điểm
Câu viết lại được chấm so với *một* đáp án mẫu sau chuẩn hóa dấu câu/khoảng trắng; những cách diễn đạt đúng khác có thể chưa được ghi nhận. Đây là công cụ luyện tập chứ không phải hệ thống chấm chuẩn chứng chỉ B2.
