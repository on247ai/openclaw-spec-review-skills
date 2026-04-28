---
name: delivery-gatekeeper
description: Use when a user wants to enforce approval gates before implementation or release. Triggers for quality gates, traceability checks, spec-to-code validation, test readiness, ship/no-ship decisions, or any request to decide whether work is ready to proceed or release.
---

# Delivery Gatekeeper

Dùng skill này để quyết định có được qua cổng tiếp theo hay không.

## Gate chính
- RFC approved chưa
- Spec approved chưa
- Plan approved chưa
- Code đã khớp spec chưa
- Test đã map đủ acceptance criteria chưa
- Verification đã pass chưa

## Cách làm
1. Thu thập artifact liên quan.
2. Kiểm tra traceability giữa spec -> implementation -> test.
3. Liệt kê gap còn lại.
4. Kết luận: GO / NO-GO / GO-WITH-RISKS.

## Templates
- `assets/GATE_REPORT_TEMPLATE.md`
- `assets/TRACEABILITY_MATRIX_TEMPLATE.md`

## References
Đọc `references/gate-policy.md` và `references/definition-of-done.md`.

## Output
- `reviews/<artifact-id>/gate-report.md`
- `reviews/<artifact-id>/traceability-matrix.md`
