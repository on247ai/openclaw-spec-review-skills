# OpenClaw Spec Review Skills

Bộ skill OpenClaw cho quy trình delivery nghiêm ngặt:
- RFC-first
- spec-first
- review-rigorous
- test-driven

Bộ này giúp biến OpenClaw thành hệ delivery có cổng kiểm soát thay vì code luôn.

## Skills trong repo
- `spec-review-delivery` — skill tổng mô tả pipeline delivery
- `rfc-author` — viết RFC
- `spec-author` — viết spec
- `implementation-planner` — viết implementation plan
- `artifact-reviewer` — review RFC/spec/plan/code/test
- `delivery-gatekeeper` — chốt GO / NO-GO / GO-WITH-RISKS
- `feature-delivery-orchestrator` — skill điều phối toàn bộ pipeline

## Cài đặt cho OpenClaw
### Cách 1: copy thẳng vào workspace
Copy thư mục `skills/` của repo này vào workspace OpenClaw của bạn:

```bash
cp -R skills/* /path/to/your/openclaw-workspace/skills/
```

Sau đó đảm bảo workspace có các folder chuẩn để chứa artifact delivery:

```text
docs/rfcs/
docs/specs/
docs/plans/
reviews/
tests/acceptance/
```

### Cách 2: clone repo vào workspace
```bash
git clone <repo-url> /path/to/your/openclaw-workspace/openclaw-spec-review-skills
cp -R /path/to/your/openclaw-workspace/openclaw-spec-review-skills/skills/* /path/to/your/openclaw-workspace/skills/
```

## Cách dùng trong OpenClaw
### Flow chuẩn
1. Dùng `feature-delivery-orchestrator` để classify feature.
2. Nếu cần RFC, dùng `rfc-author`.
3. Dùng `artifact-reviewer` để review nhiều vòng.
4. Dùng `spec-author` để viết spec.
5. Dùng `implementation-planner` để viết plan.
6. Review code/test.
7. Dùng `delivery-gatekeeper` để chốt GO / NO-GO.

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

## OpenClaw-specific notes
- Khi artifact quan trọng, dùng `sessions_spawn` để tạo reviewer độc lập.
- Có thể kết hợp `taskflow` nếu muốn track flow dài nhiều bước.
- Chỉ implement sau khi spec được approve.
- Chỉ ship sau khi gate report cho phép.
