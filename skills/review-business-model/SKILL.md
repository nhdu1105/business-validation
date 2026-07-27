---
name: review-business-model
description: >-
  Thiết kế và đánh giá mô hình kinh doanh cho một ý tưởng MMO (kiếm tiền online) đã được lựa chọn từ assess-idea - lựa chọn cơ chế doanh thu, Business Model Canvas, chiến lược giá/hoa hồng, và phác thảo unit economics. Dùng skill này bất cứ khi nào người dùng hỏi về mô hình kinh doanh, cách kiếm tiền, doanh thu, giá cả, "làm sao để kiếm tiền từ cái này", so sánh ads vs affiliate vs bán sản phẩm vs subscription, unit economics, CAC/LTV, hoặc muốn review/stress-test xem sản phẩm/kênh có khả thi về mặt thương mại không. Kích hoạt cả với những câu hỏi thường ngày như "nên tính phí kiểu gì", "ngách này nên kiếm tiền qua ads hay affiliate", hoặc "mô hình này có ổn không".
---

# Review Business Model — Kiến trúc thương mại cho ý tưởng MMO

Đề xuất một mô hình kinh doanh phù hợp với *ý tưởng cụ thể đã chọn* và thực tế của ngách/thị trường MMO đó — không phải một playbook SaaS chung chung. Sự thật cấu trúc quan trọng nhất cần xác định ngay từ đầu: **ai thực sự là người trả tiền để tạo ra doanh thu, và người đó có phải là người dùng/khán giả cuối hay không**. Trong nhiều mảng MMO, người mang lại doanh thu không phải là người dùng cuối (nhà quảng cáo trả theo lượt hiển thị/click, mạng affiliate trả hoa hồng theo đơn hàng, App Store/nền tảng ăn phần trăm giao dịch) — mô hình phải phù hợp với việc *ai thực sự trả tiền*, và giá/hoa hồng phải neo theo chuẩn thực tế của ngách đó, không phải theo trực giác hay theo chuẩn SaaS phương Tây.

## Đầu vào

Đọc `project-context.md` — đặc biệt là ý tưởng đã pursue (I#), các phát hiện nghiên cứu (F#), và ràng buộc của người dùng (ngân sách, thời gian, kỹ năng). Nếu chưa có ý tưởng nào được chọn, nói rõ rằng mô hình chỉ có thể phác thảo theo từng ý tưởng ứng viên, và hoặc làm vậy hoặc gợi ý hoàn thành assess-idea trước. Search dữ liệu hiện tại khi mô hình phụ thuộc vào nó (mức hoa hồng chuẩn của mạng affiliate, giá CPM/CPC hiện tại của ngách, chính sách chia doanh thu của nền tảng, chính sách phí thanh toán) thay vì khẳng định từ trí nhớ — các con số này thay đổi nhanh và lỗi thời rất dễ đánh lừa unit economics.

## Bước 1 — Sinh 2-3 mô hình ứng viên

Rút mô hình ứng viên từ các cơ chế doanh thu MMO thực sự đang vận hành, khớp với vòng lặp cốt lõi và các actor của ý tưởng:

- **Ads/CPM-CPC** (quảng cáo hiển thị trong content, app, game; doanh thu đến từ nhà quảng cáo/mạng quảng cáo, không phải người xem — cần khối lượng traffic đủ lớn mới có ý nghĩa)
- **Affiliate/hoa hồng (CPA/CPS)** (giới thiệu sản phẩm/dịch vụ của bên khác, nhận hoa hồng theo click/lead/đơn hàng; rủi ro nằm ở việc phụ thuộc điều khoản và tỷ lệ trả hoa hồng của mạng affiliate, có thể đổi bất cứ lúc nào)
- **Bán sản phẩm/dropshipping trực tiếp** (khách hàng là người trả tiền trực tiếp; biên lợi nhuận phụ thuộc giá vốn + phí vận chuyển + phí nền tảng bán hàng)
- **Freemium → IAP/Premium** (lớp miễn phí để thu hút; nói rõ điều gì khiến người dùng chuyển đổi trả phí — với game/app thường là tiện ích/tiến độ, không phải sự thuận tiện đơn thuần)
- **Subscription/Membership** (Patreon-style, cộng đồng trả phí định kỳ, hoặc SaaS/tool nhỏ thu phí tháng)
- **Bán sản phẩm số/khoá học/dịch vụ tư vấn** (info product, template, khoá học dựa trên chuyên môn đã xây dựng được qua content/audience)
- **Sponsorship/hợp tác thương hiệu** (thu nhập từ brand deal dựa trên lượng khán giả/độ tin cậy đã xây dựng — đòi hỏi quy mô audience tối thiểu mới đủ hấp dẫn nhãn hàng)
- **Marketplace/take-rate** (kết nối hai bên và ăn phần trăm giao dịch — vấn đề khó nhất luôn là cold-start phía cung)
- **Hybrid** (ví dụ: content miễn phí để kéo traffic → gắn affiliate link → upsell sản phẩm/khoá học riêng; đây là pattern rất phổ biến và thường bền hơn một nguồn doanh thu đơn lẻ vì không phụ thuộc hoàn toàn vào một nền tảng/đối tác)

Với mỗi ứng viên, viết một đoạn: tiền chảy như thế nào, ai thực sự là người trả tiền/tạo ra doanh thu, và điều khó nhất để mô hình này vận hành được (thường là: đạt đủ khối lượng traffic, giữ được tài khoản không bị khoá/demonetize, hoặc đàm phán được hoa hồng đủ tốt).

## Bước 2 — So sánh và đề xuất

So sánh các ứng viên theo: mức độ khớp với vòng lặp cốt lõi của ý tưởng đã chọn, bằng chứng về khả năng/sẵn sàng trả tiền của bên tạo doanh thu (F#), khả thi về phân phối/traffic với năng lực hiện tại của người dùng, cấu trúc rủi ro theo thời gian (thuật toán đổi, ngách bão hoà, mùa vụ, chính sách nền tảng siết lại — mô hình nào sống sót qua các cú sốc này), và rủi ro chính sách/pháp lý (điều khoản mạng affiliate, chính sách quảng cáo, quy định thuế thu nhập online, các ngách nhạy cảm như tài chính/sức khoẻ/crypto cần verify quy định hiện tại). Đề xuất một mô hình chính (có thể kèm hướng tiến hoá ở giai đoạn 2, ví dụ bắt đầu bằng affiliate rồi tiến tới bán sản phẩm riêng khi đã có audience) và nói thẳng vì sao các mô hình khác bị loại.

## Bước 3 — Business Model Canvas cho mô hình được đề xuất

Điền đầy đủ Business Model Canvas (phân khúc khách hàng, giá trị đề xuất theo từng phân khúc — nếu người trả tiền khác người dùng cuối thì viết riêng hai giá trị đề xuất; kênh phân phối; quan hệ khách hàng; dòng doanh thu; nguồn lực chính; hoạt động chính; đối tác chính; cơ cấu chi phí). Các khối cần làm rõ đặc thù MMO:

- **Kênh phân phối**: nêu rõ kênh nào là "canh bạc chính" để thu hút người dùng/traffic — organic (SEO, TikTok/YouTube tự nhiên, cộng đồng) hay trả phí (Facebook/Google/TikTok Ads) — và mức độ phụ thuộc vào thuật toán/chính sách của MỘT nền tảng duy nhất (rủi ro tập trung).
- **Thanh toán/nhận tiền**: phương thức phù hợp với đối tượng mục tiêu (MoMo/ZaloPay/chuyển khoản nếu là khách Việt Nam; Stripe/PayPal/thẻ quốc tế nếu là mảng toàn cầu như affiliate quốc tế hay bán trên Steam/App Store); với affiliate/ads, ghi rõ chu kỳ và ngưỡng thanh toán tối thiểu của mạng lưới (net-30/net-60, ngưỡng rút tiền) vì nó ảnh hưởng trực tiếp dòng tiền.
- **Cơ cấu chi phí**: gắn cờ các chi phí lặp lại dễ bị bỏ sót — chi phí traffic trả phí liên tục, phí công cụ/phần mềm, phí nền tảng/hoa hồng bị nền tảng ăn (App Store 30%, sàn TMĐT phí sàn...), chi phí sản xuất content liên tục nếu ý tưởng cần.

## Bước 4 — Phác thảo unit economics

Xây một phác thảo đơn giản, trung thực, từ dưới lên với các giả định được nêu rõ (khoảng số, không phải con số giả vờ chính xác):
giá/hoa hồng mỗi đơn vị (neo theo chuẩn thực tế của ngách) → biên lợi nhuận → CAC theo từng kênh (ước tính kèm lý do) → thời gian giữ chân/vòng đời kỳ vọng dựa trên rủi ro cấu trúc (bão hoà, thuật toán đổi, mùa vụ) → LTV → LTV:CAC. Nếu phác thảo chỉ hoạt động được với các giả định "anh hùng" (ví dụ: cần tỷ lệ viral/organic reach cao bất thường, hoặc cần commission rate cao hơn mức chuẩn ngách đang trả), nói thẳng điều đó — một mô hình cần 10% tỷ lệ chuyển đổi và không có rủi ro bị nền tảng khoá tài khoản trong một ngách vốn dĩ hay bị siết chính sách là một ảo tưởng, và giá trị của skill này là nói ra điều đó trước khi người dùng đổ công sức vào xây dựng.

## Cấu trúc output

```markdown
# Review mô hình kinh doanh — [tên ý tưởng]
## 1. Các mô hình ứng viên đã xem xét (kèm vấn đề khó nhất của mỗi mô hình)
## 2. Đề xuất & lý do
## 3. Business Model Canvas (mô hình được đề xuất)
## 4. Logic giá/hoa hồng & các mốc neo
## 5. Phác thảo unit economics (giả định được gắn nhãn rõ)
## 6. Top 3 rủi ro thương mại & cách kiểm chứng/giảm rủi ro với chi phí thấp nhất
```

Kết thúc bằng đề nghị cập nhật `project-context.md` (mục 5) và nhật ký quyết định, và nêu rõ mô hình đã chọn sẽ ràng buộc backlog/lộ trình như thế nào (ví dụ: mô hình affiliate cần tracking link/attribution; mô hình freemium cần hệ thống thanh toán + entitlement; mô hình content+sponsorship thuộc Track B của create-backlog trong khi mô hình app/game freemium thuộc Track A) — đây chính xác là thứ mà skill create-backlog sẽ đọc tiếp theo.
