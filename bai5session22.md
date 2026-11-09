# XÂY DỰNG QUY TRÌNH TROUBLESHOOTING NỘI BỘ VÀ BIỂU MẪU BUG REPORT — STARTUP TEAM


## PHẦN 1: QUY TRÌNH 3 BƯỚC TRA CỨU BẮT BUỘC (ĐỂ TỰ XỬ LÝ 80% VẤN ĐỀ)

Để triệt tiêu tình trạng nhắn tin loạn xạ, trôi thông tin trên nhóm chat mỗi khi gặp lỗi môi trường (như xung đột cổng Docker port conflict, lỗi biến môi trường `.env`, hoặc thiếu dependency), mọi thành viên trong nhóm bắt buộc phải tuân thủ **Quy trình 3 bước tự xử lý** trước khi được quyền nêu câu hỏi:

```text
[ GẶP LỖI MÔI TRƯỜNG ] ➔ BƯỚC 1: Googling đúng cách ➔ BƯỚC 2: Community Search ➔ BƯỚC 3: AI Decoding ➔ [ CẦN HỖ TRỢ: Gửi Bug Report ]

```

### Bước 1: Googling đúng cách (Khoanh vùng lỗi)

* **Thao tác:** Tuyệt đối không gõ câu hỏi cảm tính ("máy em bị lỗi docker rồi"). Hãy bóc tách thông báo lỗi nguyên văn (Raw Error Log) hiển thị trên Terminal.
* **Sử dụng toán tử:**
* Dùng ngoặc kép `""` để khớp chính xác cụm lỗi (ví dụ: `"bind: address already in use"`).
* Giới hạn phạm vi tìm kiếm kỹ thuật bằng `site:stackoverflow.com` hoặc `site:[github.com/docker/compose](https://github.com/docker/compose)`.



### Bước 2: Community Search (Khám phá cộng đồng mở)

* **Thao tác:** Nếu Google không ra kết quả trực tiếp, truy cập thẳng vào **GitHub Issues** của kho lưu trữ dự án hoặc **StackOverflow**.
* **Tiêu chí lọc:** Tìm các luồng (threads) đang mở (`OPEN`) hoặc đã đóng (`CLOSED`) có chứa từ khóa lỗi tương tự. Ưu tiên đọc các bình luận có lượng **Thumbs Up (`👍`) cao nhất** hoặc có gắn nhãn giải pháp (Accepted Answer) để áp dụng bản vá tạm thời (Workaround).

### Bước 3: AI Translation & Decoding (Giải mã thông qua Trợ lý AI)

* **Thao tác:** Nếu thông báo lỗi quá khó hiểu hoặc tài liệu hướng dẫn bằng tiếng Anh chuyên ngành phức tạp, hãy đưa chuỗi lỗi vào khung chat của Trợ lý AI (ChatGPT / Gemini).
* **Quy tắc an toàn vàng:**
* Phải sử dụng công thức **Prompt 3 thành phần** (Ngữ cảnh + Lỗi nguyên văn + Yêu cầu).
* **Tuyệt đối không** copy-paste các chuỗi Secret, mật khẩu cơ sở dữ liệu hay token bảo mật có trong file `.env` lên AI.
* Thẩm định kỹ câu trả lời của AI theo nguyên tắc an toàn trước khi chạy bất kỳ lệnh Terminal nào nó đề xuất.



---

## PHẦN 2: MẪU BUG REPORT TEMPLATE CHUẨN 4 MẢNH GHÉP

Nếu sau khi hoàn tất 3 bước trên mà vẫn không thể tự giải quyết (trong vòng 10–15 phút), thành viên mới được phép gửi yêu cầu hỗ trợ vào kênh kỹ thuật chung của nhóm. Yêu cầu bắt buộc phải sử dụng **Mẫu Bug Report Template** dưới đây (nếu thiếu bất kỳ mảnh ghép nào, yêu cầu sẽ bị từ chối xử lý):

```markdown
###  [BUG REPORT TỪ THÀNH VIÊN]
--------------------------------------------------
**1. Context (Ngữ cảnh môi trường):**
- Hệ điều hành đang dùng: [Ví dụ: Windows 11 / Ubuntu 22.04 / macOS Sonoma]
- Môi trường thực thi: [Ví dụ: VS Code Terminal / Docker Desktop v27.x / Node.js v20.x]
- Tác vụ đang làm: [Ví dụ: Chạy lệnh `docker compose up` để khởi động dịch vụ Backend]

**2. Expected (Hành vi mong muốn):**
- Hệ thống hiển thị gì khi chạy đúng? [Ví dụ: Container khởi động thành công, lắng nghe tại cổng port 5000]

**3. Actual (Kết quả thực tế / Hiện tượng lỗi):**
- Hệ thống trả về lỗi gì? [Ví dụ: Dịch vụ bị dừng đột ngột và báo lỗi xung đột cổng]

**4. Log & Screenshot (Nhật ký lỗi & Hình ảnh minh họa):**
- Nguyên văn dòng Error Log từ Terminal:
\`\`\`text
[Dán nguyên văn 3-5 dòng lỗi từ Terminal vào đây - Đã che thông tin nhạy cảm]
\`\`\`
- Các bước Troubleshooting đã thử ở Bước 1, 2, 3: [Ví dụ: Đã kiểm tra cổng 5000 bằng lệnh netstat nhưng không thấy tiến trình nào chiếm dụng, đã đổi sang cổng 5001 nhưng vẫn lỗi...]
--------------------------------------------------

```

---

## PHẦN 3: NGUYÊN TẮC VẬN HÀNH NHÓM CHAT KỸ THUẬT

1. **Nói KHÔNG với tin nhắn cụt ngủn:** Cấm gửi ảnh chụp màn hình điện thoại chụp màn hình máy tính mà không kèm văn bản, cấm nhắn các câu như *"Ai cứu với", "Code anh bị lỗi rồi"* mà không có Log.
2. **Xây dựng Kho tri thức chung (Knowledge Base):** Mỗi khi một lỗi được giải quyết thành công qua Bug Report, nhóm trưởng hoặc kỹ thuật viên xử lý có trách nhiệm tóm tắt nguyên nhân và cách khắc phục vào trang Wiki nội bộ của nhóm, giúp các thành viên khác không bị vấp lại lỗi cũ.