# Applying This Workflow in OpenClaw

## 1. Dùng OpenClaw như hệ delivery có cổng kiểm soát
- agent chính làm owner của feature
- subagent dùng để review độc lập
- artifact lưu bằng file trong workspace
- review cũng lưu thành file để có lịch sử

## 2. Mapping sang công cụ OpenClaw
- `sessions_spawn`: tạo reviewer độc lập
- `sessions_send`: giao tiếp với session reviewer có sẵn
- `taskflow`: theo dõi flow dài nhiều bước
- `memory`: lưu quyết định lâu dài sau khi đã chốt

## 3. Mô hình pipeline đề nghị
- Draft RFC (nếu cần)
- Spawn 2-3 reviewer cho RFC
- Chỉnh RFC -> approve
- Draft spec
- Spawn 2-3 reviewer cho spec
- Chỉnh spec -> approve
- Draft plan
- Review plan
- Implement
- Code review
- Test + verify

## 4. Rule thực thi
- reviewer không nên là cùng một prompt với author nếu cần phản biện mạnh
- luôn review artifact file, không review “mô tả bằng miệng”
- nếu implementation lệch spec, spec hoặc code phải được cập nhật và review lại
