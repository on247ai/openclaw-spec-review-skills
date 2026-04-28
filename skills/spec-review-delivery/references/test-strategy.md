# Test Strategy

## Tư tưởng
Spec sinh ra acceptance criteria.
Acceptance criteria sinh ra test cases.
Implementation phải chứng minh pass các test đó.

## Thứ tự map
1. Đọc acceptance criteria.
2. Viết danh sách test case theo happy path / edge / failure path.
3. Xác định cái nào auto-test được, cái nào cần manual verify.
4. Sau khi code xong, verify coverage không bị lệch spec.

## Nhóm test nên có
- unit tests cho logic thuần
- widget/integration/api tests nếu phù hợp
- manual verification checklist cho UI, infra, migration, external integrations

## Definition of done tối thiểu
- acceptance criteria được map đầy đủ
- test chạy/pass hoặc có lý do rõ vì sao chưa tự động hóa
- có verify note cuối
