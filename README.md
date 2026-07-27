# Bộ Skill Thẩm Định & Phát Triển Ý Tưởng Kinh doanh tại Việt Nam cho Claude Code

Một **plugin marketplace** cho Claude Code, đóng gói 6 skill hoạt động như một *pipeline* liền mạch để phát triển và thẩm định ý tưởng kinh doanh tại thị trường Việt Nam — từ nghiên cứu thị trường đến backlog sẵn sàng cho Claude Code lập trình.

Toàn bộ skill nghiên cứu và thẩm định đều được thiết kế để dựa trên **bằng chứng thực nghiệm** (có xếp hạng độ tin cậy nguồn) và **lý thuyết đã được kiểm chứng** (Jobs-to-be-Done, Desirability–Feasibility–Viability, RICE, Business Model Canvas).

Repo: https://github.com/nhdu1105/business-validation

---

## Pipeline 6 skill

Các skill nối tiếp nhau, cùng đọc và ghi vào một file bộ nhớ chung `project-context.md`. Nhờ đó, phát hiện nghiên cứu được đánh số (F1, F2…), ý tưởng được đánh số (I1, I2…), và mỗi bước sau phải trích dẫn ID của bước trước — chuỗi truy vết này là thứ giữ cho toàn bộ quy trình mang tính thực nghiệm.

| # | Skill | Vai trò | Đầu vào → Đầu ra |
|---|-------|---------|------------------|
| 0 | **project-context** | Bộ nhớ dự án (single source of truth). Vì Claude không nhớ giữa các phiên, file này giúp pipeline mang quyết định đi tiếp. | Hội thoại → `project-context.md` |
| 1 | **industry-research** | Cố vấn ngành: báo cáo thị trường, xu hướng, khoảng trống, nhu cầu, rào cản, đối thủ — trọng tâm K-12 Việt Nam. Luôn tìm kiếm web, xếp hạng nguồn A/B/C. | Yêu cầu → Báo cáo + findings F# |
| 2 | **inspire-idea** | Sinh ý tưởng/use case bám vào phát hiện nghiên cứu. Mỗi ý tưởng phải gắn với ít nhất một F#. | Findings → Idea cards I# |
| 3 | **assess-idea** | Bộ lọc trung thực: chấm Desirability–Feasibility–Viability + RICE, phân loại theo đuổi / tạm gác / loại bỏ. | Ideas → Bảng điểm + verdict |
| 4 | **review-business-model** | Đề xuất & kiểm nghiệm mô hình kinh doanh: chọn revenue model, Business Model Canvas, pricing, unit economics. | Ý tưởng đã chọn → Mô hình + BMC |
| 5 | **create-backlog** | Biến quyết định thành backlog. **Hai pha:** (1) danh sách backlog để bạn xác nhận → (2) file `SPEC.md` cho Claude Code lập trình. | Mô hình → Backlog → SPEC.md |

Luồng chuẩn: `project-context` (nền) → `industry-research` → `inspire-idea` → `assess-idea` → `review-business-model` → `create-backlog`.

---

## Đặc điểm thiết kế

- **Xếp hạng độ tin cậy nguồn**: A (nghiên cứu peer-review), B (báo cáo ngành uy tín), C (báo chí / tuyên bố một công ty). Không xây kết luận quan trọng chỉ trên nguồn C.
- **Ưu tiên bằng chứng Việt Nam** rồi mới đến Đông Nam Á → Á → toàn cầu, kèm lập luận khả năng chuyển giao (transferability) khi dùng bằng chứng nước ngoài.
- **Bám thực tế thị trường Việt**: Hành vi người dùng, mức độ sẵn lòng trả tiền, liệu có cách khác để người dùng đat được mục đích không. Skill nghiên cứu được hướng dẫn tìm kiếm cả bằng tiếng Việt.
- **`assess-idea` được viết để LOẠI ý tưởng** — tối đa giữ 2–3 ý tưởng, có bộ chặn thiên kiến (halo effect, sunk-cost, lạc quan quá mức).
- **`create-backlog` có cổng hai pha**: chỉ tạo `SPEC.md` sau khi bạn xác nhận phạm vi backlog.

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

**3. Kiểm tra:** hỏi Claude Code *"nghiên cứu thị trường với ngành ... tại Việt Nam giúp tôi"* — skill `industry-research` sẽ được kích hoạt.

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
│           ├── industry-research/SKILL.md
│           ├── inspire-idea/SKILL.md
│           ├── assess-idea/SKILL.md
│           ├── review-business-model/SKILL.md
│           └── create-backlog/SKILL.md
└── README.md
```

---

## Cách dùng hiệu quả

- **Giữ `project-context.md`**: sau mỗi phiên, lưu file này lại (hoặc gắn vào Claude Project) và tải lên ở phiên sau để pipeline không mất trí nhớ. File này được `.gitignore` bỏ qua vì là bộ nhớ riêng của từng dự án, không nên commit chung.
- **Đi theo thứ tự** nhưng linh hoạt: có thể quay lại `industry-research` khi `assess-idea` lộ ra khoảng trống dữ liệu.
- **Desk research có trần**: các skill sẽ nhắc bạn kiểm chứng sơ cấp (phỏng vấn phụ huynh/giáo viên) trước khi code — đó là tính năng, không phải thiếu sót.

---

## Ngôn ngữ

Ngôn ngữ làm việc mặc định của dự án này là **tiếng Việt**.

## Giấy phép

MIT — xem file `LICENSE`.
