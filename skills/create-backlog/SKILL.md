---
name: create-backlog
description: >-
  Biến một ý tưởng MMO đã được pursue (từ assess-idea) và mô hình kinh doanh đã chọn thành lộ trình triển khai thực tế. Nếu ý tưởng thuộc dạng phần mềm/game/app/tool tự động hoá, xuất backlog ưu tiên rồi tài liệu đặc tả kỹ thuật (SPEC.md) sẵn sàng để Claude Code lập trình không cần đoán. Nếu ý tưởng thuộc dạng sáng tạo/vận hành thủ công (content creation, affiliate marketing, dropshipping, freelancing, xây kênh, xây cộng đồng...), xuất file lộ trình chi tiết (ROADMAP.md) với timeline, mốc (milestone), đầu vào/đầu ra cần đạt, và tiêu chí chấm kết quả ở mỗi mốc. Dùng skill này khi người dùng muốn tạo backlog, user story, epic, phạm vi MVP, kế hoạch phát triển, PRD, spec, lộ trình thực hiện, kế hoạch hành động, hoặc hỏi "nên làm gì trước", hoặc muốn tài liệu để Claude Code có thể trực tiếp lập trình. Đây là skill hai pha bắt buộc - pha 1 luôn xuất bản kế hoạch/backlog để người dùng xác nhận, pha 2 (chỉ sau khi xác nhận rõ ràng) mới xuất tài liệu triển khai đầy đủ.
---

# Create Backlog / Roadmap — Từ quyết định đến kế hoạch có thể thực thi

Chuyển hoá mọi thứ ở thượng nguồn (ý tưởng được pursue, mô hình kinh doanh, ràng buộc nguồn lực, giả định rủi ro nhất) thành (1) một kế hoạch ưu tiên mà người dùng xác nhận, rồi (2) một tài liệu triển khai mà người thực thi — có thể là Claude Code, có thể là chính người dùng — làm theo mà không cần đoán. Cổng xác nhận hai pha là bắt buộc vì tài liệu đầy đủ tốn công tạo ra và tốn công làm lại — không bao giờ tạo pha 2 trước khi người dùng xác nhận rõ phạm vi ở pha 1.

## Đầu vào

Đọc `project-context.md` — ý tưởng đã pursue (I#), mô hình kinh doanh, ràng buộc của người dùng (vốn, thời gian rảnh/tuần, kỹ năng, solo hay có team), và giả định rủi ro nhất cần kiểm chứng. Nếu chưa có ý tưởng nào được pursue hoặc chưa chọn mô hình kinh doanh, nói rõ bước nào ở thượng nguồn còn thiếu; vẫn có thể làm nếu người dùng khăng khăng muốn (đánh dấu kế hoạch là "pre-validation").

## Bước 0 — Phân loại dạng ý tưởng (bắt buộc, làm trước mọi thứ khác)

Xác định vòng lặp cốt lõi của ý tưởng thuộc nhóm nào:

- **Nhóm A — Phần mềm/Game/Tool**: cốt lõi đòi hỏi viết code để vận hành (game indie, app di động, web app/SaaS nhỏ, extension trình duyệt, bot/automation script, công cụ tự động hoá cho affiliate...). → đi theo **Track A** (Backlog + SPEC.md cho Claude Code).
- **Nhóm B — Sáng tạo/Vận hành thủ công**: cốt lõi là con người thực hiện lặp lại (sản xuất content, chạy chiến dịch affiliate, xây kênh TikTok/YouTube, dropshipping vận hành bằng nền tảng có sẵn (Shopify/TikTok Shop), freelancing, xây cộng đồng, bán khoá học...) — không có deliverable là phần mềm tự viết. → đi theo **Track B** (Lộ trình chi tiết — ROADMAP.md).
- **Ý tưởng lai** (ví dụ: kênh content có kèm một tool nhỏ tự chế để hỗ trợ): tách thành hai phần, chạy Track B cho phần vận hành/sáng tạo và Track A (thu gọn) cho phần tool — nói rõ với người dùng bạn đang tách như vậy.

Nếu không rõ ý tưởng thuộc nhóm nào từ mô tả trong `project-context.md`, hỏi ngắn gọn một câu trước khi tiếp tục.

---

## TRACK A — Ý tưởng phần mềm/game

### Phase 1 — Backlog

Tổ chức theo **Epic → User story**, mỗi story phải có lý do tồn tại truy vết được về vòng lặp cốt lõi, yêu cầu mô hình kinh doanh, hoặc một phép kiểm chứng giả định rủi ro nhất:

```markdown
## Epic E1: [tên] — vì sao tồn tại (truy vết I#/mô hình/giả định)
| ID | User story | Tiêu chí chấp nhận (kiểm tra được) | Ưu tiên | Effort | Phụ thuộc |
| S1 | Là một [vai trò], tôi muốn [hành động], để [kết quả] | Given/When/Then, 2-4 tiêu chí | M/S/C/W | S/M/L | — |
```

- **Ưu tiên theo MoSCoW** (Must/Should/Could/Won't-now) và vẽ rõ **ranh giới MVP**: các Must phải tạo thành một vòng lặp hoàn chỉnh cho MỘT vai trò hoàn thành MỘT job từ đầu đến cuối. Một MVP phục vụ nửa vời ba vai trò thì không phục vụ ai cả.
- Bao gồm các epic không hào nhoáng mà mô hình kinh doanh bắt buộc phải có: tài khoản/đăng nhập, thanh toán/entitlement khớp với mô hình doanh thu đã chọn (cổng thanh toán phù hợp thị trường mục tiêu — ví dụ MoMo/ZaloPay/thẻ quốc tế tuỳ đối tượng), tracking/attribution cho link affiliate hoặc quảng cáo nếu có, và một "xương sống" sự kiện phân tích (analytics) — nếu không có, các giả định rủi ro nhất sẽ không bao giờ đo được.
- Chống lại sự phình phạm vi: nếu danh sách Must vượt quá khoảng 12-15 story, thách thức lại — cái gì có thể đẩy xuống dưới ranh giới MVP mà vòng lặp cốt lõi vẫn còn nguyên?

### Đầu ra pha 1 và cổng xác nhận

Trình bày backlog, nêu rõ ranh giới MVP và lý do, liệt kê các quyết định sản phẩm còn bỏ ngỏ mà spec sẽ cần trả lời (ví dụ: "web hay mobile-first? Có cần app riêng hay chạy trên nền tảng có sẵn?"), rồi **dừng lại và yêu cầu người dùng xác nhận phạm vi** (xác nhận toàn bộ Must / chỉnh sửa / khoanh vùng lại). Không tự ý tiếp tục nếu người dùng im lặng hoặc trả lời mơ hồ.

### Phase 2 — Đặc tả cho Claude Code (chỉ sau khi xác nhận)

Đối tượng đọc là Claude Code, thực thi mà không có bạn ở đó để hỏi. Mọi thứ mơ hồ sẽ trở thành một phỏng đoán; mọi thứ không được nói ra sẽ trở thành một thiếu sót. Viết `SPEC.md` như một file có thể tải xuống, đúng cấu trúc sau:

```markdown
# [Tên sản phẩm] — Đặc tả triển khai
## 1. Tổng quan sản phẩm & vòng lặp cốt lõi (3-4 câu + MỘT hành trình người dùng mà MVP bắt buộc phải làm tốt)
## 2. Tech stack (đề xuất, kèm lý do 1 dòng mỗi mục — tôn trọng năng lực người dùng; ổn định hơn hào nhoáng)
## 3. Mô hình dữ liệu (entity, field kèm kiểu dữ liệu, quan hệ)
## 4. Tính năng, theo từng story đã xác nhận:
   ### S# — [tên story]
   - Mô tả hành vi (văn xuôi rõ ràng, không mơ hồ)
   - Tiêu chí chấp nhận (Given/When/Then — lấy và làm sắc nét lại từ backlog)
   - Ghi chú UI (màn hình, các trạng thái chính: rỗng/loading/lỗi)
   - API surface nếu có (endpoint, method, hình dạng request/response)
## 5. Yêu cầu phi chức năng (locale/ngôn ngữ, mobile-first nếu cần, thiết bị mục tiêu, ngưỡng hiệu năng, xử lý dữ liệu người dùng nếu ứng dụng thu thập dữ liệu cá nhân)
## 6. Ngoài phạm vi (nêu rõ — mọi thứ dưới ranh giới MVP, để Claude Code không "nhiệt tình" xây thêm)
## 7. Thứ tự xây dựng (theo trình tự tôn trọng phụ thuộc; mỗi bước kết thúc bằng thứ chạy được)
## 8. Dữ liệu mẫu/seed (ví dụ thực tế phù hợp ngách và thị trường mục tiêu của ý tưởng)
```

Quy tắc viết spec:
- Đề xuất một stack cụ thể, phổ biến, phù hợp năng lực người dùng (ví dụ: một framework full-stack được hỗ trợ tốt + DB quản lý sẵn + auth quản lý sẵn) trừ khi người dùng đã nêu ưu tiên riêng — hỏi về ưu tiên đó trước pha 2 nếu chưa biết.
- Mọi tiêu chí chấp nhận phải kiểm tra được bằng cách chạy thử app. "Onboarding thân thiện" không phải là tiêu chí; "một tài khoản mới chạm được tính năng cốt lõi trong ≤3 màn hình" mới là tiêu chí.
- Khi một quyết định sản phẩm bị bỏ ngỏ ở pha 1 mà người dùng không quyết định, chọn phương án đơn giản nhất và ghi lại trong mục `## Quyết định đưa ra trong spec này` ở đầu tài liệu để không có gì bị ngầm giả định.
- Giữ đúng độ tin cậy của cơ chế kiếm tiền/giữ chân người dùng: nếu vòng lặp cốt lõi là, ví dụ, một hệ thống thưởng/retention loop, đặc tả rõ luật vận hành thật (dù đơn giản) — không để cơ chế quan trọng này là "TBD".

Kết thúc bằng đề nghị cập nhật `project-context.md` với trạng thái backlog và tên file spec.

---

## TRACK B — Ý tưởng sáng tạo/vận hành thủ công

Với các ý tưởng dạng content/affiliate/dropshipping/freelance..., "sản phẩm" không phải là phần mềm mà là một chuỗi hành động lặp lại của con người. Đầu ra ở đây không phải SPEC.md mà là một **lộ trình thực thi** đủ chi tiết để người dùng (hoặc người họ thuê) biết chính xác làm gì mỗi giai đoạn, và biết khi nào nên tiếp tục hay dừng lại.

### Trước khi lên lộ trình

Nếu chưa biết, hỏi ngắn gọn: người dùng có thể dành bao nhiêu giờ/tuần cho việc này (part-time vài giờ/tối, hay full-time), và ngân sách khởi động tối đa (gần như 0đ, vài triệu, hay có thể đầu tư đáng kể). Lộ trình phải khớp với con số thật, không phải con số lý tưởng.

### Phase 1 — Khung mốc (milestone) để xác nhận

Trình bày trước một bảng mốc rút gọn để người dùng xác nhận phạm vi/nhịp độ trước khi viết lộ trình đầy đủ:

```markdown
| Giai đoạn | Thời gian | Mục tiêu chính | Điều kiện go/no-go để qua giai đoạn tiếp |
| G1: ... | Tuần 1-2 | ... | ... |
```

Ranh giới quan trọng nhất cần vẽ rõ: **giai đoạn kiểm chứng giả định rủi ro nhất** (từ assess-idea) phải nằm sớm nhất có thể, rẻ nhất có thể — không lao vào sản xuất/mở rộng quy mô trước khi giả định đó được kiểm chứng. Sau khi trình bày khung mốc, **dừng lại và hỏi người dùng xác nhận** nhịp độ/thời lượng trước khi viết lộ trình chi tiết đầy đủ.

### Phase 2 — Lộ trình chi tiết (chỉ sau khi xác nhận)

Viết `ROADMAP.md` như một file có thể tải xuống, đúng cấu trúc sau:

```markdown
# [Tên dự án] — Lộ trình triển khai
## 1. Tổng quan & mục tiêu cuối cùng (bám theo I#, mô hình kinh doanh, giả định rủi ro nhất cần kiểm chứng trước)
## 2. Giả định rủi ro nhất & phép kiểm chứng rẻ nhất (nhắc lại từ assess-idea — đây là điều giai đoạn đầu tồn tại để trả lời)
## 3. Bảng mốc chi tiết
   | Giai đoạn | Thời gian | Đầu vào cần có | Đầu ra/deliverable cụ thể cần đạt | Tiêu chí chấm đạt/không đạt (số liệu cụ thể) | Việc cần làm (checklist hành động) |
## 4. Nhịp làm việc theo tuần trong giai đoạn hiện tại (ví dụ: thứ 2/4/6 đăng bài, thứ 3 phân tích số liệu tuần trước, thứ 5 tối ưu...) — khớp với số giờ/tuần đã xác nhận
## 5. Ngân sách & nguồn lực theo từng giai đoạn (tiền, công cụ, kỹ năng cần học thêm nếu có)
## 6. Bộ chỉ số theo dõi (số liệu cụ thể cần ghi lại mỗi tuần, và ngưỡng nào là tín hiệu tốt/xấu)
## 7. Điểm quyết định go/no-go/pivot ở cuối mỗi giai đoạn (nêu rõ: đạt tiêu chí → sang giai đoạn sau; không đạt nhưng gần → điều chỉnh gì rồi thử lại; không đạt và không có tín hiệu cải thiện → dừng, chuyển hướng)
## 8. Rủi ro đã biết & phương án dự phòng (chính sách nền tảng đổi, tài khoản bị khoá, chi phí traffic tăng...)
```

Quy tắc viết lộ trình:
- Mọi tiêu chí ở cột "chấm đạt/không đạt" phải là con số cụ thể đo được (ví dụ: "đạt tối thiểu 1.000 view trung bình/video trong 2 tuần", "tỷ lệ click-to-buy ≥ 2%", "ít nhất 3 đơn hàng thật từ người lạ, không tính bạn bè"), không phải mô tả cảm tính ("được nhiều người thích").
- Mỗi giai đoạn phải có input (nguồn lực/kỹ năng/tài sản cần có sẵn TRƯỚC khi bắt đầu giai đoạn đó) tách biệt rõ với output (thứ phải tồn tại ở CUỐI giai đoạn để coi là hoàn thành).
- Nhịp độ tuần phải khớp với số giờ/tuần người dùng đã xác nhận ở bước hỏi trước — một lộ trình đòi hỏi 4 giờ/ngày cho người chỉ có 1 giờ/tối là một lộ trình vô dụng dù nhìn đẹp trên giấy.
- Giai đoạn đầu luôn là giai đoạn kiểm chứng rẻ nhất giả định rủi ro nhất, không phải giai đoạn "xây dựng thương hiệu quy mô lớn" — mở rộng quy mô chỉ nên xuất hiện ở các giai đoạn sau, sau go/no-go đầu tiên.

Kết thúc bằng đề nghị cập nhật `project-context.md` với trạng thái lộ trình và tên file ROADMAP.md.
