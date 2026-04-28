# Artifact Policy

## RFC
Dùng để chốt hướng.

### RFC phải trả lời
- vấn đề gì đang tồn tại
- tại sao cần thay đổi
- các phương án đã cân nhắc
- trade-off của từng phương án
- rủi ro, rollback, migration
- quyết định chọn phương án nào và vì sao

### Không nên
- nhảy vào chi tiết code quá sớm
- viết RFC như spec triển khai

## Spec
Dùng để khóa yêu cầu.

### Spec phải có
- feature summary
- user stories / actor
- functional requirements
- non-functional requirements
- flows chính / flows lỗi
- edge cases
- acceptance criteria
- test cases cấp sản phẩm

## Implementation Plan
Dùng để khóa thứ tự làm.

### Plan phải có
- phạm vi
- dependency
- file/module dự kiến sửa
- thứ tự triển khai
- risk trong lúc làm
- validation steps

## Review
Mỗi review nên có:
- scope review
- findings
- mức độ nghiêm trọng
- missing cases
- đề xuất sửa
- verdict cuối
