---
name: rfc-author
description: Use when a user wants to draft, refine, or finalize an RFC before implementation. Triggers for architecture changes, multi-option design decisions, trade-off analysis, migration risk, rollback planning, or any request to write a request for change before a spec.
---

# RFC Author

Dùng skill này khi cần viết RFC trước khi đi vào spec/implementation.

## Mục tiêu
Tạo RFC đủ mạnh để chốt hướng thay đổi trước khi code.

## Khi nào phải dùng
- có nhiều phương án thiết kế
- thay đổi kiến trúc hoặc workflow lớn
- có migration / rollback / data risk
- cần debate giữa nhiều agent trước khi chốt

## Cách làm
1. Xác định vấn đề và phạm vi.
2. Liệt kê goals / non-goals.
3. Đề xuất ít nhất 2 phương án nếu còn tranh luận.
4. So trade-off rõ ràng.
5. Ghi rủi ro, rollback, migration.
6. Kết luận phương án đề xuất và trạng thái phê duyệt.

## Template
Đọc `assets/RFC_TEMPLATE.md`.

## Review
Khi RFC quan trọng, đọc thêm `references/rfc-review.md` và spawn 2-3 subagent review độc lập.

## Output
- `docs/rfcs/RFC-xxx-name.md`
