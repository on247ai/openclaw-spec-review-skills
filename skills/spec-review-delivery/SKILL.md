---
name: spec-review-delivery
description: Use when a user wants RFC-first, spec-first, review-rigorous, or test-driven delivery in OpenClaw. Triggers for requests to create or review RFCs, specs, implementation plans, test plans, multi-round artifact reviews, subagent review loops, quality gates, or a disciplined feature-delivery workflow before coding.
---

# Spec Review Delivery

Dùng skill này khi công việc phải đi theo quy trình chặt:
- feature mới phải bắt đầu bằng spec
- feature phức tạp bắt đầu bằng RFC trước spec
- mỗi artifact phải review nhiều vòng
- implementation phải trace được về spec
- test phải trace được về acceptance criteria

## Mục tiêu
Biến OpenClaw từ nơi “code luôn” thành hệ delivery có kiểm soát:
1. Chốt hướng bằng RFC khi cần.
2. Khóa yêu cầu bằng spec.
3. Khóa thứ tự làm bằng implementation plan.
4. Khóa chất lượng bằng review nhiều vòng.
5. Khóa hành vi bằng test + verification.

## Khi nào dùng RFC
Tạo RFC trước spec nếu có ít nhất 1 điều sau:
- thay đổi kiến trúc đáng kể
- có từ 2 phương án trở lên cần so trade-off
- ảnh hưởng nhiều team/module/workflow
- có rủi ro migration, rollback, data integrity, security, cost
- yêu cầu chưa rõ hoặc cần debate giữa các agent

Nếu không có các dấu hiệu trên, có thể đi thẳng vào spec.

## Trình tự chuẩn
### Flow nhẹ
Request -> Mini spec -> Review -> Implement -> Test

### Flow chuẩn
Request -> Spec -> Review -> Plan -> Review -> Implement -> Code review -> Test

### Flow nghiêm ngặt
Request -> RFC -> RFC review 2-3 vòng -> Approved RFC -> Spec -> Spec review 2-3 vòng -> Plan -> Plan review -> Implement -> Code review 2-3 vòng -> Test review -> Verify -> Ship

## Quy tắc bắt buộc
- Không implement feature mới nếu chưa có spec được chấp nhận.
- Không viết code từ RFC chưa chốt.
- Mọi artifact phải có verdict rõ: approve / revise.
- Mọi implementation phải trỏ được về spec section liên quan.
- Mọi test phải trỏ được về acceptance criteria.
- Khi review, ưu tiên tìm thiếu sót, edge case, conflict, rollback gap.

## Cách dùng subagent review
Khi artifact quan trọng, spawn 2-3 subagent review độc lập.
Phân vai reviewer như sau:
- Reviewer A: correctness / architecture
- Reviewer B: product / UX / requirement coverage
- Reviewer C: edge cases / testability / rollout risk

Sau đó:
1. Tổng hợp feedback.
2. Sửa artifact.
3. Nếu thay đổi đáng kể, chạy thêm 1 vòng review nữa.

## Output nên tạo trong workspace
- RFC: `docs/rfcs/RFC-xxx-name.md`
- Spec: `docs/specs/SPEC-xxx-name.md`
- Plan: `docs/plans/PLAN-xxx-name.md`
- Reviews: `reviews/<artifact-id>/review-1.md`, `review-2.md`, `review-3.md`
- Tests: `tests/acceptance/...` hoặc file test tương ứng trong project

## Template cần đọc khi làm việc
- RFC template: `assets/RFC_TEMPLATE.md`
- Spec template: `assets/SPEC_TEMPLATE.md`
- Plan template: `assets/PLAN_TEMPLATE.md`
- Review template: `assets/REVIEW_TEMPLATE.md`
- Traceability matrix: `assets/TRACEABILITY_MATRIX_TEMPLATE.md`

## Khi cần đọc references
- Đọc `references/artifact-policy.md` khi cần biết tiêu chuẩn từng artifact.
- Đọc `references/review-loop.md` khi cần tổ chức vòng review nhiều lớp.
- Đọc `references/test-strategy.md` khi cần map spec -> test.
- Đọc `references/openclaw-application.md` khi cần áp quy trình này vào OpenClaw/subagents/taskflow.

## Cách triển khai trong OpenClaw
- Dùng `sessions_spawn` cho review độc lập khi artifact quan trọng.
- Dùng `sessions_send` hoặc tổng hợp file review khi cần phản biện vòng 2.
- Với workflow dài, có thể kết hợp TaskFlow để track các bước: RFC -> Spec -> Plan -> Implement -> Test.
- Lưu artifact thành file trước, review file sau, rồi mới sửa file.

## Checklist hoàn tất
- [ ] Đã xác định có cần RFC hay không
- [ ] Đã có spec rõ ràng
- [ ] Đã có ít nhất 1 vòng review artifact chính
- [ ] Feature phức tạp đã có 2-3 vòng review như yêu cầu
- [ ] Đã có implementation plan trước khi code lớn
- [ ] Đã có test/verification map về acceptance criteria
- [ ] Đã có kết luận approve trước khi ship
