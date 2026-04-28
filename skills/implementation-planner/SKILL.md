---
name: implementation-planner
description: Use when a user wants an implementation plan after an approved spec or RFC. Triggers for file-level change plans, rollout order, dependency sequencing, validation steps, risk-controlled execution, or any request to plan implementation before coding.
---

# Implementation Planner

Dùng skill này khi đã có spec đủ rõ và cần plan trước khi code.

## Mục tiêu
Biến spec thành thứ tự triển khai an toàn, reviewable.

## Cách làm
1. Xác định scope của plan.
2. Liệt kê dependency và assumption.
3. Chỉ ra file/module dự kiến sửa.
4. Sắp thứ tự implement từ nền tảng đến UI/integration.
5. Nêu risk trong lúc làm.
6. Chốt validation steps sau khi code.

## Template
Đọc `assets/PLAN_TEMPLATE.md`.

## Review
Đọc `references/plan-review.md` nếu cần review plan trước khi code.

## Output
- `docs/plans/PLAN-xxx-name.md`
