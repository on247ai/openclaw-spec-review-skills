# Hướng dẫn cài đặt bộ skill này cho OpenClaw

## 1. Mục tiêu
Cài bộ skill delivery nghiêm ngặt vào workspace OpenClaw để mọi feature có thể đi theo RFC/spec/review/test pipeline.

## 2. Yêu cầu
- Đã có một workspace OpenClaw hoạt động
- Có quyền ghi vào thư mục `skills/` của workspace đó

## 3. Copy skill vào workspace
Ví dụ workspace là `/root/.openclaw/workspace`:

```bash
mkdir -p /root/.openclaw/workspace/skills
cp -R skills/* /root/.openclaw/workspace/skills/
```

## 4. Tạo folder chuẩn cho artifact
```bash
mkdir -p /root/.openclaw/workspace/docs/rfcs
mkdir -p /root/.openclaw/workspace/docs/specs
mkdir -p /root/.openclaw/workspace/docs/plans
mkdir -p /root/.openclaw/workspace/reviews
mkdir -p /root/.openclaw/workspace/tests/acceptance
```

## 5. Workflow khuyến nghị
- classify bằng `feature-delivery-orchestrator`
- viết RFC nếu cần bằng `rfc-author`
- review bằng `artifact-reviewer`
- viết spec bằng `spec-author`
- viết plan bằng `implementation-planner`
- chốt gate bằng `delivery-gatekeeper`

## 6. Khi nào dùng từng skill
### `feature-delivery-orchestrator`
Khi user muốn điều phối trọn pipeline.

### `rfc-author`
Khi feature phức tạp, nhiều phương án, có risk lớn.

### `spec-author`
Khi cần chốt yêu cầu trước khi code.

### `implementation-planner`
Khi đã có spec đủ rõ và cần plan file/module/thứ tự làm.

### `artifact-reviewer`
Khi cần review nghiêm ngặt cho artifact.

### `delivery-gatekeeper`
Khi cần GO / NO-GO trước implementation hoặc release.

## 7. Gợi ý áp vào AGENTS.md
Có thể thêm rule như sau vào AGENTS.md của workspace:
- Không implement feature mới nếu chưa có spec được approve.
- Feature phức tạp phải có RFC trước spec.
- Artifact quan trọng phải review 2-3 vòng.
- Test/verification phải map về acceptance criteria.

## 8. Kiểm tra sau cài đặt
- Kiểm tra thư mục `skills/` đã có đủ 7 skill.
- Kiểm tra OpenClaw có thể đọc đúng `SKILL.md` trong từng thư mục.
- Chạy thử 1 feature nhỏ theo flow spec -> review -> plan -> implement.
