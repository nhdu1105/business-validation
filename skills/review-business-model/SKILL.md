---
name: project-context
description: >-
  Khởi tạo, đọc, hoặc cập nhật file project-context.md, đóng vai trò nguồn thông tin duy nhất (single source of truth) cho một dự án kiếm tiền online (MMO) của người dùng - game indie, affiliate, dropshipping, content, freelance, khoá học, crypto... Dùng skill này bất cứ khi nào người dùng bắt đầu một phiên làm việc mới về dự án MMO của họ, upload hoặc nhắc tới project-context.md, hỏi "đang ở đâu rồi", muốn tóm tắt tình trạng dự án, hoặc bất cứ khi nào một skill khác trong pipeline MMO (market-research, inspire-idea, assess-idea, review-business-model, create-backlog) tạo ra output cần được lưu vào bộ nhớ dự án. Cũng dùng khi người dùng đưa ra một quyết định (chọn một ý tưởng, xác nhận một mô hình kinh doanh, huỷ một hướng đi) mà các phiên sau cần nhớ lại.
---

# Project Context — Bộ nhớ của pipeline MMO

Skill này duy trì `project-context.md`, nguồn thông tin duy nhất cho dự án kiếm tiền online của người dùng. Các phiên làm việc của Claude không có bộ nhớ giữa các hội thoại, nên file này là cách toàn bộ pipeline (nghiên cứu thị trường → sinh ý tưởng → đánh giá → mô hình kinh doanh → backlog/lộ trình) mang quyết định từ phiên này sang phiên khác. Mọi skill khác trong pipeline đọc file này làm đầu vào và ghi thêm vào nó như đầu ra.

## Vì sao điều này quan trọng

Không có file ngữ cảnh chung, mỗi skill sẽ tự suy diễn lại giả định từ đầu, mâu thuẫn với quyết định trước đó, và bắt người dùng phải giải thích lại dự án của họ mỗi phiên. Có file này, skill đánh giá ý tưởng biết những phát hiện nghiên cứu nào đã tồn tại, skill lộ trình/backlog biết mô hình kinh doanh nào đã được chọn, và không có gì âm thầm bị mất. Coi file này là "chủ yếu chỉ thêm vào" (append-mostly): quyết định được cập nhật, nhưng lịch sử và lý do được giữ lại để người dùng luôn thấy được *vì sao* một điều gì đó đã được quyết định.

## Cấu trúc file chuẩn

Khi khởi tạo một dự án mới, tạo `project-context.md` đúng khung sau (điền những gì đã biết, đánh dấu phần còn lại là `TBD`):

```markdown
# Dự án MMO — Ngữ cảnh dự án
Cập nhật lần cuối: [ngày] · Giai đoạn: [khám phá | kiểm chứng | xây dựng | vận hành]

## 1. Tổng quan dự án
- Mảng MMO: [game indie / affiliate / dropshipping / content / freelance / khoá học / crypto / khác]
- Thị trường mục tiêu: [Việt Nam / khu vực / toàn cầu]
- Hướng đi một dòng: [TBD cho đến khi một ý tưởng được chọn]
- Ràng buộc của người dùng: [ngân sách, số giờ/tuần có thể dành ra, solo hay có team, kỹ năng sẵn có, kỹ thuật hay không kỹ thuật — hỏi nếu chưa biết]

## 2. Các phát hiện nghiên cứu chính (từ market-research)
[Các phát hiện đánh số F1, F2, ... — mỗi phát hiện một dòng + hạng bằng chứng A/B/C + nguồn]

## 3. Danh sách ý tưởng rút gọn (từ inspire-idea + assess-idea)
| ID | Ý tưởng | Trạng thái (pursue/park/killed) | Vì sao |

## 4. Nhật ký quyết định
[Các mục có ngày: quyết định gì, ai quyết, dựa trên bằng chứng nào]

## 5. Mô hình kinh doanh (từ review-business-model)
[Tóm tắt mô hình đã chọn — người trả tiền, cơ chế doanh thu, mức giá/hoa hồng neo theo thị trường — hoặc TBD]

## 6. Trạng thái backlog/lộ trình (từ create-backlog)
- Dạng ý tưởng: [phần mềm/game (Track A) hay sáng tạo/vận hành thủ công (Track B)]
[Link/tóm tắt các hạng mục backlog đã xác nhận, hoặc tên file SPEC.md / ROADMAP.md đã tạo, hoặc TBD]

## 7. Câu hỏi bỏ ngỏ & giả định rủi ro nhất
[Điều gì còn cần kiểm chứng trước khi xây dựng/mở rộng quy mô]

## 8. Cảnh báo & bài học rút ra
[Các claim thu nhập/case-study đã bị bác bỏ vì không kiểm chứng được, các thay đổi chính sách nền tảng cần theo dõi, các rủi ro đã biết]
```

## Quy trình làm việc

1. **Đầu phiên**: Nếu người dùng đã upload `project-context.md`, đọc toàn bộ trước khi làm bất cứ điều gì khác và tóm tắt 3-4 câu "đây là tình trạng hiện tại". Nếu họ nhắc tới dự án nhưng chưa có file, đề nghị khởi tạo một file — chỉ cần hỏi về ràng buộc của người dùng (khoảng ngân sách, số giờ/tuần, solo hay có team, kỹ năng kỹ thuật hay không), vì mọi phần còn lại sẽ được điền dần khi pipeline chạy.
2. **Sau khi một skill trong pipeline tạo ra output**: Chắt lọc output vào đúng mục liên quan. Các phát hiện trở thành mục `F#` đánh số để các skill sau có thể trích dẫn ("Ý tưởng I3 giải quyết F2 và F7"). Không dán nguyên báo cáo đầy đủ vào — file ngữ cảnh phải giữ dưới khoảng 2 trang, nếu không nó sẽ mất tác dụng. Báo cáo đầy đủ nằm ở các file output riêng (báo cáo nghiên cứu, SPEC.md, ROADMAP.md...).
3. **Khi người dùng ra quyết định**: Ghi lại vào Nhật ký quyết định kèm ngày và lý do một dòng. Ý tưởng bị killed vẫn ở lại trong bảng, đánh dấu killed — mọi nỗ lực "hồi sinh" sau này phải phản biện lại được lý do killed ban đầu, không được lặng lẽ bỏ qua.
4. **Luôn xuất toàn bộ file đã cập nhật** (không phải bản diff) dưới dạng `project-context.md` có thể tải xuống, để người dùng lưu vào Claude Project hoặc upload lại ở phiên sau.

## Quy tắc

- Không bao giờ bịa ra phát hiện, quyết định, hoặc ràng buộc không có trong hội thoại hoặc file hiện có. Nếu một mục chưa rõ, giữ nguyên `TBD` — một "sự thật" sai trong bộ nhớ dự án sẽ đầu độc mọi skill ở phía sau.
- Hạng bằng chứng luôn đi kèm phát hiện: A = số liệu chính thức/nền tảng hoặc nghiên cứu có kiểm chứng, B = báo cáo ngành/case-study đã xác minh được, C = báo chí, blog cá nhân, hoặc claim thu nhập chưa kiểm chứng. Các skill phía sau (đặc biệt assess-idea) cân nhắc theo hạng này — không để một claim C-grade âm thầm biến thành "sự thật" chỉ vì nó nằm trong file ngữ cảnh lâu ngày.
- Nếu file được upload mâu thuẫn với điều người dùng vừa nói, nêu rõ mâu thuẫn và hỏi cái nào là hiện tại thay vì âm thầm ghi đè.
- Vì các mảng MMO thay đổi nhanh (thuật toán, chính sách nền tảng, độ bão hoà ngách), khi cập nhật lại một dự án cũ đã lâu không đụng tới, chủ động hỏi xem có phát hiện/số liệu nào trong mục 2 và 8 đã lỗi thời cần research lại không, thay vì mặc định mọi thứ vẫn còn đúng.
