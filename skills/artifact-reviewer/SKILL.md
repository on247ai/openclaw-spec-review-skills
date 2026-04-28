---
name: artifact-reviewer
description: Use when a user wants a rigorous review of an RFC, spec, implementation plan, source code, or test plan. Triggers for review rounds, blocker/major/minor findings, independent reviewer passes, subagent review loops, or requests to critique an artifact before approval.
---

# Artifact Reviewer

Dùng skill này khi cần review artifact nghiêm ngặt trước khi approve.

## Phạm vi
- RFC
- Spec
- Plan
- Source code
- Test plan / verification checklist

## Cách review
1. Xác định artifact type.
2. Review theo correctness, completeness, risk.
3. Ghi finding theo severity: blocker / major / minor.
4. Chỉ rõ missing edge cases hoặc conflict.
5. Kết thúc bằng verdict: approve / revise.

## Template
Đọc `assets/REVIEW_TEMPLATE.md`.

## Review loop
Đọc `references/review-severity.md` và `references/multi-round-review.md`.

## Output
- `reviews/<artifact-id>/review-N.md`
