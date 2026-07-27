# Bộ Skill Nghiên Cứu, Đánh Giá & Lên Lộ Trình Kiếm Tiền Online (MMO) cho Claude Code

Một **plugin marketplace** cho Claude Code, đóng gói 6 skill hoạt động như một *pipeline* liền mạch để tìm, kiểm chứng và triển khai ý tưởng kiếm tiền online (MMO) — game indie, affiliate marketing, dropshipping, content creation, freelancing, bán khoá học, crypto... — từ nghiên cứu thị trường đến backlog/lộ trình sẵn sàng để thực thi (bằng Claude Code nếu là phần mềm/game, hoặc bằng chính bạn nếu là content/affiliate/vận hành thủ công).

Toàn bộ skill nghiên cứu và thẩm định đều được thiết kế để dựa trên **bằng chứng thực nghiệm** (có xếp hạng độ tin cậy nguồn) và **lý thuyết đã được kiểm chứng** (Jobs-to-be-Done, Desirability–Feasibility–Viability, RICE, Business Model Canvas).

Repo: https://github.com/nhdu1105/business-validation

---

## Pipeline 6 skill

Các skill nối tiếp nhau, cùng đọc và ghi vào một file bộ nhớ chung `project-context.md`. Nhờ đó, phát hiện nghiên cứu được đánh số (F1, F2…), ý tưởng được đánh số (I1, I2…), và mỗi bước sau phải trích dẫn ID của bước trước — chuỗi truy vết này là thứ giữ cho toàn bộ quy trình mang tính thực nghiệm, thay vì một mớ ý tưởng "nghe có vẻ hay" không kiểm chứng được.

| # | Skill | Vai trò | Đầu vào → Đầu ra |
|---|-------|---------|------------------|
| 0 | **project-context** | Bộ nhớ dự án (single source of truth). Vì Claude không nhớ giữa các phiên, file này giúp pipeline mang quyết định đi tiếp. | Hội thoại → `project-context.md` |
| 1 | **market-research** | Cố vấn thị trường MMO: báo cáo quy mô, xu hướng, khoảng trống, nhu cầu, rào cản, đối thủ cho một mảng MMO cụ thể (game indie, affiliate, dropshipping, content, freelance...). Luôn tìm kiếm web, xếp hạng nguồn A/B/C — đặc biệt cảnh giác các claim thu nhập "kiếm X triệu/tháng" chưa kiểm chứng. | Yêu cầu → Báo cáo + findings F# |
| 2 | **inspire-idea** | Sinh ý tưởng kiếm tiền bám vào phát hiện nghiên cứu. Mỗi ý tưởng phải gắn với ít nhất một F#, kèm cơ chế kiếm tiền/tăng trưởng, kênh traffic dự kiến, và ước tính vốn/thời gian khởi động. | Findings → Idea cards I# |
| 3 | **assess-idea** | Bộ lọc trung thực: chấm Desirability–Feasibility–Viability + RICE, phân loại theo đuổi / tạm gác / loại bỏ. Có bộ chặn thiên kiến riêng cho MMO ("thiên kiến guru" — cảnh giác số liệu từ người bán khoá học về chính ngách đó). | Ideas → Bảng điểm + verdict |
| 4 | **review-business-model** | Đề xuất & kiểm nghiệm mô hình kiếm tiền: ads, affiliate CPA/CPS, bán sản phẩm, freemium/IAP, subscription, sponsorship, marketplace, hoặc hybrid — Business Model Canvas, pricing/hoa hồng neo theo chuẩn ngách, unit economics. | Ý tưởng đã chọn → Mô hình + BMC |
| 5 | **create-backlog** | Biến quyết định thành kế hoạch thực thi. **Hai pha, rẽ theo dạng ý tưởng:** (1) khung backlog/lộ trình để bạn xác nhận → (2a) nếu là phần mềm/game: `SPEC.md` sẵn sàng cho Claude Code lập trình; (2b) nếu là content/affiliate/vận hành thủ công: `ROADMAP.md` với timeline, mốc, đầu vào/đầu ra, tiêu chí đạt/không đạt cụ thể. | Mô hình → Backlog/Lộ trình → SPEC.md hoặc ROADMAP.md |

Luồng chuẩn: `project-context` (nền) → `market-research` → `inspire-idea` → `assess-idea` → `review-business-model` → `create-backlog`.

---

## Đặc điểm thiết kế

- **Tổng quát cho mọi mảng MMO**: không cố định vào một ngách — bước đầu tiên của mỗi skill luôn xác định rõ người dùng đang khảo sát mảng nào (game indie, affiliate, dropshipping, content, freelance, khoá học, crypto, hay mảng khác) trước khi đào sâu.
- **Xếp hạng độ tin cậy nguồn**: A (số liệu chính thức/nền tảng, nghiên cứu có kiểm chứng), B (báo cáo ngành uy tín, case-study đã xác minh), C (báo chí, blog cá nhân, hoặc claim thu nhập một cá nhân/kênh chưa kiểm chứng). Không xây kết luận quan trọng chỉ trên nguồn C — mảng MMO ngập tràn claim thu nhập không kiểm chứng được nên nguyên tắc này đặc biệt quan trọng.
- **Ưu tiên địa lý theo tầng** khi liên quan: Việt Nam → Đông Nam Á → Á → toàn cầu, kèm lập luận khả năng chuyển giao (transferability); với các mảng vốn dĩ toàn cầu (affiliate quốc tế, game trên Steam/App Store), bằng chứng toàn cầu được dùng ngay từ đầu.
- **Bám thực tế vận hành**: rủi ro chính sách/thuật toán nền tảng (demonetize, shadow ban, đổi điều khoản affiliate), độ bão hoà ngách, chi phí traffic, và mức độ khớp giữa lộ trình với số giờ/tuần và ngân sách thật của người dùng — không phải con số lý tưởng.
- **`assess-idea` được viết để LOẠI ý tưởng** — tối đa giữ 2–3 ý tưởng, có bộ chặn thiên kiến (halo effect, sunk-cost, lạc quan quá mức, và thiên kiến "guru MMO").
- **`create-backlog` có cổng hai pha và rẽ nhánh theo dạng ý tưởng**: chỉ tạo tài liệu triển khai đầy đủ (`SPEC.md` hoặc `ROADMAP.md`) sau khi bạn xác nhận phạm vi backlog/lộ trình rút gọn.

---

## Cài đặt qua GitHub

**1. Trong Claude Code, thêm marketplace:**

```
/plugin marketplace add nhdu1105/business-validation
```

**2. Cài plugin:**

```
/plugin install business-validation@business-validation
```

Cú pháp là `<tên-plugin>@<tên-marketplace>`. Tên marketplace lấy từ trường `name` trong `marketplace.json` (ở đây là `business-validation`).

**3. Kiểm tra:** hỏi Claude Code *"nghiên cứu thị trường affiliate mỹ phẩm tại Việt Nam giúp tôi"* hoặc *"làm game hyper-casual còn tiềm năng không"* — skill `mmo-market-research` sẽ được kích hoạt.

### Cài thử tại máy (không cần push)

```
/plugin marketplace add /đường-dẫn/tới/business-validation
/plugin install business-validation@business-validation
```

---

## Cấu trúc repo

```
business-validation/
├── .claude-plugin/
│   └── marketplace.json          # Registry marketplace (bắt buộc ở gốc repo)
├── plugins/
│   └── business/validation/
│       ├── .claude-plugin/
│       │   └── plugin.json        # Manifest của plugin
│       └── skills/
│           ├── project-context/SKILL.md
│           ├── market-research/SKILL.md
│           ├── inspire-idea/SKILL.md
│           ├── assess-idea/SKILL.md
│           ├── review-business-model/SKILL.md
│           └── create-backlog/SKILL.md
└── README.md
```

---

## Cách dùng hiệu quả

- **Giữ `project-context.md`**: sau mỗi phiên, lưu file này lại (hoặc gắn vào Claude Project) và tải lên ở phiên sau để pipeline không mất trí nhớ. File này được `.gitignore` bỏ qua vì là bộ nhớ riêng của từng dự án, không nên commit chung.
- **Đi theo thứ tự** nhưng linh hoạt: có thể quay lại `market-research` khi `assess-idea` lộ ra khoảng trống dữ liệu, hoặc quay lại `inspire-idea` khi `review-business-model` cho thấy không mô hình nào khả thi với ý tưởng hiện tại.
- **Khai báo ràng buộc thật ngay từ đầu**: số giờ/tuần có thể dành ra và ngân sách khởi động — các skill dùng con số này để không đề xuất ý tưởng/lộ trình vượt quá khả năng thực tế của bạn.
- **Desk research có trần**: các skill sẽ nhắc bạn kiểm chứng sơ cấp (chạy thử quảng cáo nhỏ, đăng vài bài content thăm dò, landing page smoke test) trước khi đầu tư công sức xây dựng toàn bộ — đó là tính năng, không phải thiếu sót.
- **Cẩn trọng với claim thu nhập**: khi một phát hiện chỉ dựa trên C-grade (blog cá nhân, video "kiếm X triệu/tháng"), pipeline sẽ luôn gắn nhãn "chưa kiểm chứng" — đừng bỏ qua nhãn này khi ra quyết định.

---

## Ngôn ngữ

Ngôn ngữ làm việc mặc định của dự án này là **tiếng Việt**.

## Giấy phép

MIT — xem file `LICENSE`.
