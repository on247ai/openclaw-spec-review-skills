---
name: feature-delivery-orchestrator
description: Use when a user wants an end-to-end RFC/spec/plan/review/test workflow orchestrated in OpenClaw. Triggers for requests to run strict feature delivery, decide whether RFC is required, coordinate multi-round reviews, spawn reviewer subagents, enforce quality gates, or manage a disciplined implementation pipeline from request to ship.
---

# Feature Delivery Orchestrator

Dùng skill này khi user muốn điều phối toàn bộ pipeline delivery theo chuẩn nghiêm ngặt.

## Mục tiêu
Quyết định và điều phối:
1. Có cần RFC hay không.
2. Khi nào phải sang spec.
3. Khi nào phải sang implementation plan.
4. Cần bao nhiêu vòng review.
5. Có đủ điều kiện GO để implement/ship chưa.

## Quy trình điều phối
### Bước 1: Phân loại mức độ thay đổi
Xếp task vào 1 trong 3 mức:
- Nhẹ: mini spec -> review -> implement -> test
- Chuẩn: spec -> review -> plan -> review -> implement -> test
- Nghiêm ngặt: RFC -> review nhiều vòng -> spec -> review nhiều vòng -> plan -> review -> implement -> code review -> gate -> test -> ship

### Bước 2: Quyết định có cần RFC không
Đọc `references/rfc-decision-tree.md`.
Nếu task đụng architecture, migration, nhiều phương án, security, data, hoặc workflow lớn -> cần RFC.

### Bước 3: Sinh artifact đúng thứ tự
- RFC: dùng skill `rfc-author`
- Spec: dùng skill `spec-author`
- Plan: dùng skill `implementation-planner`
- Review: dùng skill `artifact-reviewer`
- Gate: dùng skill `delivery-gatekeeper`

## Cách điều phối review
### Với artifact nhẹ
- 1 reviewer là đủ

### Với artifact quan trọng
- spawn 2-3 reviewer độc lập bằng `sessions_spawn`
- reviewer A: architecture/correctness
- reviewer B: product/coverage
- reviewer C: edge cases/testability/risk

### Sau review
- tổng hợp finding
- sửa artifact
- nếu còn blocker hoặc sửa lớn, chạy thêm 1 vòng review nữa

## Cổng chuyển bước
Không được sang bước tiếp theo nếu:
- artifact hiện tại chưa có verdict approve hoặc equivalent
- còn blocker mở
- testability quá mơ hồ
- traceability bị đứt

## File outputs chuẩn
- RFC: `docs/rfcs/RFC-xxx-name.md`
- Spec: `docs/specs/SPEC-xxx-name.md`
- Plan: `docs/plans/PLAN-xxx-name.md`
- Reviews: `reviews/<artifact-id>/review-N.md`
- Gate report: `reviews/<artifact-id>/gate-report.md`
- Traceability: `reviews/<artifact-id>/traceability-matrix.md`

## References nên đọc khi cần
- `references/rfc-decision-tree.md`
- `references/review-matrix.md`
- `references/gate-sequence.md`
- `references/subagent-review-playbook.md`

## Assets nên dùng
- `assets/DELIVERY_CHECKLIST.md`
- `assets/FEATURE_CLASSIFICATION_TEMPLATE.md`
- `assets/REVIEW_ASSIGNMENT_TEMPLATE.md`

## Kết quả mong muốn
Mỗi feature phải có:
- classification rõ
- artifact chain rõ
- số vòng review rõ
- gate status rõ
- test/verify plan rõ
