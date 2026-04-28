# OpenClaw Spec Review Skills

[![OpenClaw](https://img.shields.io/badge/OpenClaw-AgentSkills-5B5BD6)](https://github.com/on247ai/openclaw-spec-review-skills)
[![Workflow](https://img.shields.io/badge/Workflow-RFC%20%E2%86%92%20Spec%20%E2%86%92%20Plan%20%E2%86%92%20Review%20%E2%86%92%20Test-7C3AED)](https://github.com/on247ai/openclaw-spec-review-skills)
[![Status](https://img.shields.io/badge/Status-Internal%20Ready-16A34A)](https://github.com/on247ai/openclaw-spec-review-skills)

Bộ skill OpenClaw cho quy trình delivery nghiêm ngặt:
- RFC-first
- spec-first
- review-rigorous
- test-driven

Mục tiêu là biến OpenClaw từ nơi “code luôn” thành hệ delivery có cổng kiểm soát, có artifact chain rõ ràng, có review loop, và có quality gate trước khi ship.

## Repo này dành cho ai
- team kỹ thuật muốn chuẩn hóa delivery workflow
- workspace OpenClaw nội bộ muốn ép feature đi theo spec/review/test
- agent owner muốn tái sử dụng pipeline này cho nhiều project

## Skills trong repo
- `spec-review-delivery` — skill tổng mô tả toàn pipeline
- `rfc-author` — viết RFC trước implementation
- `spec-author` — viết spec và acceptance criteria
- `implementation-planner` — viết implementation plan theo file/module/thứ tự làm
- `artifact-reviewer` — review RFC/spec/plan/code/test
- `delivery-gatekeeper` — chốt GO / NO-GO / GO-WITH-RISKS
- `feature-delivery-orchestrator` — skill điều phối end-to-end pipeline

## Cài đặt cho OpenClaw
### Cách 1: copy thẳng vào workspace
```bash
cp -R skills/* /path/to/your/openclaw-workspace/skills/
```

Sau đó đảm bảo workspace có các folder chuẩn:

```text
docs/rfcs/
docs/specs/
docs/plans/
reviews/
tests/acceptance/
```

### Cách 2: clone repo vào workspace
```bash
git clone https://github.com/on247ai/openclaw-spec-review-skills.git /path/to/your/openclaw-workspace/openclaw-spec-review-skills
cp -R /path/to/your/openclaw-workspace/openclaw-spec-review-skills/skills/* /path/to/your/openclaw-workspace/skills/
```

## Quick start
### Flow chuẩn
1. Dùng `feature-delivery-orchestrator` để classify feature.
2. Nếu cần RFC, dùng `rfc-author`.
3. Dùng `artifact-reviewer` để review artifact.
4. Dùng `spec-author` để viết spec.
5. Dùng `implementation-planner` để viết plan.
6. Review code/test.
7. Dùng `delivery-gatekeeper` để chốt GO / NO-GO.

## Ví dụ dùng thật
### Ví dụ 1 — feature nhỏ
**Request:** thêm filter đơn giản cho màn danh sách.

**Flow:**
`Mini spec -> Review -> Implement -> Test`

### Ví dụ 2 — feature chuẩn
**Request:** thêm Android 13+ notification permission flow.

**Flow:**
`Spec -> Review -> Plan -> Review -> Implement -> Test`

Artifacts ví dụ:
- `docs/specs/SPEC-001-android13-notification-permission.md`
- `docs/plans/PLAN-001-android13-notification-permission.md`
- `reviews/SPEC-001/review-1-technical.md`
- `reviews/SPEC-001/review-2-product.md`

### Ví dụ 3 — feature phức tạp
**Request:** đổi kiến trúc sync/offline-first có migration dữ liệu.

**Flow:**
`RFC -> RFC review -> Spec -> Spec review -> Plan -> Implement -> Gate -> Test -> Ship`

## Folder artifact khuyến nghị
```text
docs/
  rfcs/
  specs/
  plans/
reviews/
tests/
  acceptance/
```

## Nguyên tắc vận hành
- Không implement feature mới nếu chưa có spec được approve.
- Feature phức tạp phải có RFC trước spec.
- Artifact quan trọng nên review 2-3 vòng.
- Mọi test nên trace được về acceptance criteria.
- Chỉ ship khi gate report cho phép.

## OpenClaw-specific notes
- Khi artifact quan trọng, dùng `sessions_spawn` để tạo reviewer độc lập.
- Có thể kết hợp `taskflow` nếu muốn track flow dài nhiều bước.
- Nên lưu artifact thành file trước, review file sau, rồi mới sửa file.

## Tài liệu đi kèm
- `docs/INSTALL_OPENCLAW.md` — hướng dẫn cài vào workspace OpenClaw
- `docs/GITHUB_PUBLISHING.md` — hướng dẫn publish repo lên GitHub

## Repository
- GitHub: `https://github.com/on247ai/openclaw-spec-review-skills`
